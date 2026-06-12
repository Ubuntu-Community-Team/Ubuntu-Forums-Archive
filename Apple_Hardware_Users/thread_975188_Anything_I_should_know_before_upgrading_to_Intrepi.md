---
title: "Anything I should know before upgrading to Intrepid ?"
date: 2008-11-08
forum: Apple Hardware Users
---

### Post by Zaff on 2008-11-08
Pretty much my question is in the title.
I have a macbook 2nd Gen white (not the Santa Rosa). Is there anything I should be aware of before upgrading.
Thanks.

---

### Post by cyberdork33 on 2008-11-08
> **Zaff said:**
> Pretty much my question is in the title.
I have a macbook 2nd Gen white (not the Santa Rosa). Is there anything I should be aware of before upgrading.
Thanks.
touchpad configuration is a bit different. There are numerous current threads about this.

---

### Post by Kevbert on 2008-11-08
If your macbook has a floppy disk drive it probably won't work (bug still to be fixed).

---

### Post by Henry Higgins on 2008-11-08
> **Kevbert said:**
> If your macbook has a floppy disk drive it probably won't work (bug still to be fixed).

?

Macs haven't had floppy drives since 1999.

---

### Post by cyberdork33 on 2008-11-08
> **Henry Higgins said:**
> ?

Macs haven't had floppy drives since 1999.
and no MacBook ever has...

---

### Post by Poyntz on 2008-11-08
I don't know how this would affect macbooks but if you had a Windows PC I'd be suggesting you learn how to handle graphic drivers using shell before attempting to upgrade as many (including myself) have experianced graphic driver issues when upgrading.

---

### Post by hwertz on 2008-11-09
When I did an Hardy->Intrepid update a while ago:
     1) Default kernel doesn't support SMP, for a dual core G4 it saw 1 core.  I think the multiprocessor kernel is simply a seperate package now.

     2) My system started printing blank pages a while back.  This is REALLY getting to me, but I don't know what's wrong.  I'm using a different computer to print for now.  I'm assuming this was an upgrade problem, and printing "should" work for you.

---

### Post by bbarabas on 2008-11-11
Hi, I have an iBook G4 and trying to upgrade from 8.04 to 8.10. I get the following error message (using the 'normal' Synaptic): 
[http://ports.ubuntu.com/ubuntu-ports/dists/intrepid/Release](http://ports.ubuntu.com/ubuntu-ports/dists/intrepid/Release)  Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)
Am I doing something wrong? Thx.

---

### Post by mkvnmtr on 2008-11-11
bbarbas you should probably start another thread to get help with your problem. I have had the same problem on my Ibook G4 and also couldn't get a fresh install to work. I just haven't had a couple of days to start a thread and try to get it working. I am happy with 8.04 and am hearing al lot of problems with 8.10. I am thinking about waiting a couple of months before trying an upgrade. If you start a thread and have some success I will try to upgrade also.

---

### Post by ubuntubrian on 2008-11-11
I am just finishing up upgrading my G4 TiBook to 8.10 and did my G3 PowerBook a week ago. The G3 was from a clean install of Hardy and the G4 has been upgraded since Hoary, 4.10.
The upgrade on the G3 worked fine with updatemanager but that was a week ago. On the G4 I got the same error:
> [http://ports.ubuntu.com/ubuntu-ports...trepid/Release](http://ports.ubuntu.com/ubuntu-ports...trepid/Release) Unable to find expected entry partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)
this is due to the fact that it is a ported release and this should be fixed soon.
I couldn't wait so I edited my /etc/apt/sources.list file with gedit:
```
sudo gedit /etc/apt/sources.list
```
and using find and replace I changed all hardy to intrepid. I then saved the file.
Then in a terminal I did
```
sudo apt-get update
sudo apt-get dist-upgrade
```
this took many hours of downloading and installing and at the end I had quite a few packages fail so I just kept updating and upgrading in the terminal.
I then went into Synaptic and upgraded everything that I could, repeatedly until there were only 3 failed packages, none important.
I then rebooted and I have a working Intrepid!
Now, there are some issues. KDE stuff will not upgrade but I don't really care too much as I run Gnome except for K3b-indispensable. Also am having trouble with firefox crashing on swf files Oddly not a problem on the G3 at all and gnash plugin sort of plays youtube videos) and the other gecko browsers Epiphany and Galeon crash with segfaults without even starting up.
Lots of packages were removed and there are some weird dependency issues but perhaps they'll get worked out. 
On the plus side, audio etc work out of the box and no messy configuring or detective work. Totem plays youtube and  BBc feeds-what I really wanted! Hardy would not except for a brief period but some updates killed that.
still exploring Intrepid but so far so good!

---

### Post by mkvnmtr on 2008-11-11
Thank you Ubuntubrian. Your experience tells me I need to wait. I need to use 2 or 3 browsers at once and if their crashing I better wait.

---

### Post by bbarabas on 2008-11-19
I managed to upgrade. In the repositories menu I left checked only main and universe and it worked. But I am not happy with the new version, the system is slower now plus programs/functions are not working properly any more. 

The most annoying problem is that I cannot change network configuration now. The worst part is that it does not require the sysadmin password. Any clue?

---

