---
title: "Using partitions for installing"
date: 2014-03-21
forum: Apple Hardware Users
---

### Post by yonster on 2014-03-21
I'm in the process of installing lubuntu 13.10 on an old Mac-mini.  Since the newest Ubuntu version 14.04 will soon be coming out, and will have much longer support, I was previously recommended to select the 'Something else' option, then "manually partition the drive into a root (boot flag/) partition and a seperate /home partition (and a swap)."  Another person mentioned using /tmp, /home, and /boot partitions.  Both agreed that this makes reinstalling  much easier and efficient.  At the time these suggestions were given, I wasn't ready to perform the installation, and now am. 

So far I've selected the 'Something else' screen, but not sure _how_ or _where_ to enter these suggested partitions. Should I select the 'New Partition table' and enter these partitions with commas, or on seperate lines??

---

### Post by Laiquendi on 2014-03-21
This question is answered in a graphical way here: [http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

### Post by yonster on 2014-03-21
Ok, thanks, I'll check it out.

---

### Post by yonster on 2014-03-21
I've been attempting to follow the suggestions at this link.  The first question that came up is (yes, I'm THAT much of an absolute beginner) how to convert MB into GiBs?  Are GiBs basically 1/10th of the number shown for MBs?  The examples seem to switch back and forth, and that seems to be the ratio, if I understand it properly.  I'd like to be sure of this before I continue, because I don't want to either permanently erase existing files, *or* do this all over again!!

I'm also wondering if anyone has suggestions on how many bytes to use for swap size?  I'm confused because the instructions say "notice that you should set swap size more than you have physical memory in order to use hibernation".  What's confusing is that the free space in the example given is 85899 MB, yet they only set the swap size at 512 MB.  Isn't the 'free space' the amount of physical memory?  If so, aren't the instructions contradicting themselves??

In addition, the picture given for some odd reason leaves out the 'Mount point:' field, so I don't know if something should be entered there or not.  Anyone know and care to share?

---

### Post by yonster on 2014-03-21
Btw, when I say "this link" I'm referring to the link provided by Laiquendi: [www.askubuntu.com/questions/34326...g-installation](www.askubuntu.com/questions/34326...g-installation).

---

### Post by varunendra on 2014-03-21
Assuming you also want to keep you Mac OS, this one is also a "Must Read" for you : [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:_Mac_OSX_and_Ubuntu](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:_Mac_OSX_and_Ubuntu)

---

### Post by yonster on 2014-03-21
Thanx V, I'll check that out.

---

### Post by tiffany3 on 2014-03-22
Here's a link to my post. It sounds like we had the same issues regarding understanding partitioning. The video linked in my post was the best one I could find. If you partition your drive exactly as he has it, you will get Ubuntu to work. 

[http://ubuntuforums.org/showthread.php?t=2210567](http://ubuntuforums.org/showthread.php?t=2210567)


here's a computer data conversion link: [http://www.onlineconversion.com/computer_base2.htm](http://www.onlineconversion.com/computer_base2.htm)

I hope this helps!

---

