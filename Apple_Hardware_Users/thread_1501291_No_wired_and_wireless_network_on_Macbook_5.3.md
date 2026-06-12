---
title: "No wired and wireless network on Macbook 5.3"
date: 2010-06-04
forum: Apple Hardware Users
---

### Post by Di Petrio on 2010-06-04
Hello! I just installed ubuntu 10.4 on my macbook pro 2.8 GHz 4 Gb RAM, and I have a problems with internet. I have no wired and wireless internet.
I installed ndiswrapper and some similar things but failed, nothing is working now.
Please, help me sombody to solve my problem, is there some working drivers?

---

### Post by Bachstelze on 2010-06-04
The wired NIC should work out of the box. For the wireless one you will need ton install the driver either manually or through the restricted drivers manager. See [https://help.ubuntu.com/community/MacBookPro5-3/Lucid](https://help.ubuntu.com/community/MacBookPro5-3/Lucid)

---

### Post by Di Petrio on 2010-06-04
How can I do **sudo apt-get install** without internet??

---

### Post by linuxopjemac on 2010-06-04
I would do a re-installation. Wired should work out of the box.
[http://ubuntuforums.org/showthread.php?t=1493364&highlight=wired+wireless](http://ubuntuforums.org/showthread.php?t=1493364&highlight=wired+wireless)

---

### Post by sushiboy on 2010-06-04
Sadly, I experienced the no internet problem as well.

I installed Ubuntu using Parallels. And after Ubuntu finished downloading the updates and prompted me to restart it, I can no longer browse the internet. My Wifi / router cannot be detected.

---

### Post by amd-64 on 2010-06-06
1. Make sure the following modules are loaded, wl for wifi, forcedeth for wired.

2. Post the output of 
ifconfig
iwconfig

3. Do you have network manager installed?

---

### Post by sha.goyjo on 2010-06-06
Folks, folks, we have about three different problems going on simultaneously, and this thread is going to get very confused if we don't sort them out. 

First off, wired should work out of the box. If it doesn't, reinstall. Something has gone wrong. Make SURE to check your md5sum on both your download AND YOUR CD! That is the most common cause of of bad installs, and doing it will greatly reduce the occurrence of problems like this. That being said, they still do crop up from time to time. So for the broken wired connection, I'd suggest a reinstall.

As for the broken wifi, when you do a reinstall, avoid Jockey (the restricted drivers manager). There is something funky going on with it in regards to those drivers. Unfortunately, I cannot test said funk, because my iBook G4 (which uses said drivers) just walked out the door with my fiancee on a 27 month Peace Corps tour of duty. Regardless, my advice is to use
```

$sudo apt-get install b43-fwcutter

```
instead. It's what jockey is supposed to be doing anyways. 

If you had been running lucid for longer, I would advice a more complicated solution, but since your install is so new, my advice is just simply to reinstall.

---

