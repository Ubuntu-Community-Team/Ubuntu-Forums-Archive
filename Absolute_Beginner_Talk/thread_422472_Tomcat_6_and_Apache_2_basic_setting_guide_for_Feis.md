---
title: "Tomcat 6 and Apache 2 basic setting guide for Feisty"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by garylai on 2007-04-25
This is the continuing guideline of "[Tomcat 6 installation guide for Feisty]("http://ubuntuforums.org/showthread.php?t=420034&highlight=tomcat")". It is about the basic setting between tomcat 6 and apache 2 which make them work better, and I hope you enjoy it!

_Step 1_: install the libapache2-mod-jk
***sudo apt-get install libapache2-mod-jk***

_Step 2_: After that, check whether there is **jk.load** in the apache 2 modules
***sudo ls /etc/apache2/mods-enabled/***
If your result like this, that's fine:
[B]cgi.load  mod-security.conf  php5.conf  proxy.conf  rewrite.load  userdir.load
_jk.load_   mod-security.load  php5.load  proxy.load  userdir.conf[/B]

_Step 3_: Edit and save the two lines of **workers.properties**
***sudo vi /etc/libapache2-mod-jk/workers.properties***
[B]workers.tomcat_home=/usr/share/tomcat6
workers.java_home=/usr/lib/Java6U1[/B]

_Step 4_: **apache2.conf ** setting
Open and copy all the content in **httpd_example_apache2.conf**
***sudo vi /usr/share/doc/libapache2-mod-jk/httpd_example_apache2.conf***
then paste the content following the last line of **apache2.conf**

_Step 5_: Edit **rc.local**
***sudo vi /etc/rc.local***
[B]export JDK_HOME=/usr/lib/Java6u1
export JAVA_HOME=/usr/lib/Java6u1[/B]

_[Step 6_: Restart apache2
***sudo /etc/init.d/apache2 restart***

_Step 7_: Restart tomcat
[I][B]sudo /usr/share/tomcat6/bin/./shutdown.sh
sudo /usr/share/tomcat6/bin/./startup.sh[/B][/I]

Now the basic setting is finished, then load your jsp files to usr/share/tomcat6/webapps/ROOT

---

### Post by tb323 on 2007-04-30
I followed your guide succesfully, but now I'm stuck. I have read some threads about this "problem" but still no go:
I'd like to place my webapps directory inside my public_html. 

In /usr/share/tomcat6/conf/server.xml: 
..
<Host name="localhost"  appBase="/home/myhome/www/public_html/webapps"
            unpackWARs="true" autoDeploy="true"
            xmlValidation="false" xmlNamespaceAware="false">

          <Context path="" docBase="."/>
..
Unsure about the context-tag.. some say it should be there and others say it shouldn't.

What am I missing?

---

