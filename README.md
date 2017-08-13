# Building a custom jenkins image on OSE

1. Create the imagestream  

```
oc tag registry.access.redhat.com/openshift3/jenkins-2-rhel7  custom-jenkins:latest
```

2. Edit the plugins.txt to add the required plugins

```
gitlab-plugin:1.4.7
gitlab-logo:1.0.3
pipeline-model-definition:1.1.9
```

3. Create the build config 

```
oc create -f customjenkins-bc.yml
```

4. Start the build 

```
oc start-build custom-jenkins-build  --follow
```

4. Use the image in the templates 

```
custom-jenkins:latest
```
