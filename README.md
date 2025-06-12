# Test SHA

# pr-closed Trigger Example
To execute a job by a pr closed event in Screwdriver.cd, you can specify ~pr-closed requires property on the jobs.

Example:
```
shared:
  image: node:lts
jobs:
    main:
        requires: [~commit, ~pr]
        steps:
            - echo: echo 'this is test job.'
    jobA:
        requires: [~pr-closed]
        steps:
            - echo: |
                echo 'this job is executed when a pr is closed/merged.'
    jobB:
        requires: [~pr, ~pr-closed]
        steps:
            - echo: |
                echo 'this job is executed when a pr is created or it is closed/merged.'
    jobC:
        requires: [~pr-closed:stable]    
        steps:
            - echo: |
                echo 'this job is executed when a pr is closed/merged on branch stable.'
```
