---
title: "Creating new applications for tomcat?"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by iangregson on 2007-09-25
Hi there,

can anyone tell me what i need to do to create a new web applicaton under tomcat... for example it ships with docs, samples etc... what if i need to create "myOwnApp".. hence [http://localhost:8080/myOwnApp](http://localhost:8080/myOwnApp) is where my new app would be ...

I will be using eclipse... but still very new to this... 

Also probably stupid question, but how do i get my files to my server... because in my situation i have myEclipse on Windows Vista and my tomcat/apache on ubuntu ... Does myEclipse/eclipse support uploading the files automatcally or do i ftp or should i setup samba... or something?

Thanks in advance for any info..

---

### Post by sgordon on 2007-10-03
Well, the basic answer would be to create a 'WAR' (Web ARchive) file which contains the content for your application. In your example, call it ```
myOwnApp.war
```

This is basically a .zip file which contains your application. The eclipse 'jar' tool should be suitable for this task. So the tomcat-docs application could have been deployed (if not already there) by creating a ```
tomcat-docs.war
``` file which contains (top level) appdev, config folders etc. and the WEB-INF folder which has the web.xml file which you will probably need.

Deploying to the server gives you a few options. Copying the WAR file to the 'webapps' folder is the simplest, but needs something running on your server waiting for the file to be copied, samba or FTP as you suggest.

Tomcat also comes with a manager application to interactively deploy webapps. bit harder to automate, but not impossible. A clever wget from the client would work!

That get you any closer?!

  Si

---

