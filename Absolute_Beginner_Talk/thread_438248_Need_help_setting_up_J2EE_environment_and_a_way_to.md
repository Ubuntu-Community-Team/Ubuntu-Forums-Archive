---
title: "Need help setting up J2EE environment and a way to edit from another PC"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by AbsurdParadigm on 2007-05-09
Hi,

I'm new to Linux, as of last week.  I'm currently unemployed and trying to build up my skills while looking for my next job.

I'm trying to set up a J2EE server on my Ubuntu 6.10 server, but I'm having a bit of difficulty. I'm getting extremely frustrated. I've had the machine set up for about a week now. I have figured out that Apache is indeed running and I can view web pages from my other (Win XP) machine.

I have been reading up and have installed KDE, Synaptic, Krusader, Firefox, and a few others. As far as J2EE goes, I have installed Tomcat 5.

First of all, what does everyone recommend to install for a J2EE server? Secondly, I have been trying to unpack Sun's j2sdkee 1.3.1 in usr/local/, but it was giving me fits. Isn't that the directory where I want to install things like that?

Does anyone know of a good tutorial to set up J2EE? I've found lots of sources, but everything is a bit vague for beginners.  :(   After a week of screwing around, I feel like I'm getting nowhere, except in learning new curse words. All I have to show for my trouble is a huge headache.

My father hangs out on theses forums and he said you guys are pretty nice and helpful. If someone could help me out, I'd really appreciate it!

What I need to know is

1) How do I set this server up as a J2EE environment?
2) How do I install things to usr/local/? It keeps giving me problems, even when I try to do commands with sudo.
3) How do I set up a way to edit the files from my Win XP machine? FTP Server? How do I configure that?

Brent

---

### Post by vikram on 2007-05-11
Hi Brent,

Here's what I did to install the JDK 

 sudo apt-get install sun-java5-jre sun-java5-fonts sun-java5-plugin
 sudo update-alternatives --set java /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

you can install and use eclipse for java development and debugging on the linux box itself no need for using ftp server. eclipse is also a great UI to know as it is often used in commercial J2EE  projects (or Websphere Application Development IDE which is also Eclipse based)

all the best and remember to have fun !

---

### Post by Zootropo on 2007-05-19
> **vikram said:**
> Hi Brent,

Here's what I did to install the JDK 

 sudo apt-get install sun-java5-jre sun-java5-fonts sun-java5-plugin
 sudo update-alternatives --set java /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

you can install and use eclipse for java development and debugging on the linux box itself no need for using ftp server. eclipse is also a great UI to know as it is often used in commercial J2EE  projects (or Websphere Application Development IDE which is also Eclipse based)

all the best and remember to have fun !

He's talking about the Enterprise Edition, you are talking about the Standard Edition and also giving indications on how to install the JRE, and not the JDK

---

