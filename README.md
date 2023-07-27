# Adding GitHub Triggers

This folder holds the files for the lab: _Adding GitHub Triggers_ which is part of the **IBM-CD0215EN-Skills Network Introduction to CI/CD** course.

Start a pipeline run:

Terminal 1:
In one of the sessions, you need to run the kubectl port-forward command to forward the port for the event listener so that you can call it on localhost.

Use the kubectl port-forward command to forward port 8090 to 8080.

kubectl port-forward service/el-cd-listener  8090:8080


Terminal 2:
Use the curl command to send a payload to the event listener service.

curl -X POST http://localhost:8090 \
  -H 'Content-Type: application/json' \
  -d '{"ref":"main","repository":{"url":"https://github.com/ibm-developer-skills-network/wtecc-CICD_PracticeCode"}}'

+ This should start a PipelineRun. You can check on the status with this command:

tkn pipelinerun ls

+ You can also examine the PipelineRun logs using this command (the -L means “latest” so that you do not have to look up the name for the last run):

tkn pipelinerun logs --last

