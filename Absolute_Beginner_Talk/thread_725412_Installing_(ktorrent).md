---
title: "Installing (ktorrent)"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by r5gtt2k3 on 2008-03-15
Now, I've typed in the terminal "sudo apt-get install ktorrent-2.2.5-0.pm.1.i586.rpm 

and it gives me Couldn't find package  ktorrent-2.2.5-0.pm.1.i586.rpm
It's sitting right there on my desktop :| I'm not quite sure what i am doing, but im trying to install the latest Ktorrent because the older versions are banned from some trackers i use, Help please :D

---

### Post by r5gtt2k3 on 2008-03-15
I'm doing it wrong :|

But when i "rpm-i" I get the same thing 
error: open of ktorrent-2.2.5-0.pm.1.i586.rpm failed: No such file or directory

---

### Post by kaens on 2008-03-15
.rpm files are meant to be installed on linux distros that are based off of red hat (IIRC). The packages for debian-based systems (like ubuntu) are called .deb files.

Never fear though - you may still be able to install from the .rpm

There's a tool called alien for doing just this:

```

sudo apt-get install alien

...

sudo alien -i  ktorrent-2.2.5-0.pm.1.i586.rpm

```

should do it for you.


If it's on your desktop, and your terminal is in your home directory,  need to do

```


sudo alien -i Desktop/ktorrent-2.2.5-0.pm.1.i586.rpm


```


the command ```
pwd
``` will tell you what directory you're in

---

### Post by hhhhhx on 2008-03-15
use alien to convert it to a deb

---

### Post by r5gtt2k3 on 2008-03-15
Ok i don't think i can use this rpm ****.  even the rpm -u doesnt do anything 

How else can i install/update Ktorrent ? Wish it would be as simple as windows :|

---

### Post by r5gtt2k3 on 2008-03-15
ahhh i didnt know rpm wasn't for Ubuntu, I can get a .Tar.Bz I will try that before the alien thing, see if it's any easier :|

---

### Post by kellemes on 2008-03-15
[enable your backports]("https://help.ubuntu.com/community/UbuntuBackports")
[ktorrent 2.2.5 is there]("http://packages.ubuntu.com/gutsy-backports/ktorrent")..

More info..
[http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources")

---

### Post by sajro on 2008-03-15
Why not just ```
sudo apt-get install ktorrent
``` It's in the repositories because it's part of Kubuntu. Don't forget to load IPBlocker, though!

EDIT: Didn't notice he was in Hardy.

---

### Post by kellemes on 2008-03-15
> **sajro said:**
> Why not just ```
sudo apt-get install ktorrent
``` It's in the repositories because it's part of Kubuntu. Don't forget to load IPBlocker, though!

EDIT: Didn't notice he was in Hardy.

He wants 2.2.5

---

### Post by r5gtt2k3 on 2008-03-15
ahh with the backports you just click "enable" in the update manager ? it's really that simple ? ... ihope it works, I've been looking on the net for ages:|

---

### Post by r5gtt2k3 on 2008-03-15
Wow thank you, It only needed a tick !! 2 hour googling and it was just ticking abox, thanks alot dude :D

---

### Post by r5gtt2k3 on 2008-03-15
yeh i tried sudo apt-get install sudo apt-get update.. nothing worked, This has though, Thanks again :D

---

