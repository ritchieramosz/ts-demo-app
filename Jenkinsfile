pipeline {
    agent { label 'agent' }
    stages {
        stage('Build') {
            steps {
                sh 'cd app && npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'cd app && npm test'
            }
        }
        stage('Docker Build') {
            steps {
                sh 'cd app && docker build -t  444106639146.dkr.ecr.us-east-1.amazonaws.com/app:jenkins-${BUILD_NUMBER} .'
            }
        }
        stage('Docker Push') {
            steps {
                sh '''
                    aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 444106639146.dkr.ecr.us-east-1.amazonaws.com
                    docker push  444106639146.dkr.ecr.us-east-1.amazonaws.com/app:jenkins-${BUILD_NUMBER} 
                  '''
            }
        }
    }
}  

/* Esta es una estructura para hacer un jenkinsfile con mensajes de error y pruebas con su dependencias.


pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    try {
                        echo 'Iniciando la fase de construcción...'
                        dir('app') {
                            sh 'npm install'
                        }
                        echo 'Construcción completada exitosamente.'
                    } catch (Exception e) {
                        echo "Error durante la fase de construcción: ${e.message}"
                        error 'Fallo en la fase de construcción.'
                    }
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    try {
                        echo 'Iniciando la fase de pruebas...'
                        dir('app') {
                            sh 'npm install --only=dev'  // Instalar dependencias de desarrollo
                            sh 'npm test'  // Ejecutar las pruebas
                        }
                        echo 'Pruebas completadas exitosamente.'
                    } catch (Exception e) {
                        echo "Error durante la fase de pruebas: ${e.message}"
                        error 'Fallo en la fase de pruebas.'
                    }
                }
            }
        }

        // Puedes agregar más etapas según sea necesario...

    }

    // Puedes agregar postacciones, notificaciones, etc.

}

Node.js tiene varias herramientas populares para realizar pruebas en aplicaciones JavaScript. Algunas de las más utilizadas son:

Mocha:

Descripción: Mocha es un marco de pruebas flexible y completo que permite ejecutar pruebas asíncronas y síncronas. Es muy configurable y puede utilizarse con varios bibliotecas de aserciones.
Instalación: npm install --save-dev mocha
Jest:

Descripción: Jest es un marco de pruebas desarrollado por Facebook que es fácil de configurar y ofrece una amplia gama de características, como pruebas de snapshot y cobertura integradas.
Instalación: npm install --save-dev jest
Jasmine:

Descripción: Jasmine es otro marco de pruebas popular para JavaScript que se centra en ser fácil de usar y leer. Proporciona una sintaxis de estilo BDD (Desarrollo Dirigido por Comportamiento).
Instalación: npm install --save-dev jasmine
Chai:

Descripción: Chai es una biblioteca de aserciones que se puede utilizar con Mocha o cualquier otro marco de pruebas. Proporciona una sintaxis expresiva para escribir aserciones claras y legibles.
Instalación: npm install --save-dev chai
Jasmine:

Descripción: Jasmine es un marco de pruebas de comportamiento para JavaScript que no requiere configuración. Es autónomo y se utiliza para realizar pruebas BDD.
Instalación: npm install --save-dev jasmine
Cypress:

Descripción: Cypress es una herramienta de prueba de extremo a extremo que permite realizar pruebas en el navegador. Puede utilizarse para pruebas de integración y pruebas de usuario.
Instalación: npm install --save-dev cypress

OJO

La diferencia entre --save-dev y --only=dev radica en cómo se utilizaban en las versiones antiguas de npm y cómo se utilizan en las versiones más recientes.

--save-dev:

Versiones antiguas (npm 4 y anteriores): Se usaba para agregar dependencias a la sección devDependencies de tu archivo package.json. Por ejemplo, npm install --save-dev mocha agregará mocha a devDependencies.
Versiones recientes (npm 5 y posteriores): Aunque aún funciona, npm 5 y versiones posteriores automáticamente instalan las dependencias de desarrollo cuando ejecutas npm install --save-dev. Entonces, la bandera --save-dev se ha vuelto redundante en estas versiones.
--only=dev:

Esta es una forma más moderna de especificar que solo quieres instalar las dependencias de desarrollo. Funciona independientemente de si estás utilizando npm 4 o versiones más recientes.

*/