---
title: "Xforms/chiba and installing tomcat"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by jaseywasey on 2006-01-25
Hello,
I'm wanting to try out a server side implementation of Xforms (web forms/xhtml/xml stuff). There's a server side tool called chiba which requires:

    * JDK/JRE 1.4 or higher
    * a Servlet 2.3 compatible webcontainer

[http://chiba.sourceforge.net/installation.html](http://chiba.sourceforge.net/installation.html)
Installation of Chiba Web on Tomcat 4.1/5.0

    * download [email]chiba-web-@chiba-web-version@.war[/email]
    * copy the WAR-file to $CATALINA_HOME/webapps
    * Important: Extract WEB-INF/lib/dom3-xercesImpl.jar and 

[snip]

    * the step above is not necessary for Tomcat's LE-jdk14 editions
    * start Tomcat
    * point your browser to [http://@baseurl.host@:@baseurl.port@/chiba-web-@chiba-web-version@](http://@baseurl.host@:@baseurl.port@/chiba-web-@chiba-web-version@) to view the sample forms

This looks dead easy which worries me! Has anyone tried this or similar (installing Tomcat). I've used Xampp (apache/php/mysql)automatix for java sdk. I'm going slowly but news of any gotchas would be great. At the moment I don't really feel I'm doing proper linux as I'm using sneaky tools etc. I was expecting more command line typing- I'm disappointed.

---

