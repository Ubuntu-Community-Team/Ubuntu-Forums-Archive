---
title: "synaptic challenge"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by grekei on 2007-06-08
I was using the Synaptic package manager to install some java programming packages(about to start an online IT course which includes intro to Java).The installation stalled and when I looked at the details it  needed a download from Sun(it was unclear what to down load and the address appears to be incorrect) so I took the abort option[Press RETURN to try again, 'no' + RETURN to abort]which did not work.After several attempts I shut down to escape synaptic .On rebooting and opening synaptic got message  dpkg --configure -a
The return message was 
Setting up sun-java6-doc (6-00-2ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.
I think I have downloaded the correct package to temp. but I don't know:
1  how to make it owned by root
2 if this is all I have to do to make every thing install and work
Hoping somebody out there can help 
                                                                      Cheers

---

### Post by kill4killin on 2007-06-08
If you are having that much trouble I might suggest you use automatix...it is not exactly recommended by most people but personally I loved it. Just install that and then look through for the JDK and what have you and install them that way.

---

### Post by Emerzen on 2007-06-08
Hi, I should start by telling you I don't code in Java, so I can't be very specific about your problem.  The simplest way to change file/folder ownership/permissions is:

```
gksudo nautilus
```

This will open the file browser as root.  Find the file/folder you want, right click it, select properties and go to Permissions tab.  You can change the owner, group, permissions etc... from there.

I'm not sure, but it sounds like you've just installed the documentation for Java.  I recommend going under the Applications Menu-> Add/Remove...-> and search for Java or under the Programming section.  This will install everything you need instead of just one package.  If that fails, I suggest trying Automatix:

[Automatix]("http://www.getautomatix.com/")

---

### Post by grekei on 2007-06-08
Have resolved root ownership of download ,thank you.Have also worked out how to abort the original install that was stuck in synaptic(I was using a syntax error previously).Will now start again from scratch thanks for all input.Please consider this resolved for now
Cheers:)

---

