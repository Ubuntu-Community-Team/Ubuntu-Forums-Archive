---
title: "Tomcat login and restart problem"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by thepiston on 2008-03-12
Ok, after a meltdown trying to use Tomcat 6 on 6.10 (which you should never ever try btw) I have it running on 7.10.  I used this tutorial:
[http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/](http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/)

2 problems though: 

1) I have this in my conf file, but I still can't log in using this username/pass:
> <tomcat-users>
<role rolename="manager"/>
<user username="tomcat" password="s3cret" roles="manager"/>
</tomcat-users>

Also
2) when I try to restart Tomcat, after it says "using JRE_HOME: /usr/lib/jvm/java-6-sun" it says 

> /usr/local/tomcat/bin/catalina.sh:  356: /usr/lib/jvm/java-6-sun/bin/java: not found

I'm too much of a noob to know if these things have anything to do with each other...

---

### Post by Hospadar on 2008-03-13
Do you have sun-java-6 installed?

---

### Post by thepiston on 2008-03-13
> **Hospadar said:**
> Do you have sun-java-6 installed?

yep, i installed it like the tutorial said

---

### Post by thepiston on 2008-03-13
found the problem - noscript...

---

