---
title: "Firefox 3 flash plugin help"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by nehc on 2008-02-06
i just installed the firefox 3 but realized that it will not install the flash plugin needed to watch youtube. i have reading through posts but i could not find how to install the plugin or how to uninstall firefox 3 and install the firefox 2. if there is still no fix for this problem, do you know how long will it take to release how to fix this?
nehc

---

### Post by NightwishFan on 2008-02-06
Are you using 32 or 64bit?

---

### Post by syxbit on 2008-02-06
me too
using x64.
regular firefox works, and so does swiftweasel 3.0 .deb

firefox-3.0preb3 just got added to backports, but no flash here! (it copies the profile straight from .mozilla/firefox so it's not a profile issue

any ideas?

---

### Post by nehc on 2008-02-06
gutsy 32bit

---

### Post by lamalex on 2008-02-06
Works fine for me... Did you try the manual installation from adobe?

---

### Post by petersonjacob on 2008-02-06
download the tar.gz from adobe, then open a terminal and cd to the directory of the downloaded file open a terminal and type this:
sh flashplayer-installer
do this in normal user and follow the instructions

---

### Post by nehc on 2008-02-06
ok i downloaded the install_flash_player_9_linux.tar.gz to the desktop. 
can you give me the complete code to install it please? i am new to terminal so i don't know how to do it myself, everything i have done so far was copy and paste codes hehehe.
i got an update from ubuntu with this pluging. It said that it installed successfully but it is not.
thanks

---

### Post by nehc on 2008-02-06
hello i tried 
nehc@nehc-ubuntu:~$ sudo tar -C /opt -jxvf ~/Desktop/install_flash_player_9_linux.tar.gz
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error exit delayed from previous errors

but doesnt work.....

---

### Post by syxbit on 2008-02-06
i'm pretty sure that code won't work for x64, as it's only a 32bit binary.
unlike when you install flashplugin-nonfree, which does an ndiswrapper for x64 (but the flashplugin-nonfree hasn't worked for months!)

---

### Post by petrojn on 2008-02-09
Try this patch [Nspluginwrapper Install Script for Dapper-Gutsy]("http://ubuntuforums.org/showthread.php?t=476924").  Worked for me (using Hardy Heron alpha 4 with Intel x86_64 and Firefox 3).
Installed recommended version of script, selected Gutsy and afterwards did this:
 # cp -p /usr/lib/mozilla/plugins/* /usr/lib/firefox-3.0-3.0b3pre/plugins

 :)

---

### Post by cybertron3000 on 2008-02-09
For solving nearly all video issues, try using this ingenious "Quickstart 6.0" download:

[http://ubuntuforums.org/showthread.php?p=3774207#post3774207](http://ubuntuforums.org/showthread.php?p=3774207#post3774207)

---

### Post by philinux on 2008-02-09
Just used this and it works fine.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)

---

### Post by petersonjacob on 2008-02-18
cd to the desktop, if that is where u downloaded it to, but first extract all files using the x window and right clicking on the file and clicking extract here.  then navigate there using the terminal

should be like

cd /home/(your login name here)/Desktop/(the extracted folder on the desktop)/
then type
sh flashplayer-installer
or 
sh flashplayer_installer
which ever one it is

---

### Post by flickerfly on 2008-02-29
I only had to do 
```
sudo cp -p /usr/lib/mozilla/plugins/* /usr/lib/firefox-3.0-3.0b3pre/plugins
```

No extra software. I'm using 32-bit Gutsy.

---

### Post by forrestcupp on 2008-02-29
> **syxbit said:**
> i'm pretty sure that code won't work for x64, as it's only a 32bit binary.
unlike when you install flashplugin-nonfree, which does an ndiswrapper for x64 (but the flashplugin-nonfree hasn't worked for months!)
if you enable backports and proposed updates, the flashplugin you will get works just fine.

> **flickerfly said:**
> I only had to do 
```
sudo cp -p /usr/lib/mozilla/plugins/* /usr/lib/firefox-3.0-3.0b3pre/plugins
```

No extra software. I'm using 32-bit Gutsy.
I tried that and for some reason it didn't work for me.

If you can get your hands on the very latest version, it works.  I'm using the latest Swiftweasel deb, which is basically FF3 b3 only optimized to be faster, and my flashplugin worked out of the box.

---

