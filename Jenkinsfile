pipeline{
    agent any
    stages{
        stage("Install dependencies"){
            steps{
                bat 'dotnet restore'
            }
            post{
                success{
                    echo "========Instalation executed successfully========"
                }
                failure{
                    echo "========Instalation execution failed========"
                }
            }
        }
        stage("Build"){
            steps{
                bat 'dotnet build --no-restore'
            }
            post{
                success{
                    echo "========Build executed successfully========"
                }
                failure{
                    echo "========Build execution failed========"
                }
            }
        }
         stage("Run Tests"){
            parallel{
                stage("Unit tests"){
                    steps{
                        bat 'dotnet test TestProject1/TestProject1.csproj --no-build --verbosity normal'
                    }
                    post{
                        success{
                            echo "========Unit tests executed successfully========"
                        }
                        failure{
                            echo "========Unit tests execution failed========"
                        }
                    }
                }
                stage("Integration tests"){
                    steps{
                        bat 'dotnet test TestProject2/TestProject2.csproj --no-build --verbosity normal'
                    }
                    post{
                        success{
                            echo "========Integration tests executed successfully========"
                        }
                        failure{
                            echo "========Integration tests execution failed========"
                        }
                    }
                }
                stage("UI tests"){
                    steps{
                        bat 'dotnet test TestProject3/TestProject3.csproj --no-build --verbosity normal'
                    }
                    post{
                        success{
                            echo "========UI tests executed successfully========"
                        }
                        failure{
                            echo "========UI tests execution failed========"
                        }
                    }
                }
            }
        }
    }
    post{
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}