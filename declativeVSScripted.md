# Jenkins Pipelines: Scripted vs Declarative

## Introduction

In Jenkins, pipelines are essential for automating the software delivery process. There are two primary types of pipelines: **Scripted Pipelines** and **Declarative Pipelines**. Each has its own syntax and use cases.

## Difference Between Scripted and Declarative Pipelines

| Feature                       | Scripted Pipeline                               | Declarative Pipeline                           |
|-------------------------------|------------------------------------------------|------------------------------------------------|
| **Syntax**                    | Uses a Groovy-based syntax.                    | while the syntax for Declarative Pipeline is also based on Groovy, but it uses a more structured and predefined format.      |
| **Complexity**                | Better suited for complex workflows.           | Ideal for straightforward, linear workflows.  |
| **Readability**               | Can become complex and harder to read.        | Generally more readable and maintainable.     |
| **Control Flow**              | Supports advanced Groovy constructs (loops, conditionals). | Limited control flow; focuses on stages.      |
| **Error Handling**            | Allows for try-catch blocks for custom error handling. | Basic error handling through the `post` section. |
| **Structure**                 | No enforced structure; the user has full control. | Enforced structure with defined stages and steps. |
| **Use Cases**                 | Suitable for dynamic and complex build processes. | Suitable for standard CI/CD processes.        |
| **Post Actions**              | Can manually define cleanup and notifications. | Easy to define in the `post` section.        |
| **Learning Curve**            | Steeper learning curve, requires Groovy knowledge. | Easier for beginners and less technical users. |

## Examples

### Scripted Pipeline Example

```groovy
node {
    stage('Build') {
        echo 'Building the application...'
    }
    stage('Test') {
        echo 'Running tests...'
    }
    stage('Deploy') {
        echo 'Deploying the application...'
    }
}

### declative Pipeline Example
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
            }
        }
    }
}
