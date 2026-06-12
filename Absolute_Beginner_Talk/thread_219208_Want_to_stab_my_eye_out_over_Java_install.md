---
title: "Want to stab my eye out over Java install"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by belelelele on 2006-07-19
OKay guys.  I've just installed ubuntu on my machine, and for now, simply want to be able to see java applets from Firefox(straight from the about: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.4) Gecko/20060608 Ubuntu/dapper-security Firefox/1.5.0.4).

I've updated the repositories such that I am getting them from multiverse, and then from Synaptic, I've installed sun-java5-jre, sun-java5-plugin, sun-java5-bin, and just jre.

I also changed the jre to the sun version.

From firefox, when I do run an "about:plugins", I get
```

Java(TM) Plug-in 1.5.0_07-b03

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.5.0_07

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;jpi-version=1.5.0_07 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;jpi-version=1.5.0_07 	Java 		Yes

```

I think I've done just about everything I'm supposed to do, but I still cannot see applets from Firefox.  Given, I am a complete noob to Linux (2nd day), but I really want to make this work.  I've done searches on JRE, JVM, and plugins for Firefox, but I still cannot seem to find an answer.](*,) 

So if someone could help me out with what I'm doing wrong, I'd greatly appreciate it.  Thx.:) :KS

---

### Post by T700 on 2006-07-19
Stop stabbing and just click on the Automatix link in my sig.  It will take care of all your Java problems and do lots of other good things.  It's simple, safe, and easy.

Paul

---

### Post by belelelele on 2006-07-19
Yes, I tried that too but ran into trouble.

From [HTML]http://ubuntuforums.org/showthread.php?t=190025[/HTML], 
after what I felt like was a successful key import, running the "sudo apt-get update" command gives me:

```

Get: 1 http://www.beerorkid.com dapper Release.gpg [189B]
Get: 2 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get: 3 http://us.archive.ubuntu.com dapper-updates Release.gpg [189B]
Get: 4 http://security.ubuntu.com dapper-security Release.gpg [189B]
Hit http://www.beerorkid.com dapper Release
Hit http://us.archive.ubuntu.com dapper Release
Get: 5 http://security.ubuntu.com dapper-security Release [30.9kB]
Hit http://www.beerorkid.com dapper/main Packages
Hit http://us.archive.ubuntu.com dapper-updates Release
Hit http://us.archive.ubuntu.com dapper/main Packages
Hit http://us.archive.ubuntu.com dapper/restricted Packages
Hit http://us.archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper/multiverse Packages
Hit http://us.archive.ubuntu.com dapper/main Sources
Hit http://us.archive.ubuntu.com dapper/restricted Sources
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://us.archive.ubuntu.com dapper-updates/main Sources
Hit http://us.archive.ubuntu.com dapper-updates/restricted Sources
Get: 6 http://security.ubuntu.com dapper-security/main Packages [39.4kB]
Get: 7 http://security.ubuntu.com dapper-security/restricted Packages [4275B]
Get: 8 http://security.ubuntu.com dapper-security/main Sources [9552B]
Get: 9 http://security.ubuntu.com dapper-security/restricted Sources [974B]
Fetched 85.3kB in 1s (53.3kB/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?

```


Soo, That's that, but I still want to be able to run JAVA, and Automatrix later, but one step at a time...

---

### Post by T700 on 2006-07-19
Something has you locked.  Do you have a terminal open or Adept or Symantic running?  If not, I'd reboot and try again.  If you still get that, you'll need delete the lock files.

Paul

---

### Post by belelelele on 2006-07-19
Hmm... how do u run the "sudo apt-get update" without opening a terminal?  Sorry, soy un noob.

---

### Post by T700 on 2006-07-19
> **belelelele said:**
> Hmm... how do u run the "sudo apt-get update" without opening a terminal?  Sorry, soy un noob.

Sorry, I wasn't clear.  It sounds like you have *two* things running, trying to lock.  My suggestion was to make sure that only one terminal or application is trying to apply the lock at a time.  Sometimes things can be running in the background, so that's why the suggestion to reboot and/or delete the files by hand.

Paul

---

### Post by Kilz on 2006-07-19
I wonder what version the orignal poster is running. If its amd64 they may have trouble seeing java in the defalut firefox.

---

### Post by belelelele on 2006-07-19
> **T700 said:**
> Sorry, I wasn't clear.  It sounds like you have *two* things running, trying to lock.  My suggestion was to make sure that only one terminal or application is trying to apply the lock at a time.  Sometimes things can be running in the background, so that's why the suggestion to reboot and/or delete the files by hand.

Paul

GAh!  Had another terminal open in another workspace.  Installed Automatrix successfully but still have problems with Java in Firefox.

---

### Post by belelelele on 2006-07-19
> **Kilz said:**
> I wonder what version the orignal poster is running. If its amd64 they may have trouble seeing java in the defalut firefox.


Version of?  I'm not running an amd64 machine, but am running one w/ Xeon, but not sure if that makes a difference?

---

### Post by sean_ on 2006-07-19
[http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox) This should hlep.

---

### Post by Kilz on 2006-07-19
> **belelelele said:**
> Version of?  I'm not running an amd64 machine, but am running one w/ Xeon, but not sure if that makes a difference?

I was asking what version of Ubuntu you installed, the 32bit 1386 version, or the 64bit amd64 version.

---

### Post by catlett on 2006-07-19
[http://www.ubuntuforums.org/showthread.php?t=211828](http://www.ubuntuforums.org/showthread.php?t=211828) Go to that thread and scroll down to the third poster. It is "Artificial Intelligence" an Ubuntu Forum Staff Member. Just follow the steps laid out in the post.
Since you are new I'll explain a little more.
Open up a terminal. Then just copy/paste the commands A.I. listed. One at a time and press enter after every string of commands.
This will give you the latest install of java, as well as a way to verify you have it installed.

---

### Post by belelelele on 2006-07-19
> **catlett said:**
> [http://www.ubuntuforums.org/showthread.php?t=211828](http://www.ubuntuforums.org/showthread.php?t=211828) Go to that thread and scroll down to the third poster. It is "Artificial Intelligence" an Ubuntu Forum Staff Member. Just follow the steps laid out in the post.
Since you are new I'll explain a little more.
Open up a terminal. Then just copy/paste the commands A.I. listed. One at a time and press enter after every string of commands.
This will give you the latest install of java, as well as a way to verify you have it installed.


Alright I followed these instructions, and 

```
....-desktop:~$ java -version
java version "1.5.0_07"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_07-b03)
Java HotSpot(TM) Client VM (build 1.5.0_07-b03, mixed mode, sharing)

```

it still doesn't work!  *sigh...

---

### Post by belelelele on 2006-07-19
> **Kilz said:**
> I was asking what version of Ubuntu you installed, the 32bit 1386 version, or the 64bit amd64 version.

How do you check this?  
    
When going to "about Ubuntu" under System, I found...

Thank you for your interest in Ubuntu 6.06 LTS - the Dapper Drake - released in June 2006.


Nothing leads me to believe its the 64 bit edition...
How do you check this?  Sorry fro the ?;'s...

---

