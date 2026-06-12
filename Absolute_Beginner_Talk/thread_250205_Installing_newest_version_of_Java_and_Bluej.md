---
title: "Installing newest version of Java and Bluej"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by petrockthief on 2006-09-03
Yeah, I'm really new to linux. I dowloaded the jdk and jre .bin files and tried to incorporate that into the Add/Remove Apps menu but it didn't work. I also have a .jar file for a program called Bluej. I thought I just had to ```
java -jar bluej.jar
``` anyways I can't make sense of it and your help would be appreciated until I get a feel for this.

---

### Post by jrock08 on 2006-09-08
If you downloaded it from the bluej site, as I assume you did then you probably also looked at the installation instructions.  They say,

> Run the installer by executing
java -jar bluej-213.jar 

I did this after cd Desktop as that is where my files download to and,
> jrock@jrock-desktop:~/Desktop$ java -jar bluej-213.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at java.awt.Font.tk(libgcj.so.7)
... and so on 


My question for you is do you have the JDK installed.  Also if you could post the terminal text it would make troubleshooting easier.

Jrock

---

### Post by Optimus Prime on 2006-09-11
This installer cannot be run using the GCJ version of Java. To set the official Sun Java to be the default, run ```
sudo update-java-alternatives -s java-1.5.0-sun
```
then execute the jar file using ```
java -jar bluej-213.jar
```
It installed for me using this method, and should be work fine as long as you have the sun-java5-jdk package installed.

Good luck,
Optimus Prime

---

### Post by jrock08 on 2006-09-12
ok so I know I have the latest java and I changed sun java to be my default however i still get an error

```
Unable to access jarfile bluej-213.jar
```

Any ideas?

---

### Post by D_frag on 2006-09-12
i have a somehow similar problem i downloaded the java 2 sdk with netbeans and it's a .bin file sitting on my desktop but i dunno how to install it ?

---

### Post by Timothy Butwinick on 2006-09-12
I also had some problems installing Java. Try Easy Ubuntu 
[http://ubuntuguide.org/wiki/Dapper#How_to_use_Easy_Ubuntu](http://ubuntuguide.org/wiki/Dapper#How_to_use_Easy_Ubuntu)

---

### Post by steve.horsley on 2006-09-12
> **D_frag said:**
> i have a somehow similar problem i downloaded the java 2 sdk with netbeans and it's a .bin file sitting on my desktop but i dunno how to install it ?

**sudo sh ./whateverItIs.bin** should do it.

Or
[B]chmod +x ./whateverItIs.bin
sudo ./whateverItIs.bin[/B]

---

### Post by steve.horsley on 2006-09-12
> Unable to access jarfile bluej-213.jar

That's basically "file not found". Do **ls** to make sure it's in your current directory, and check the spelling (case sensitive).

---

### Post by jrock08 on 2006-09-14
ok so i must have forgotten to cd to desktop last time. 


ok got it to work thanks alot

---

### Post by atraub on 2007-11-23
I'm trying to install BlueJ, and it asks me where java is installed.  I found several folders throughout my harddrive with java-like names, but what folder would it be looking for by default?  (Very new to Ubuntu, long time user of BlueJ).  I'm going insane trying to figure it out!!  Somebody help me!!!

---

### Post by airawan on 2007-11-27
Try /usr/local/java
If you have install java from synaptic or add/remove, it should be located under /usr/lib/jvm

---

### Post by The Cog on 2007-11-27
If you are going to use bluej, you should install the Sun java JDK first. The package is in Synaptic.

I don't know where it installs to though. This command will help find it:
find / -name java 2>/dev/null

---

