---
title: "Partition Question for future Ubuntu user"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by dannyj on 2007-01-25
I've been very curious about Ubuntu so I got my old notebook out of the closet, wiped out XP and installed Edgy on it. Very cool. I'm getting more and more impressed with Ubuntu (the product and the concept) and looking forward to the April release of Feisty Fawn. I've decided to install the upcoming version of Ubuntu on my current notebook. My current notebook has a "60" gig hard drive. 17.5 Gb are used and 38.3 are free - yes, I now that doesn't add to 60 but that's what my local disk property says. I'd like to dual boot with XP because I need Macromedia Studio 8 for my work.

Question: What would be the best partition setup for my XP and (future) Ubuntu system?

--by the way, the reason I can't install Edgy on my current system is because it stalls on the partitioning step of install. I've read that bug will be fixed in feisty.

---

### Post by taurus on 2007-01-25
First, defrag the heck out of your XP (three times for luck) filesystem.  Then, use gparted on the LiveCD to resize your harddrive, leaving some space at the end of the harddrive to install Ubuntu.  And when you get to the partition part, tell the installer to use that empty space and just sit back for about 20 minutes or so.  Then, you would have Ubuntu, dualbooting with XP.

---

### Post by dannyj on 2007-01-25
Interesting and thank you for your helpful reply. What about the partition sizing in my initial question? what would you recommend?

---

### Post by taurus on 2007-01-25
20 GB should be plenty for Ubuntu unless you plan to install and download a bunch of stuff.

---

### Post by Sef on 2007-01-25
> 20 GB should be plenty for Ubuntu unless you plan to install and download a bunch of stuff.

20 GB is fine.  I have an older computer with a 20 GB hard drive, and it works well.  Of course I don't download a whole lot either.

---

### Post by hscottyh on 2007-01-25
Once you get ubuntu up.... I'm sure you'll end up running a virtual machine instead of dual booting. Let me say vmware-player is better than sliced bread. That is, if you do have that one program or two you can't do without. 

It's so great not to have to reboot. I have a couple of Windows programs I have to run 3 or 4 times a year. Thank God I don't have to reboot for it. :guitar:

---

### Post by dannyj on 2007-01-25
hscottyh,

Vmware-player!? I'm interested! Where do I find information about this software? Is it like the Wine program?

---

### Post by seshomaru samma on 2007-01-26
Read[ this ]("http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware")

---

### Post by xhaan on 2007-01-26
> **taurus said:**
> First, defrag the heck out of your XP (three times for luck) filesystem.  Then, use gparted on the LiveCD to resize your harddrive, leaving some space at the end of the harddrive to install Ubuntu.  And when you get to the partition part, tell the installer to use that empty space and just sit back for about 20 minutes or so.  Then, you would have Ubuntu, dualbooting with XP.

I just wanted to reiterate about defrag.
I just recently resized my XP partition again to add in another one for Edgy to go onto and it took FIVE defrags, two of those in offline mode, just to get some "unmovable" files off the back of the partition.

So just make sure that nothing is still hanging around in the space you're going to be getting rid of... after you defrag, check again to make sure it was effective enough.

---

### Post by hyper_ch on 2007-01-26
Before you start resizing your windows partition **MAKE BACKUPS!!!!**

Although in 99.999999% of the cases you won't have any problems but if you have a problem upon resizing then you may loose all your data... (in the end one never knows what's going to happen if you do something on your computer...)

Wine will try to run windows appz directly in linux
VmWare is a virtualization product, this means it will create a second, virtual windows pc within your ubuntu install... since this is then windows, you can run all windows appz in VmWare (however 3d isn't supported [yet])

---

### Post by dannyj on 2007-01-26
Thank you all for your great responses! One of the things that gets me excited about Ubuntu (Linux) is the massive community and how extremely eager everyone is to help.

---

