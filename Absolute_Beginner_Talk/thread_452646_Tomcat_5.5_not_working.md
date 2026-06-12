---
title: "Tomcat 5.5 not working"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by neo.patrix on 2007-05-23
I have installed tomcat-5.5 with webapps and admin. 

Also I had fixed tomcat5.5 deamon code according to  [https://bugs.launchpad.net/ubuntu/+source/tomcat5.5/+bug/97096]("https://bugs.launchpad.net/ubuntu/+source/tomcat5.5/+bug/97096")

tomcat5.5 did execute properly for few time it was able to use homepage, jsp-examples, servlet-examples on [http://localhost:8180/](http://localhost:8180/)

But after few startup it simply stopped working!!! When i start it with command "sudo /etc/init.d/tomcat5.5 start" it does show status as OK.

but when I check status , I get "not running" instead of PID !!!

I also removed tomcat5.5 using "aptitude purge" and reinstalled it, but it keeps giving me same
error?

---

### Post by nyvalbanat on 2007-06-08
Is there anything in your tomcat logs?
Can you start tomcat using its bin/startup.sh script?

---

