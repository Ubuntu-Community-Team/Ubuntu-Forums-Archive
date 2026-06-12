---
title: "help needed on running java app"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by scorn_ik on 2007-04-04
i want to run mobile application emulator, mpowerpalyer....whenever i tries it shows me the folloeing eorros:


scornik@scornik-desktop:~/Desktop/mpp-sdk$ java -jar player.jar


""[COLOR="Red"]java.lang.NoClassDefFoundError: net.roydesign.mac.mpj
   at java.lang.Class.initializeClass(libgcj.so.7)
   at com.mpp.player.PowerPlayerApp.<clinit>(PowerPlayerApp.java)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.ClassNotFoundException: com.apple.mrj.MRJOSType not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:player.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   ...4 more
mpowerplayer 2.0.1185
java.lang.NoClassDefFoundError: net.roydesign.mac.mpj
   at java.lang.Class.initializeClass(libgcj.so.7)
   at net.roydesign.mpx.mpa(mpx.java)
   at net.roydesign.mpx.<init>(mpx.java)
   at com.mpp.player.PowerPlayerApp.mpa(PowerPlayerApp.java)
   at com.mpp.player.PowerPlayerApp.mpz(PowerPlayerApp.java)
   at com.mpp.player.PowerPlayerApp.<init>(PowerPlayerApp.java)
   at com.mpp.player.PowerPlayerApp.main(PowerPlayerApp.java)
Exception during event dispatch:
java.lang.NoClassDefFoundError: net.roydesign.mac.mpj
   at java.lang.Class.initializeClass(libgcj.so.7)
   at net.roydesign.mpx.mpa(mpx.java)
   at net.roydesign.mpx.<init>(mpx.java)
   at com.mpp.player.PowerPlayerApp.mpa(PowerPlayerApp.java)
   at com.mpp.player.PowerPlayerApp.mpa(PowerPlayerApp.java)
   at com.mpp.player.PowerPlayerApp.mpa(PowerPlayerApp.java)
   at com.mpp.player.PowerPlayerApp.mpa(PowerPlayerApp.java)
   at com.mpp.player.mptb.run(mptb.java)
   at java.awt.event.InvocationEvent.dispatch(libgcj.so.7)
   at java.awt.EventQueue.dispatchEvent(libgcj.so.7)
   at java.awt.EventDispatchThread.run(libgcj.so.7)[/COLOR]""


please help me run the emulator...

---

### Post by lcg on 2007-04-04
> **scorn_ik said:**
> i want to run mobile application emulator, mpowerpalyer....whenever i tries it shows me the folloeing eorros:

[...]
I don't know this application. But reading through the error messages, I see it is using libgcj. I had some trouble with that and Eclipse a while ago. What Java VM do you have installed on your machine?
If you haven't installed one, try installing the package 'sun-java6-jre'.

HTH,
Lars

---

### Post by scorn_ik on 2007-04-06
thank you for your attention,  i tried to install sun-java6-jre according to your advise but it shows me some dependency error. i have attached the screenshot of that error to clarify  ....  i think i need ia32-sun-java6-bin   package but i didn't find anywhere... i searched it in "packages.ubuntu...", "ubuntu dvdrom"...but still i am lost here....


please help me  ....:(

---

### Post by scorn_ik on 2007-04-06
**[COLOR="Red"]is there noone............!!!!!!!!!!](*,) [/COLOR]**

---

### Post by Maestro23 on 2007-04-06
Do what is says.  Ubuntu is good at telling you what it needs.

This is what I have installed on my system.

> sun-java6-bin
sun-java6-jre
sun-java6-jdk
sun-java6-plugin


---

### Post by scorn_ik on 2007-04-06
i think u r missing my point here..... i cant't find the required dependency while installing jre..

i have already installed jdk6.....

---

### Post by scorn_ik on 2007-04-06
i still nedd help!!!!!!
i am using ubuntu 6.06.....
Maestro23, u sugested me to install sun-java6-plugin.....but in dapper i can't find this package....in edgy i found this package....can i install edgy package in ubuntu 6.06 ?? ? ?

---

### Post by scorn_ik on 2007-04-07
please help me anyone......i am still having problems:(

---

### Post by scorn_ik on 2007-04-10
i just gave my last hope for any other replys.....bye bye

:mad:

---

### Post by vedanuzal on 2007-04-10
if you installed the sun jdk package then it should be installed but you also need to either make sure the gnu version gij is not installed(which they shouldn't be using at all !)  or update your alternatives there are plenty of howto's around just google it.  if this doesn't help you need to post a detailed list of the steps you've taken and the problems that you have had.

---

### Post by cjl2301 on 2007-04-10
You could also just try Sun Java 5 from the official repositories:

```
sudo aptitude install sun-java5-jdk
sudo update-java-alternatives -s java-1.5.0-sun
```

Edit /etc/jvm and move /usr/lib/jvm/java-1.5.0-sun to the top of JVMs offered:
```
sudo gedit /etc/jvm
```

---

### Post by abish on 2008-03-30
hey, i installed the icedtea version. and the javaws too.
works great with me.
but when i load the mpowerplayer's index.jnlp with javaws, 
i get the following error message:

when i run mpowerplayer jnlp file, starts well, out of 1.2 MB, 250 KB is downloaded, then the error message occurs.

Loading player.jar from content.mplayit.com
read 279 KB of 1.2 MB
failed to load resource...
unable to launch mpowerplayer.
this is the error message.

An error occurred while launching/running the application.

Title: mpowerplayer
Vendor: mpowerplayer inc.
Category: Download Error

Corrupted JAR file at [http://content.mplayit.com/client/player.jar](http://content.mplayit.com/client/player.jar)


what do i need to do next>

---

