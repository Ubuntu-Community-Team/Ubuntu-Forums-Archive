---
title: "Tomcat Permission denied"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by sim085 on 2007-07-27
hi,

I have installed Tomcat and it works find when I start it from the administrator account. However I created another account as "Desktop User" and when i try to start Tomcat I get the following on the terminal:```
developer@administrator-basic:/usr/local/lib/apache-tomcat-6.0.13/bin$ sh startup.sh
Using CATALINA_BASE:   /usr/local/lib/apache-tomcat-6.0.13
Using CATALINA_HOME:   /usr/local/lib/apache-tomcat-6.0.13
Using CATALINA_TMPDIR: /usr/local/lib/apache-tomcat-6.0.13/temp
Using JRE_HOME:       /usr/lib/jvm/java-1.5.0-sun-1.5.0.11/
touch: cannot touch `/usr/local/lib/apache-tomcat-6.0.13/logs/catalina.out': Permission denied
./catalina.sh: 338: cannot create /usr/local/lib/apache-tomcat-6.0.13/logs/catalina.out: Permission denied
developer@administrator-basic:/usr/local/lib/apache-tomcat-6.0.13/bin$
```A friend of mine suggested that i create a new User Group and use 'chown' on that user group so that I can have access to that folder. However this does not seem to work. 

Does anyone know how I can solve this problem?

Regards,
Sim085

---

### Post by sim085 on 2007-07-27
Could at least someone tell me how to give permissions to a user group. I can give permissions to a user without any problem but I am having problems to find the syntax on how to give permissions to a user group so that each user within that user group will have access to tomcat folder.

Regards,
Sim085

---

### Post by rax_m on 2008-07-04
Permissions in Unix for both users and groups are all given with the same command

Normally when doing an "ls -l" from the terminal you'll see something like:
```

-rwxrwx---   1 tomcat55 adm      1678 2007-10-09 22:18 server-minimal.xml
-rwxrwx---   1 tomcat55 adm     19334 2008-04-18 09:58 server.xml

```
I can't remember what the first dash represents, bu after that the perms are as follows:

rwx   rwx   rwx
user  group everyone

So in the above file listsing, the user and group that owns the file can read, write and execute the file. You grant permissions with 
```
 chmod xxx somefile 
```
where xxx is the permissions you want to grant. Do "man chmod" for more on how it works.

---

