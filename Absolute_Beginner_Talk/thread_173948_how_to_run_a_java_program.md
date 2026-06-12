---
title: "how to run a java program"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by hotbrainz on 2006-05-11
well i have the drake dapper beta. I am unable to load Java in it. Even if i manage to. How can i run java programs from the command line. I need this for applications like sockets! Any help much appreciated.

---

### Post by Kobalt on 2006-05-11
Have you installed java yet ? If not : 
```
sudo apt-get install sun-j2re1.5
```

Make sure to have the correct (PLF) repos in your sources.list to install it.

---

### Post by Sef on 2006-05-11
```
sudo apt-get install sun-j2re1.5
```

The above's not the proper way to install java on Dapper.

To install java, go to restricted formats to install it.  If you have not installed Universe and Multiverse, then read the top part of the wiki first.   Java is down at the bottom of the wiki.

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by hotbrainz on 2006-05-11
i read the following steps in a ubuntu help thing:

1.chmod +x jre-1_5_0_06-linux-i586.bin
to get the permissions sorted

2.sudo apt-get install fakeroot java-package java-common

this step 2 is not happening. It says "could not find Java package"

Any help Appreciated

---

### Post by Sef on 2006-05-11
Did you download the java package?

From just above chmod:

[ http://java.sun.com/j2se/1.5.0/download.jsp"][WWW] http://java.sun.com/j2se/1.5.0/download.jsp]("[WWW)

> and click on “Download JRE 5.0 Update 6”. Ensure you do not choose one of the JDK or J2EE versions unless you are going to develop Java applications.

You must first accept the licence, then click on “Linux self-extracting file” (jre-1_5_0_06-linux-i586.bin). Save this file to your hard drive.

Make the downloaded file executable. At the command line, change to the directory where you downloaded the file, and type: 

---

### Post by hotbrainz on 2006-05-11
I got that all right Sef. I think it is the problem of the repositories. I gotta connect to the net to install them is it not?
 It is the  universe-multiverse thing!
I cant get a net connection for my linux system. Can you tell  me how i could download some package of updates to do this. I have a windpws system running and connected to the internet.
Cheers

---

