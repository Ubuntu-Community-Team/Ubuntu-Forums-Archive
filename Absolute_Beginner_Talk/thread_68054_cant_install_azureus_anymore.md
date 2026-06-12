---
title: "cant install azureus anymore??"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by servvs on 2005-09-21
ok, i had hoary installed and i installed azureus just fine. i installed breezy, then went back to hoary. I enabled the repositories and i tried to install azureus and i get this error 
The following packages have unmet dependencies:
  azureus: Depends: sun-j2sdk1.5 but it is not installable or
                    java2-runtime but it is not installable
I dont know what is the problem, but i think it may have something to do with my repositories. could someone email me there sources.list file? [email]servvs@gmail.com[/email]

Or if there is another way i can get rid of this problem can someone point me in that direction.

---

### Post by Blue1k on 2005-09-22
This has been mentioned on another post and doesn't seem to be available for now. What you could do is install the self-extracting file from here:

[http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp) 


Basically the easiest way to install this (at least for me is to do this)

1. create /usr/java directory
type in console: **sudo mkdir /usr/java**
2. move the jre bin file into the new java folder
type: cd /(to the place where you saved the java bin file)
for example: **cd /home/user/**
then type: **sudo mv jre-1_5_0_04-linux-i586.bin /usr/java**
3. Install Java
type: **cd /usr/java**
then type:** sudo ./jre-1_5_0-linux-i586-rpm.bin**
4. You need to link the installed java to the usr directory so that other programs "see" it such as azureus.
type: **ln -s /usr/java/jre1.5.0_04/bin/java /usr/bin/java**
*might need sudo command-can't remmeber for this step

I tried to install the azureus from the repositories but it stil couldn't see java.
If you use the Azureus from the home Azureus site (GTK version), it works perfectly.

---

### Post by bored2k on 2005-09-22
Java has been on and off the backports, so we will now make you a package:

[http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp)

Download the JRE .BIN executable

```
sudo apt-get install fakeroot java-package
```

Go to the dir where the package is downloaded:
```
fakeroot make-jpackage FILENAME.bin
```
```
sudo dpkg -i *.deb
```

That will create a debian java package that's easy to manage via Synaptic.

---

### Post by hippyjim on 2005-09-23
[QUOTE=Blue1k]
3. Install Java
type: **cd /usr/java**
then type:** sudo ./jre-1_5_0-linux-i586-rpm.bin**
[/QUOTE]

Gives me: 

sudo: ./jre-1_5_0-linux-i586-rpm.bin: command not found

[QUOTE=bored2k]
fakeroot make-jpackage FILENAME.bin
[/QUOTE]

gives me:

/usr/bin/fakeroot: line 150: make-jpackage: command not found

Anyone got any ideas, it'sdriving me nuts not having a decent bittorrent client!

And for some reason Ktorrent is rejected by my tracker......but they're really fussy.

---

### Post by bored2k on 2005-09-23
My bad. Try this:
```
sudo apt-get install java-package fakeroot
``` 
```
fakeroot make-jpkg filename.bin
``` 


If it doesnt work try,
Try ```
sudo bash jre-1_5_0-linux-i586-rpm.bin
```

---

