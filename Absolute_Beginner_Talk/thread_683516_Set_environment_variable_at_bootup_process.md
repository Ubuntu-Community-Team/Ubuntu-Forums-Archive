---
title: "Set environment variable at bootup process"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by rene.guenther on 2008-01-31
I am trying to set an environment variable at bootup process.
I created a script startup_script:

```
#!  /bin/sh
echo  “Entering custom startup script… “
export ANT_HOME=”/usr/local/ant”
echo  “Leaving custom startup script… “
```

I made it executable: ```
chmod 755 startup_script
```.
I added it to bootup process:
```
update-rc.d -f startup_script start 90 2.
```
Runlevel is 2 what I checked with command ```
runlevel 
```(output is N 2)
When booting I can see the output of the echo “Entering…” and “Leaving…”
I login and type```
 echo $ANT_HOME
```. The output is empty. What am I missing?

Thanks and regards
René

---

### Post by breaking on 2008-01-31
Test

---

### Post by kpkeerthi on 2008-01-31
I'm not sure if your method is a recommended way of setting env variables.
I usually set env variables in 
1. ~/.bashrc - This file will be read everytime a non-interactive shell (think *terminal*) is opened.
or 
2. /etc/profile or in one of (~/.bash_profile or ~/.bash_login or ~/.profile) - These files will be read everytime some user logs in.

Usually setting an env variable in ~/.bashrc should suffice as this file is automatically read upon login.

---

### Post by rene.guenther on 2008-01-31
I am running a background job. This job needs the variable to be set. Will the variable available to the background job if I do like you recommended?

thanks
rene

---

### Post by kpkeerthi on 2008-01-31
How are you starting the background job? I assume you have my-background-job.sh file or something like that. You just have to add whatever env variables you need to my-background-job.sh.

---

### Post by rene.guenther on 2008-01-31
Actually I dont know :-) I installed some tool (cruise control) automating my software building process. This tool is somehow scheduled. But I found out that it runs under root. I found out that this tool is using the settings from /root/.profile

---

