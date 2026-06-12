---
title: "Blue Screen of Death"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by landsg on 2006-04-22
Hello All:

I have a desktop box with XP/Debian dual boot setup.  Today I installed Ubuntu, replacing the old Debian Linux OS.  Ubuntu boots up just fine, a clean install and everything is recognized.  Awesome!!  But you know it was just too easy...

When I attempt to boot back to XP, it gets just past the initial Windows screen and then I get a brief "blue screen of death" flash before the whole system reboots on its own.

Assuming my MBR is screwed up.  Any ideas on how I can repair?

---

### Post by stoeptegel on 2006-04-22
The bootcode is in the first 446 bytes of the MBR, and that seems to be fine seeing that you can boot both windows and ubuntu.

The next 66 bytes is for the partition table, and that also should be fine unless you've done some strange partitioning. If it's not ok you will lose data fast. But since it's just a windows BSOD it's probably nothing special.

In my windows time, i came to the finding that BSOD's on bootup could be solved most of the time by deleting the pagefile.

---

### Post by landsg on 2006-04-22
Thanks for the reply.  How can I delete the pagefile?  Sorry, I am still fairly new to Linux (but am beginning to really like Ubuntu).

---

### Post by stoeptegel on 2006-04-22
[QUOTE=landsg]Thanks for the reply.  How can I delete the pagefile?  Sorry, I am still fairly new to Linux (but am beginning to really like Ubuntu).[/QUOTE]

First try to boot again to look if it was just an unlucky windows failure. If not then i would wipe the pagefile.

You have a windows installation cd? Boot from it and go into the recovery where you can input commands. There you can remove the pagefile.sys file.
 
This pagefile.sys file is locked though, so you have to copy another file over it with 
copy boot.ini pagefile.sys [enter]
then you can delete the pagefile.sys with
del pagefile.sys [enter]

After this you do
exit [enter]
remove the cd and cross your fingers for the boot.

I can't guarantee this would solve the issue, but for me it has solved all (and that are a lot) of my BSOD problems i had on bootup of windows.

---

### Post by landsg on 2006-04-22
OK, thanks.  I will give it a shot and let you know what happens.

---

### Post by landsg on 2006-04-22
I tried Windows recovery mode, but it is asking for an Admin password.  I am the only user, but it doesn't take any password that I have used in the recent past.

Can I reinstall XP over the top of the old install?  Hoping that Windows will just reinstall itself without damaging data or apps.  However, I do have everything backed up on a USB hard drive so I can reinstall if I have to.  Yuck....

---

### Post by Stew2 on 2006-04-22
[QUOTE=landsg]I tried Windows recovery mode, but it is asking for an Admin password.  I am the only user, but it doesn't take any password that I have used in the recent past.

Can I reinstall XP over the top of the old install?  Hoping that Windows will just reinstall itself without damaging data or apps.  However, I do have everything backed up on a USB hard drive so I can reinstall if I have to.  Yuck....[/QUOTE]

Hello, unless you set up a specific administrator password when you set up XP the field can usually be left blank. Try just hitting enter when it asks for the admin password. Hope this helps. :) 

Regards,
Stew

---

### Post by stoeptegel on 2006-04-22
If it's the home version op xp the password might be blank.

If you really can't have access, reinstalling windows could work yes. 
Downside is not only reinstalling and using backups, but the windows installation will also overwrite the MBR part with the bootcode. So you end up with windows only to boot from. 

If you want the road of reinstalling windows, it would personally wipe the whole disk with partitions on it. While doing this you can make a backup of the MBR after installing windows and (k/x)ubuntu, knowing this is a good mbr backup for latter needs.

I feel sorry you might have to take this road, though i don't a relationship in a BSOD in windows and a fresh ubuntu installtion. So it would probably happend anyways.

Take care and if you have questions, don't hestitate...

---

### Post by landsg on 2006-04-22
I managed to get into the the prompt in recovery mode and tried to copy the boot.ini file and then delete the pagefile.sys.  However, end result in the same.  BSOD.

---

### Post by jpfreely on 2006-04-22
If it gets only just past the boot screen it may be that Windows can't mount the NTFS partition. I had this problem once. In recovery console make sure you do a CHKDSK /P.

---

### Post by stoeptegel on 2006-04-22
Knowing that you have a backup, i would wipe the disk & partition table with fdisk (or based on it), and install windows + ubuntu after that.

You can however do a online search on the BSOD error code, but it could give you more a headache than removing everything and go from a clean system.

So... if you format the windows partition and you haven't got any other partitions with data on the disk you'd like to keep, i would advise you to destroy the partition table. 
(i don't think your problem was in this area though, but just to make sure can't do any harm and ensures you there's not an old problem walking with you)

EDIT
Oh, yeah good idea jpfreely. Do a checkdisk first and see where it gets you. :)

---

### Post by landsg on 2006-04-22
I tried the CHKDSK /P, and it found some errors.  However, tried to reboot again and I still see the BSOD.   I can't see the BSOD long enough to get the error code.   

I have a separate hard drive for Linux, something I did intentionally to try and keep things more simple versus putting two different OS on one drive.   Do I still need to wipe the drive with XP on it?   If it weren't for Quicken, I don't really think I would need XP at all.

---

### Post by landsg on 2006-04-22
Thought of one other thing.  I had Norton Systemworks on XP, with "GoBack" enabled.  After I installed Ubuntu, I noticed the Norton screen flashed up just before the BSOD flashed.  Could Ubuntu have affected Norton in a way that is preventing XP from booting??

---

### Post by stoeptegel on 2006-04-22
[QUOTE=landsg]Could Ubuntu have affected Norton in a way that is preventing XP from booting??[/QUOTE]

No i think not. Ubuntu makes a root and swap partition which where in this case on a different physical disk. The only thing that changed on the disk where windows is located is the MBR. (so the partition table might be screwed up, which shouldn't happen in the first place)

Quicken can be run with "crossover office" emulator under ubuntu though. If you deside to remove windows and put the disk where ubuntu is on as master in the system, then you probably have a issue with a missing grub. 

So you would have to install grub manually in that case.

Peronally i would let the system for what it is and try quicken with crossover office first so you can deside wheither it will work for you or not. Then you can deside to reinstall windows and ubuntu(or only restore grub), or switch disks so the ubuntu disk is on sata channel1 or as master so the system can boot from it + install grub manually.

---

### Post by landsg on 2006-04-23
Is crossover already there in Ubuntu, or do I have to download/install??

---

### Post by 3rdalbum on 2006-04-23
Unfortunately, Crossover Office is a commercial application.

---

### Post by stoeptegel on 2006-04-23
No you have to download and install manually.  

They have a full working 30 day trail version here:
[http://www.codeweavers.com/products/download_trial](http://www.codeweavers.com/products/download_trial)

---

### Post by landsg on 2006-04-23
Downloaded the trial version.  Very nice.  Now I just have to get my Quicken 2005 download application file from my USB hard drive.  For some reason, Ubuntu can't mount the USB drive, although it does see it.  Error message:  "Could not determine filesystem type".

If I can get Quicken installed, then maybe there is hope for me yet!

---

### Post by prismic on 2006-04-23
I am having the exact same problem!  Unfortunately in my case, I was being an idiot and did not back up my data.  I have an older back up about a month old, but I would REALLY like to be able to boot back into Windows and at least get the data out to a back up.  Can anyone help?

---

### Post by landsg on 2006-04-23
[QUOTE=prismic]I am having the exact same problem!  Unfortunately in my case, I was being an idiot and did not back up my data.  I have an older back up about a month old, but I would REALLY like to be able to boot back into Windows and at least get the data out to a back up.  Can anyone help?[/QUOTE]


Well, you have read all the posts on this thread, and I was not able to get back into Windows at all.  I am reinstalling a fresh XP this morning and am planning on putting Ubuntu on right after that.  Then, I am going to install Crossover - it works very well.

Have you tried doing the CHKDSK /P option, along with the other things on this thread?  Hope you have more success than I did.

---

### Post by garner_nc on 2006-04-23
Maybe I'm missing something here but, if you can boot Ubuntu, can you access your WinXP partition? If so you could back-up your files through Ubuntu then re-boot and re-install XP. Then you should be able to copy your files off your backup media to your XP partiton.

All the Best,
Doug White
Garner, NC USA

---

### Post by prismic on 2006-04-23
Argh!  You are right!  I could do that!  It just never occured to me while I was in panick mode last night.  I just tried it was able to offload all of my important stuff onto an external drive.  Thanks for that advice!

Now I just have to figure out what caused it to not boot up, because I do intend to create a dual-boot machine.

---

### Post by Manveru913 on 2006-04-23
This same thing happened to me a while back after installing Linux and setting up a dual boot system. Unfortunetly it *was* quite a long time ago as i dont quite remember exactly what i did to fix it... 
I remember it might have been something with the grub.conf file and how it was set up with regards to windows (i was using an old redhat distro though, so i had to edit the .conf file myself, and ive since installed ubuntu in the same situation and its worked fine on its own). 
I also remember that after it was fixed, it turned out to be a problem solely with windows, which probably means i ended up reinstalling windows and it just worked.
Looks like Im just a little to late anyway, as you have already reinstalled it seems.

---

