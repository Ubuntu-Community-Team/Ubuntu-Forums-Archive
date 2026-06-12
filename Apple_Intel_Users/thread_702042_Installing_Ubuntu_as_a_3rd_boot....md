---
title: "Installing Ubuntu as a 3rd boot..."
date: 2008-02-19
forum: Apple Intel Users
---

### Post by veganjustice on 2008-02-19
Okay, I am confused a bit, and have read other posts, but still not fixing my problem...

I have been sing Ubuntu for a while now, but under Parallels, as well has I have an iMac G3 and an iBook G3 that are both Ubuntu machines...

But on my Intel iMac, I have Mac OS X, and a second boot of Windows XP for some gaming I do. I want to get away from using Parallels/VMWare Fusion for my Linux needs, so I wanted a 3rd boot, which I wanted Ubuntu...
I have rEFIt installed already, and that works fine at the boot menu, but like, when I use Boot Camp Assistant to repartition, to add a 3rd partition, it only gives me the option to restore the actual Mac OS partition. 

Does anyone have any idea what I can do to create another partition, so I can install Ubuntu onto it?

I can partition either my Mac or my Win drive using Disk Utility, but it only gives me the option of 30gb or higher for the Mac one, or just splitting my Windows one in half, neither of which I want. I don't need 30gb dedicated to Ubuntu, but I do need the 20gbs I have for XP, I don't want 10 of that gone. 

Anyone have any ideas?
Thanks!

Jordan

---

### Post by cyberdork33 on 2008-02-19
well you are doing things a bit out of order. I would suggesting making sure you have your windows stuff backed up before doing much. Then you can boot the Ubuntu live cd and start the partition editor. This will shrink whichever partition you want.

---

### Post by veganjustice on 2008-02-19
What am I doing out of order? 
Anyways, so the partition editor from the Ubuntu install cd will let me choose one of the partitions, and size it to what I need? 
I wasn't aware of that...
Hahaha, thanks

---

### Post by cyberdork33 on 2008-02-19
Typically, you would install Windows Last. I would do a bit of research on triple booting as there are difficulties. Windows can only see 3 partitions, Linux needs to boot from one of the first 4 partitions, windows doesn't like having he partitions change after it is installed, etc.

I know that you have an iMac, but the older Macbook Pros are quite similar. Check out the triple boot section of the wiki page:
[https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)

There are some other popular tutorials for triple booting, but there is some out-of-date info in them:
[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)
[http://ubuntuforums.org/showthread.php?t=594298](http://ubuntuforums.org/showthread.php?t=594298)

---

### Post by veganjustice on 2008-02-19
Yeah, I know Windows would like to go last, but unfortunetly, I have had Windows installed for a long time now... 
But I will change the Mac OS X Partition, not the Windows, so you think it will still effect it? I am going to take like 15gigs from the OS X drive, not the Windows. 

And if I just use the partition sizer in Ubuntu, will it know to take free space for the Mac OS X side? So I don't lose any of my OS X install? 

Thanks for the help.

---

### Post by cyberdork33 on 2008-02-19
> **veganjustice said:**
> Yeah, I know Windows would like to go last, but unfortunetly, I have had Windows installed for a long time now... 
But I will change the Mac OS X Partition, not the Windows, so you think it will still effect it? I am going to take like 15gigs from the OS X drive, not the Windows. 

And if I just use the partition sizer in Ubuntu, will it know to take free space for the Mac OS X side? So I don't lose any of my OS X install? 

Thanks for the help.if you start gparted from the Livecd, you will see what it is like, you will know which partition is which. In fact, you can install it on your VM and check it out first; familiarize yourself.

The resizing of the partition is not what matters, it is the partition order. Like I said, feel free to try, but I would backup my game saves in case I royally screwed up my windows install.

---

### Post by jackhe22 on 2008-02-21
Hope this helps!  First Open Disk Utility (Applications-Utilities-Disk Utility) select the HDD from the menu on the left and select Partition from the top menu and click the Plus icon under your two partitions. WARNING: BACK UP YOUR WINDOWS PARTITION BEFORE STARTING ANY OF THIS.

---

### Post by cyberdork33 on 2008-02-21
> **jackhe22 said:**
> Hope this helps!  First Open Disk Utility (Applications-Utilities-Disk Utility) select the HDD from the menu on the left and select Partition from the top menu and click the Plus icon under your two partitions. WARNING: BACK UP YOUR WINDOWS PARTITION BEFORE STARTING ANY OF THIS.That will work, but you have to be using Leopard for that feature, then you will still have to delete that partition and create a new one for Ubuntu.

---

