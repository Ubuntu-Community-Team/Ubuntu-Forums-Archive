---
title: "Ubuntu on MBP Install Hangs"
date: 2008-02-08
forum: Apple Intel Users
---

### Post by jhinz03 on 2008-02-08
I am trying to install the latest version of Ubuntu onto my MacBoook Pro but the install keeps hanging.  I click on Start or Install Ubuntu and then goes to a black screen with generic text that does really say anything useful.  From there it just sits indefinitely. Ive checked the disk to make sure it burned properly and check to make sure the DL went properly and everything is good. I installed rEFIt but nothing seems to work.  I cant even get it to come up Live.  Im about to give up. The laptop was purchased in September and has the Core2 Duo T7500 with 4GB of memory and I believe it is using the 965 Chipset. The exact message I get is "Running Local Boot Scripts (/etc/rm.local)"  After that, it just sits doing nothing indefinitely.

---

### Post by cyberdork33 on 2008-02-08
[https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)

---

### Post by jhinz03 on 2008-02-08
I greatly appreciate the suggestion on the link but the correct procedure is not the issue that Im having.  I cant even get it to boot into the Live.  It just hangs after it get to the "Running Local Boot Scripts..." line.  It says "ok" next to it but then it never does anything after that.  Ive let it sit  for over an hour while I was playing XBOX to see if I just wasnt giving it enough time but still nothing.  I can type lines into the interface and it gives me a cursor but thats all.  When I hit the power button, it shows lines about ending the scripts and then just ejects the disk and goes to a black screen and just sits there until I hold the power button in and power off.


Also weird, if I dont reinsert the CD once it ejects, I cant power off without removing the battery and power cable.  I dont know if that is any more relevant info but maybe someone knows something that I dont.

---

### Post by cyberdork33 on 2008-02-08
apparently someone has changed the wiki. 

I believe you have a Santa Rosa Macbook Pro, and the LiveCD has always had issues booting on that machine. I don't know the proper procedure to get it working. Try booting with safe graphics mode. or try the alternate install CD.

---

### Post by jhinz03 on 2008-02-12
Thanks for the help! Booting in Safe Graphics Mode worked great and I got it installed on my external.  Just a couple of quick questions.  If I downloaded the amd64 image.....it automatically installs it as the 64-bit version, correct?  Im pretty sure but it didnt ask and I wanted to verify before download the 64 bit clients for BOINC.  Also, I have been having the same GRUB Hard Drive Error mentioned in several other posts.  I didnt see any answers there but the last post on that thread was over 1 year ago and I was wondering if anyone has gotten it working yet but maybe this is better posted over there.

---

### Post by cyberdork33 on 2008-02-12
> **jhinz03 said:**
> Thanks for the help! Booting in Safe Graphics Mode worked great and I got it installed on my external.  Just a couple of quick questions.  If I downloaded the amd64 image.....it automatically installs it as the 64-bit version, correct?  Im pretty sure but it didnt ask and I wanted to verify before download the 64 bit clients for BOINC.  Also, I have been having the same GRUB Hard Drive Error mentioned in several other posts.  I didnt see any answers there but the last post on that thread was over 1 year ago and I was wondering if anyone has gotten it working yet but maybe this is better posted over there.
yes. You can use the following command to check the kernel version you have
```
uname -a
```
It should say x86_64 in there somewhere.
I idk exactly what error you are talking about. How did you boot into your system if grub is having errors?

---

