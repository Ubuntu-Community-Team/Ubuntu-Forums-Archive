---
title: "java version incorrect"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by jafmontes on 2008-03-18
hi everyone, 

newbie help required.

I just installed ubuntu 7 and also have upgrade the java version to 1.6.0_03.

Searched the forums and also checked the following cmds:

java -version = which showed the correct version

sudo update -alternatives -- config java which again showed the default java to be used.

ran about:plugins on ff and showed the the new java version plugins are installed.

also checked ff and java is definitely enabled.

when i tried this link to verify whether java is installed , [www.java.com](www.java.com), it just came back with a message that I'm running 1.4 instead of 1.6

I'm running out of options and hence I posted one here.  Hope someone can help.

Thanks,

---

### Post by Ub1476 on 2008-03-18
Search for java/jre in Synaptic to see what is installed.

---

### Post by forrestcupp on 2008-03-18
Well, you could try removing all versions and reinstalling, like this:
```
sudo apt-get --purge remove sun-java*
```
then reinstall the correct version
```
sudo apt-get install sun-java6-plugin
```

Maybe that will work.

---

### Post by jafmontes on 2008-03-19
thank you everyone for your suggestions.  I just removed the GCJ JRE and it's now working.

---

### Post by justanotherhandle on 2008-03-19
For the next time, it is also necessary to move the java-sun-Version line to the top of the file in /etc/jvm 

By default it written below the java-gcj and the jre on top is the one run by default. 

HTH

---

### Post by breakerr on 2008-03-19
> **forrestcupp said:**
> Well, you could try removing all versions and reinstalling, like this:
```
sudo apt-get --purge remove sun-java*
```
then reinstall the correct version
```
sudo apt-get install sun-java6-plugin
```

Maybe that will work.

Hello there.....this is similar to my issue....but what happens to me is....

.**..I CANT UPDATE**  I have version 1.6.0_03  and I removed that to install version 1.6.0_05 but I don't get it.....trying and trying...avoiding to be bothering around here...but no clue...at the end I need your help guys, please!!!!!!!

I already tried this[ link]("http://java.sun.com/javase/6/webnotes/install/jdk/install-linux.html#self-extracting") from java sites but the part on the command to specify version I dont get it right chmod +x jdk-6_<version>_-linux-i586.bin  What I'm suppose to change or how to edit/substitute the version part for....what goes in version with the arrows symbols or without it ???  and how could I know if I have permission like they mention there ( Make sure that execute permissions are set on the self-extracting binary.) ????

---

### Post by glennric on 2008-03-19
sun java 6 update 3 is the version in the repositories. You can't update to version 6 update 5 using the repositories.

---

### Post by breakerr on 2008-03-19
> **glennric said:**
> sun java 6 update 3 is the version in the repositories. You can't update to version 6 update 5 using the repositories.

But how can I get the latest version then ??? I want** 1.6.0_05** and the instruction in the file or java website aren't working for me ??? do I need to disable the repos and do a bunch of steps like compiling....I know squad about :redface: com:-kpiling ???

---

### Post by glennric on 2008-03-19
Here is a tutorial on how to do it
[http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation_with_java-package]("http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation_with_java-package")

---

### Post by breakerr on 2008-03-19
> **glennric said:**
> Here is a tutorial on how to do it
[http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation_with_java-package]("http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation_with_java-package")

From the link you gave me: *[http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation_with_java-package](http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation_with_java-package)*

After I do:    **apt-get install java-package**  I tried to add the correct version to the command by replacing the number 5   inside the command line for a number 6

(***fakeroot make-jpkg jre-1_5_0_05-linux-i586.bin***) I transform that into (***fakeroot make-jpkg jre-1_6_0_05-linux-i586.bin***) to gt the latest version and what I get is:

root@breaker-desktop:~# fakeroot make-jpkg jdk-6u5-linux-i586.bin
You are real root -- unfortunately, some Java distributions have
install scripts that directly manipulate /etc, and may cause some
inconsistencies on your system. Instead, you should become a
non-root user and run:

fakeroot make-jpkg jdk-6u5-linux-i586.bin

which will allow no damage to be done to your system files and
still permit the Java distribution to successfully extract.

Aborting.

---

### Post by igknighted on 2008-03-19
1) what does java6_05 have that java6_03 doesn't that you need so bad?  If it's just to have the latest, it probably isn't worth it.

3) Why are you logged in as root?  Type 'exit' to return to your normal user, then run the fakeroot command.

2) That's a really hard way to install... follow the directions on the sun site... much easier (although certainly not the "preferred" way.

---

### Post by glennric on 2008-03-19
> **igknighted said:**
> 1) what does java6_05 have that java6_03 doesn't that you need so bad?  If it's just to have the latest, it probably isn't worth it.

3) Why are you logged in as root?  Type 'exit' to return to your normal user, then run the fakeroot command.

2) That's a really hard way to install... follow the directions on the sun site... much easier (although certainly not the "preferred" way.

He is right.  You should not be logged in as root.  However, I disagree that you should follow the directions on the sun site.  That is not the proper way to install java on a (ubuntu) debian system.  The proper way (if you insist on not installing from the repositories) is to use make-jpkg.

---

### Post by breakerr on 2008-03-19
> **glennric said:**
> He is right.  You should not be logged in as root.  However, I disagree that you should follow the directions on the sun site.  That is not the proper way to install java on a (ubuntu) debian system.  The proper way (if you insist on not installing from the repositories) is to use make-jpkg.

Thanks to both...is appreciated for real...thanks so much.....I already gave up and now installing java6_03 again after I removed :p  what happened is that I tried to open a few pss files in my email inbox and sometimes they tell me that I don't have the proper version of java to see that specific pss/powerpoint file...but is ok...I can live with it I guess.

---

### Post by breakerr on 2008-03-20
> **glennric said:**
> He is right.  You should not be logged in as root.  However, I disagree that you should follow the directions on the sun site.  That is not the proper way to install java on a (ubuntu) debian system.  The proper way (if you insist on not installing from the repositories) is to use make-jpkg.

Now I screwed all.....I have an older java version 1.4.2 classpath and everytime Im loading a java content site/page I get a little window saying:  
[U]Click "Cancel" if you do not trust the source of this applet.
Click "Trust Applet" to load and run this applet now.
Click "Trust Applet and Add To Whitelist" to always load and run this applet from now on, without asking.
The whitelist is a list of the URLs from which you trust applets.
Your whitelist file is " /home/breaker/.gcjwebplugin/whitelist.txt ".[/U]

But when I type **java -version** on terminal I get:
[I]java version "1.6.0_05"
Java(TM) SE Runtime Environment (build 1.6.0_05-b13)
Java HotSpot(TM) Client VM (build 10.0-b19, mixed mode, sharing)[/I]

What the *@@**%3 did I do ????? HELP!!!!

---

