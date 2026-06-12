---
title: "macromedia flash player"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by sanityscourge on 2006-06-17
how do I get this to work. Being the newb I dunno how to unpack but I assume it means extract. Then what? I've been trying at this for a long time and haven't found something I could understand to install it.

---

### Post by tronica on 2006-06-17
get this tool, its called easyubuntu and it installs and sets up tons of stuff. it will get you going on flash and many other things.

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

---

### Post by xXx 0wn3d xXx on 2006-06-17
Type this in terminal:
> sudo apt-get install flashplugin-nonfree

If that doesn't work, try Automatix.

---

### Post by sanityscourge on 2006-06-17
I tried that and it didn't have the flash player thing there.

Edit to xx owned xx:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree

Aside from that it didn't do anything else.

---

### Post by xXx 0wn3d xXx on 2006-06-17
[QUOTE=sanityscourge]I tried that and it didn't have the flash player thing there.[/QUOTE]
You tried what ? Easy Ubuntu, Automatix, flashplugin, etc. Please be specific. If you don't have flashplugin follow [ this tutorial. ](http://www.psychocats.net/ubuntu/sources.php)

---

### Post by sanityscourge on 2006-06-17
Easy ubuntu I tried and your method.

Gave me junk.

---

### Post by Sef on 2006-06-17
An easier way to open the repositories is this way:

[Easy way to add Universe and multiverse]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

Universe is freeware (open sourced), multiverse is closedware (not open sourced).

Then to download flash:

```
sudo apt-get update

sudo aptitude install flashplugin-nonfree
```

For more info on what you can install, [click here. (Restricted Formats)]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by sanityscourge on 2006-06-17
To Sef:

After adding the repositories and used the sudo apt-get update and then did
sudo aptitude install flashplugin-nonfree it gave me this

sanity@Infector:~$ sudo aptitude install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "flashplugin-nonfree"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by Sef on 2006-06-17
> sanity@Infector:~$ sudo aptitude install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "flashplugin-nonfree"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

It seems like multiverse was not enabled.  That's what has happened to me when it was not enabled.

---

### Post by sanityscourge on 2006-06-17
just go an enable the multiverse howso?

please bear with me :(

---

### Post by Sef on 2006-06-17
> just go an enable the multiverse howso?

Try to enable it again.  Maybe you made a mistake.  I have done it wrong more than once. :lol

> please bear with me 

No problems.  Have been where you are.

---

### Post by learning on 2006-06-18
I think there has been something screwy going on with flash lately.

I had problems earlier and ended up having to download and install. 

See this thread-->

[http://www.ubuntuforums.org/showthread.php?t=198446](http://www.ubuntuforums.org/showthread.php?t=198446)

---

### Post by azc on 2006-06-18
Hello,

This how I installed the Flash Player plug-in for Firefox. (Ubuntu 6.06)

First, visit this page: [http://plugindoc.mozdev.org/linux.html#Flash](http://plugindoc.mozdev.org/linux.html#Flash)

Note the instructions:
> 
1. Download Flash Player 7.0.
2. Decompress it, then copy libflashplayer.so to your Mozilla plugins directory and flashplayer.xpt to your Mozilla components directory.

Download the file: (Click the link: Macromedia Flash Player for x86 Linux)
   Filename: install_flash_player_7_linux.tar.gz

Decompress the file:
   tar -xzvf  install_flash_player_7_linux.tar.gz

login as root:
   sudo -i
   (supply password)

Copy the files mentioned in the instructions to the appropriate directories:
   cp libflashplayer.so /usr/lib/firefox/plugins/
   cp flashplayer.xpt /usr/lib/firefox/components/

Now change to the two mentioned directories, and ensure the file owership and permissions are the same as the rest of the files in those directories. 
cd /usr/lib/firefox/plugins/
cd /usr/lib/firefox/components/

See the man pages for:
chown
chmod
if you wish.

Exit root shell

Restart Firefox
------------------------
Hope this works for you.

---

### Post by cacharreo on 2006-06-18
The easiest way to add plugins like flash, multimedia codecs, etc is to use automatix. It install by you the most things you need.
for most info take a look to:
***[http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405) ***:roll:

---

