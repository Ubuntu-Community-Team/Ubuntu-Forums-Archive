---
title: "Macbook 2,1 Maverick iSight"
date: 2010-10-30
forum: Apple Hardware Users
---

### Post by idealistic on 2010-10-30
Hi,

I'm new to Linux, and I tried to use my iSight camera (especially for skype).
It didn't look so complicated and I saw many posts about that so I decided to do it myself, but I can't get it to work.

I got the AppleUSBVideoSupport file, but when i type ift-extract AppleUSBVideoSUpport in the terminal (using Guake), it tells me : Option -a is mandatory see --help

what does that mean ?

DOes anybody have the same problem ?

THanks,

THeo

---

### Post by B Pearce on 2010-10-30
Hey,

I have the same model macbook (2,1).  This is how I got my macbook isight working.

0. Open Ubuntu Software Centre and click on Edit -> Software Sources -> Other Software -> Add..

paste in

```
 deb [http://ppa.launchpad.net/mactel-support/ppa/ubuntu](http://ppa.launchpad.net/mactel-support/ppa/ubuntu) maverick main 
```

1. Mount your Macintosh HD in linux by clicking on it in nautilus.

2. Navigate to /System/Library/Extensions/IOUSBFamily.kext/Contents/Plugins/AppleUSBVideoSupport.kext/Contents/MacOS

3.  Copy the file AppleUSBVideoSupport in this folder to your home directory (/home/**YOU**)  [TIP: this file is a java class file that is roughly 85kb as of 10.6]

4.  Type in the terminal 

```
sudo apt-get install isight-firmware-tools
```5. a frame-buffer menu will appear, type in the box /home/**YOU**/AppleUSBVideoSupport

6.  The isight-firmware-tool will extract the relevant info automatically.

7. Reboot for good measure, and your done.


[B]Endnote:  Upon reboot you may see the message "isight-firmware-tools failed to blah blah blah"
this is irrelevant, everything works fine.

Furthermore, I have tested this on iMac 8,1.  isight-firmware-tools does not work.

[/B]all the best,

B Pearce

---

### Post by idealistic on 2010-10-31
Hi, thanks for your answer,

I didnt keep the macos X partition so I did it the other way and it finally worked.

Everything looks perfect, it works on cheese and on Ekiga fine, and on skype it works in the test section perfectly, it detects the isight and tells me its allright but when i skype with a friend, he cannot see my video even though it appears on my screen ...

Does anybody have any idea about that ?

thanks

---

### Post by B Pearce on 2010-10-31
Hey,

I have installed skype and I don't have any problems.

I would use the method above, you don't need Mac OS partition, you just need the file, which you have.

The problem probably stems from the ApI not having access to the required kernel module, which the above method fixes.

All the best,

Brad.

---

### Post by leviathan1 on 2010-11-09
hi, 

i just installed ubuntu 10.10, now i'm trying to set it up properly.
this thread fits perfectly to my system and my problem.

i did exactly the steps B Pearce explained (inclusively rebooting), but i had no success seeing my face..

who can help? what could i have done wrong?

best wishes, levi

---

