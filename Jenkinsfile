pipeline {
    agent any

    tools {
        maven 'Maven 3.6.3' // אם יש לך Maven מותקן בג'נקינס, אם לא, תוכל להוריד אותו
        jdk 'JDK 11' // או גירסה אחרת של JDK לפי הצורך
    }

    stages {
        stage('Checkout') {
            steps {
                // משיכת הקוד מהרפוזיטורי
                git 'https://github.com/zolbergeli/maven-demo.git'
            }
        }

        stage('Build') {
            steps {
                // הרצת build בעזרת Maven
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                // הרצת בדיקות עם Maven
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                // יצירת ארכיב JAR (או WAR לפי הגדרות הפרויקט)
                sh 'mvn package'
            }
        }

        stage('Deploy') {
            steps {
                // כאן תוכל להוסיף שלב לפריסת האפליקציה (למשל על שרת)
                echo 'Deploying application...'
            }
        }
    }

    post {
        always {
            // תמיד אחרי סיום, שלב לנקות או לבצע פעולות אחרות
            cleanWs() // מנקה את העבודה של ג'נקינס
        }
    }
}
