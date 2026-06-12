---
title: "can't log into tomcat5 manager"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by bandito40 on 2007-09-03
Hi all,


I am having problems logging into Tomcat5 manager.  I set the user and password in the tomcat-users.xml file which gets me passed login popup but I get a page that says this:

-------------------------------------------------------------------------------------------------------------
HTTP Status 403 - Access to the requested resource has been denied

type Status report

message Access to the requested resource has been denied

description Access to the specified resource (Access to the requested resource has been denied) has been forbidden.
Apache Tomcat/5.0
----------------------------------------------------------------------------------------------------------

It is the same when I log into Tomcat Administration.


I am trying to get in because this is the method to compile a servlet laid out on [https://help.ubuntu.com/community/ApacheTomcat5.]("https://help.ubuntu.com/community/ApacheTomcat5")

Any ideas?

Carl

---

### Post by ptillemans on 2007-09-04
Check that the user you have defined has the proper roles :

```
  <user username="admin" password="admin" roles="admin,manager"/>

```

Also I've noticed the latest versions of tomcat have no more admin/manager applications deployed,  And in ubuntu/debian the admin application is in a separate package.

Which is Ok for me since I find these clunky apps a waste of (disk)space. Drop your war in /var/lib/tomcat5/webapps/ and restart the tomcat server. A lot easier and faster 

Also if it is for development, then look into the xml deployment desciptor to allow you to do development in place instead of always (re)deploying.

grts,

Peter

---

### Post by bandito40 on 2007-09-04
Thanks,

That did the trick!:)

---

