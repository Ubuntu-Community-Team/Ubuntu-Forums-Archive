---
title: "rolling back upgrade by using acronix True Image"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Wilbur Kelly on 2008-02-24
Because I was having several problems with the upgrade to 7.10 (see earlier post about 6.10 to 7.04 to 7.10), I decided to try to go back to an earlier install. Since I had gone from 6.11 to 7.04 to 7.10 the only way I knew to do that was to use a acronis TrueImage restore of 6.11. I think I tried to install from my backup of the 6.11 to the ext3 partition it was installed in but when I tried to reboot I got an error message Grub 1.5 error 17. I tried to figure that out but since I have a complicated system I was not able to do so. I have the original SATA drive that came with my HP that has the original install of XPMedia Edition from HP. I have a second IDE disk I installed and it has XP on it (one I have the install disk for since HP didn't see fit to provide one with the machine's version of Media Edition XP) and it also has my troubled 7.10 Ubuntu upgrade on it as a dual boot installation. I have by boot order set to boot from the IDE (second disk) that is double boot.

I have several problems with the upgrade but I finally used True Image from Acronis to restore the ENTIRE IDE drive back to my troubled installation with XP and 7.10 and it booted up without the grub error and I was able to get back to the xp/7.10 dual boot. I know I have grub somewhere (?) but my understanding is that I would have had to know where and how to get to it and once I got there I would have had to know what to change and I couldn't get windows or Linux to open with the Grub error 17 message hanging it up so I restored the disk and it is now back to square 1.

What I want to do is to go back to a True Image of the partition that has 6.11 on it. I have such an image saved and that is what I tried this morning. If I do that again, do I have to restore the ext3 partition which has 6.11 on it as well as the swap file from the same time or can I just restore the image from 6.11 on the ext3 partition?

I am not sure why what I did this morning didn't work, but it's taken all day to get back to 7.10 and I still can't adjust the resolution on my display and I could under 6.11. The printer still doesn't work under 7.10 and it did just fine under 6.11. I think when I upgraded to 7.04 things worked ok but I didn't stay there long enough to test it but just kept updating to 7.10. What I plan is to go to 7.04 once I get 6.11 working again and see if 7.04 works ok regarding printer and resolution. There was a screen on the way from 7.04 to 7.10 that gave me the choice of keeping the old info or going for new and I don't have the name of the screen but suspect that is where I lost things in /etc/X11/xorg.conf . The xorg.conf that I cut and pasted below is showing some failsafe entries that weren't there earlier but I can't even print things out to have in front of me to try to edit xorg.conf since ubuntu 7.10 says that my printer "may not be connected" when it is physically connected at least.

SO: if I restore the 6.11 image do I just have to do it to the partition that holds the ext3 or also restore the swap files saved contemporaneously as well? Is there something about that restore that should have resulted in the grub 17 error? Is there something that I can do to fix the grub 17 error short of reinstalling my entire hard disk to allow me to boot beyond error 17 if it happens again to allow me to get to the 6.11 Ubuntu I am trying to go back to? This is a lot like the groundhog day movie...

I wish I had imaged 7.04 on the way here. It would have made things a lot simpler.

This is copied from an earlier post/thread that was more focused on how to get 7.10 working right. It really has a different focus so I have renamed it and started again.

Thanks for any help.

---

### Post by louieb on 2008-02-24
I use partimage not True image, but I would think it would be the same restore in basic.
Just restore your 6.10 partition image. Should not need to restore swap don't think it would help or hurt.

Then get a [Super Grub Disk ]("http://forjamari.linex.org/projects/supergrub/") and get GRUB working again.  
Good stuff here [IDBS on SuperGrub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

Theres a way to fix grub with the live CD but I've lost the link. Might want to do a forum search.

---

### Post by Jose Catre-Vandis on 2008-02-24
Sounds like you have three problems:

Grub - not picking up the right info about the location of your install

Screen - xorg.conf incorrect settings / metamodes

Printer - drivers

There is no reason why you shouldn't be able to resolve all of these by searching the forums on the respective problems, and when you have fixed them you will feel great!

There is a nice 20 page thread about Error 17 here ```
http://ubuntuforums.org/showthread.php?t=442945
```
and follow the links in "Hermans" signature for more info
FWIW, I tend to rely on grub completely as my bootloader, regardless of the number of disks/installs, and always put it on the first hard disk. This helps me to overcome issues with booting from 2nd hard disks etc etc, as opposed to relying on the bios to point to the booting HDD.

Loads of threads about xorg.conf, just search

Post info about your printer and we can see what needs doing. The printing setup in Gutsy is much better than in previous incarnations

In answer to your partition / restore queries, if you have a separate swap partition on disk, your restored installations should just find it and use it, no need to restore swap. Depending on how Acronis works it should simply recreate the image, along with the file system, but you will need an existing partition to restore it too. When I do this type of thing I generally wipe what is on there and create a new partition for the image to go into.

---

### Post by Wilbur Kelly on 2008-02-24
Thread relabled from: Re: rolling back upgrade by using acronix True Image 

I would like to thank Louieb because I really am a neubie and I don't know about Partimage, yet.  If I try to roll back to 6.10 I will try to just restore the 6.10 image.  I used Acronis True Image because I had it, and had managed to image the whole drive before I tried to restore an earlier image.  At least it did let me get back to a working system again.

I would like to thank Jose because the problems  may not be as big  as they seems.  I have managed to do a lot by just keeping on plugging.  I am sure you are right about feeling great once I get them fixed.

Problem number 1: I may not have been clear. Grub worked fine once I reinstalled the image from 7.10.  I want to understand Grub so I can fix it if I have the problem again but it is now working.  I did read the excellent thread on Grub error 17.  I am not sure where Grub "lives" or how to back up the MBR.  That seems like a good place to start but, as I said, it is not a burning issue if I can get the video display and printer issues fixed.

Problem number 2: Regarding the Screen resolution, I have a nVidia processor, somehow it works in XP without the nvidia driver apparently (I just checked in Device manager and it doen't have a driver, so it is apparently using whatever the installer chose for XP).  It is a GeForce something with an nVidia 6150 card.  Anyway, I had the ability to choses among more resolutions in 6.10 and 6.11 but it working well enough at 800x600 to use until I figure out how to fix it.  So that is not a deal breaker.

Problem number 3 the Printer doesn't work:  I have a HP LaserJet 5 and it comes up with an error message that my "printer may not be connected" but it physically is. Additionally, I can print an Ubuntu grayscale test page just fine, but when I have a file to print => it gives me the error message above.  I really don't have an idea about how to proceed. 

I guess my two questions are:
1) I am at a loss to know how to start with the printer question based on the above.
2) At some point in the initial upgrade path to 7.10 (now restored and working) the Nvidia card seemed to be working as evidenced by a nice splash screen.  I never saw that nice splash screen again.  So I am not sure how to proceed in getting that working again.

I stayed up most of the night reading about Grub and the GrubED script that may or may not wrok for 7.10 but I have decided to let what works work for now (Grub) and work on getting the monitor and the printer working.

I appreciate the help.
Sicerely,
WK

---

