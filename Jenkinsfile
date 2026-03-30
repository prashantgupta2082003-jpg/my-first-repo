pipeline{
    agent any
    stages{
        stage('1. Checkout'){
            steps{
                git url:'https://gitlab.siescoms.in/mca25024/repo.git' ,branch:'main'
            }
        }

        stage('2. Build Image'){
            steps{
                bat 'docker build -t myweb .'
            }
        }
        
        stage('3. Stop all Containers'){
            steps{
                bat 'docker stop mycont || exit 0'
                bat 'docker rm mycont || exit 0'
            }
        }
        
        stage('4. Run the Image- Containerize'){
            steps{
                bat 'docker run -d -p 8000:80 --name mycont myweb'
            }
        }
    }
}
