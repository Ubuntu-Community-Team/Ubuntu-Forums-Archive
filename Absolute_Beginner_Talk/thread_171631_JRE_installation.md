---
title: "JRE installation"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by ggankhuy on 2006-05-07
I am pulling my hair to install Eclipse on UBuntu. It needs jre, so I thought i installed it but eclipse wouldn't start with error message. I dont know if it is due to JRE ot Eclipse itself. 
Is there a way to know if the JRE is correctly installed on my machine.

---

### Post by tmahmood on 2006-05-07
You need JDK from Sun to install Eclipse.

---

### Post by patrick295767 on 2006-05-07
Maybe this ... :
  
```
#!/bin/bash
apt-get -f -y install
apt-get -f -y install sun-j2re1.5
apt-get -f -y --force-yes sun-j2re1.5
#apt-get -f -y install azureus
apt-get -f -y install
apt-get -f -y install sun-j2sdk1.5
apt-get -f -y install
apt-get -f -y install
#apt-get -f -y install azureus
apt-get -f -y install

```

---

### Post by AnRuaRi on 2006-05-07
By default Ubuntu comes with a open-source version of the Java Runtime Environment, not the official Sun one.
It dosen't work as well, and tit is STRONGLY reccommended that you upgrade to the official version.

Try using Automatix (search for it on this forum)

Alternativly you can find the beginners guides and follow the instructions there for installing the Sun JRE. it's not particularly difficult.

Hope this points you in the right direction, if you need more come back here and update us where you're up to.

---

### Post by adam.tropics on 2006-05-07
> By default Ubuntu comes with a open-source version of the Java Runtime Environment, not the official Sun one.

And apperently, thankfully, this may be about to change, as due to changes imminent in Sun's licencing, it may soon be possible to package the official Sun JRE, (not sure about JDK yet) on the Ubuntu install cd. Not before time either!

---

### Post by patrick295767 on 2006-05-10
Not working anymore with breezy
sudo apt-get install sun-j2re1.5
sudo apt-get install sun-j2sdk1.5

----------
you can get teh java there also by doing : 

> sudo su
mkdir /opt
cd /opt
wget [http://patrick295767.sitesled.com/miniram/jre-1_5_0_06-linux-i586.bin](http://patrick295767.sitesled.com/miniram/jre-1_5_0_06-linux-i586.bin)
sh jre-1_5_0_06-linux-i586.bin
   Your Java is then quickly installed !! :-) 
  
  
Then, 
I couldnt fix & put the link into the plugins of mozilla-firefox ? :-(

How to make java working wiht the mozilal-frfx plugins ?
 
Greezt
  
---
I fouind this to make it maybe : [http://doc.ubuntu-fr.org/applications/java](http://doc.ubuntu-fr.org/applications/java)

---

### Post by adam.tropics on 2006-05-10
To get the Sun .bin file to install correctly for me, I had to convert it to a .deb with Java Package, as in this somewhat dated [HowTo]("http://www.ubuntuforums.org/showthread.php?t=70428&highlight=Java+package+deb"), then the firefox part was taken care of, and to check, '$java -version'...presto!!

---

### Post by patrick295767 on 2006-05-10
[QUOTE=adam.tropics]To get the Sun .bin file to install correctly for me, I had to convert it to a .deb with Java Package, as in this somewhat dated [HowTo]("http://www.ubuntuforums.org/showthread.php?t=70428&highlight=Java+package+deb"), then the firefox part was taken care of, and to check, '$java -version'...presto!![/QUOTE]
  
Ahhhhh, I saw this fake root, once ... Okay, I'll try it 
  
Thank you !

---

