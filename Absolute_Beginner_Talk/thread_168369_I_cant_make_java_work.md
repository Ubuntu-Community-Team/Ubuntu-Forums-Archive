---
title: "I cant make java work"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by eyesoftheworld on 2006-04-30
someone please help me, im having some serious problems getting java to install on my computer, ive tried following the directions but it doesnt ever work for me

---

### Post by jazzmuzik on 2006-04-30
What instructions are you following? What have you tried?

---

### Post by halitech on 2006-04-30
what version of java are  you trying to install and from where?

---

### Post by catlett on 2006-04-30
Lately this advice has become a bit controversial on Ubuntu forums[-X . Many people believe (and righfully so I suppose:-k ) that the script I'm about to lead you to is too "easy". That a new user doesn't learn anything buy running the script. That although they get everything they need to run there computers' browsers, mp3 players and media players the user didn't learn the process or understand their configuration.
My reasoning is, if this script gets people up and running they will stay in their Linux os and not boot into windows to do certain things. That they won't learn right away but by them staying in their linux os and using it they will have opportunities to learn more and want to because they like their system.
 If they can't figure out the installs and give up on it, they won't have learned and they won't be running Ubuntu.#-o  
That being said, follow this link [http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)  It will give you directions on how to install Automatix. Automatix will install Java and many other things (i.e. Firefx 1.5 and all plug-ins, totem movie player with codecs, mp3 players and more). It makes life easy. You won't learn how to install stuff but the stuff will be installed and usable.=D>

---

### Post by testube_babies on 2006-05-01
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

This includes a detailed java installation guide.

---

### Post by joshrobinson on 2006-05-01
download the jre 1.5 bin from the sun java website


put it in /usr/java  you have to make the dir java
use sudo nautilus to have a root file browser

or sudo mkdir java while in the usr directory
rename the bin java.bin for ease of typing filenames

sudo chmod +x java.bin
sudo ./java.bin

hit q to get past the terms agreement
type yes to install

java -version
if it doesnt come back with 1.5.0 you need to make a symbolic link

go into /usr/bin you will see a file named java.. rename it to java2

go into the /usr/bin folder with terminal


ln -s /usr/java/(java folder name)/bin/java  
the java folder name in /usr/java is probibly jre1.5.0_06

so

ls -s /usr/java/jre1.5.0_06/bin/java

do java -version again and it should be 1.5.0 this time

---

### Post by nanotube on 2006-05-01
you can find java installation instructions if you follow the link in my sig and go to the Install Sun Java section.
(you can also find a sun java .deb file in there that you can just install with dpkg -i, and then update alternatives, as per instructions).
alternatively, you can add the seveas repository to your sources.list, and you will be able to install sun java through synaptic. (to find the seveas repository, just search google for it.)

---

