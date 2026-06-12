---
title: "New to Linux and Ubuntu; need help restoring my hard drive."
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by kingbagel on 2007-05-03
Hello all,

I have had nothing short of a nightmare trying to install Ubuntu. I'm brand new to Linux, having used nothing but Windows all my life. I heard about Ubuntu through a friend, and, hungry for an alternative, have been very curious to try it ever since, but have hit hurdle after hurdle along the way. Some quick information about my system:

Windows XP / Service Pack 2
Intel Celeron 2.8GHz Processor
Two 80GB hard drives
1GB of RAM

Not sure what else you'd need to know, but let me know if there is... anyway, I started off with the Live CD. No matter what I would do, Ubuntu absolutely would not run. I would hit "Start or Install Ubuntu," and would then be treated to line after line of code scrolling up my screen, until it eventually locked with some kind of error and I had to hold the power button down to reboot. I tried it again when 7.04 came out, and still had the same results. So I tried using Wubi. I wrestled with it for about four hours today, and after countless problems, Ubuntu installed -- but when I loaded it from the boot menu, I had nearly the exact same problem as I did with the Live CD. Code would scroll up the screen, now sometimes indefinitely for over ten minutes, and wouldn't stop until I manually powered down. Then I had a crazy idea -- Wubi downloaded the Alternate ISO for Ubuntu, and so I figured that would give me different results than the Live CD. I burned it and booted it, went through with the install.

Now, I have two drives: one holds Windows and all of my files, and the other is empty. I installed the empty drive to double my disk space, but later decided to try installing Ubuntu on it. I figured that with a totally clean drive, I couldn't go wrong. Back to the install -- I hit several errors along the way and stupidly let it continue anyway. It partitioned my second hard drive, but I never installed a boot method (because both options gave me errors), and just finalized it anyway. Restarted the computer, and of course, there was no way to boot into this fresh install, and so I went into Windows... and now my drive is completely gone. Windows does not recognize it at all.

The cause is probably basic, obvious fact and I'm totally oblivious to it. I'm clueless when it comes to anything involving hard drives or partitions or file systems. I have a feeling that I fouled things up quite nicely, and so I'd like to -- at the very least -- restore my drive to clean, fresh, empty condition and start new. I don't even know where to start, or if it's possible. Is there anybody that can tell me how to reformat that drive, restore it to Windows-recognizable condition, and get back to the start again? Or, better yet, can somebody lead me through steps to actually get Ubuntu working? I'm sure I left far too details out of my story and it's probably too vague, but I can give more information if necessary. I am desperate for help and totally frustrated with everything, and so any help I can get is extremely appreciated. I thank you very much in advance for all your help...

-Ric

---

### Post by tchoklat on 2007-05-03
Odd as the liveCD installation on a windows dual boot is usually very good. Did you allow the system to automatically partition your HDD for you?

---

### Post by Hmarroqu on 2007-05-03
> **kingbagel said:**
> Hello all,

The cause is probably basic, obvious fact and I'm totally oblivious to it. I'm clueless when it comes to anything involving hard drives or partitions or file systems. I have a feeling that I fouled things up quite nicely, and so I'd like to -- at the very least -- restore my drive to clean, fresh, empty condition and start new. I don't even know where to start, or if it's possible. Is there anybody that can tell me how to reformat that drive, restore it to Windows-recognizable condition, and get back to the start again? Or, better yet, can somebody lead me through steps to actually get Ubuntu working? I'm sure I left far too details out of my story and it's probably too vague, but I can give more information if necessary. I am desperate for help and totally frustrated with everything, and so any help I can get is extremely appreciated. I thank you very much in advance for all your help...

-Ric


As for ur previous errors, im clueless, but i can tell u that to get ur extra harddrive back to windows (blah) u must make it NTFS, if the live CD works for u u can do that thru Gnome Partition editor, found in System-Adminisration-Gn.... 

Can u get the live CD up and runing?, sorry i just skimed thru and didnt really get the jist of all the prior things.

---

### Post by Hmarroqu on 2007-05-03
> **tchoklat said:**
> Odd as the liveCD installation on a windows dual boot is usually very good. Did you allow the system to automatically partition your HDD for you?


Would the fact that he is using two HDD one being the master w/ windoze on it be what would make that a problem?

---

### Post by tchoklat on 2007-05-03
No, the installer will select an area on one of the other HDD and partition it and install Ubuntu

---

### Post by Hmarroqu on 2007-05-03
> **tchoklat said:**
> No, the installer will select an area on one of the other HDD and partition it and install Ubuntu

so when he would boot, the grub from the second hdd, which im guessing is not the primary, will appear as it normally does for a 1hdd dual boot?

---

### Post by louieb on 2007-05-03
Windows does not show your 2nd drive because you have installed Linux on it. And out of the box windows does not know how read the file system used by Linux. 
To prove thats its still there Right click on my computer  Manage>Disk Management. Windows will show the 2nd drive and tell you the partitions on that drive are Healthy and unknown. 
Now to fix that  get [Ext2 IFS For Windows]("http://www.fs-driver.org/index.html") follow the instructions and you will be able to use your 2nd drive from windows.

Now to fix the Dual Boot problem. First have your Windows install disk handy. OR if you don't have one get   [Super Grub Disk]("http://supergrub.forjamari.linex.org/")  get it anyway your going to use it to get your machine to dual boot windows and Linux. 
The installer usually sets up Dual Boot but sometimes it fails. You have a common setup. I use it myself the only difference is I have Linux on the 1st drive and XP on the 2nd.  Follow the instructions  at [Herman on SuperGrub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") and your should have your PC Dual Booting fairly quickly.

---

### Post by kingbagel on 2007-05-03
Thank you all so much for your replies. I'll resume trying to squash the Windows beast tonight when I get home from work. One quick question, though; I saw somebody mention GParted in another thread last night while I was looking for an answer, and so I burned the Live CD just for kicks to see if it would do anything at all toward my cause. However, that live CD didn't work, either. I got a kernel error message, similar to ones I had with the Ubuntu Live CD and during the alternate iso install process. Do I need to install a Linux kernel or something before I can use Ubuntu? Thanks again.

---

