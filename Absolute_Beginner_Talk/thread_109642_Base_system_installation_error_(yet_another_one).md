---
title: "Base system installation error (yet another one)"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by silvero on 2005-12-29
Hi all,

I have just built a new system and one of the things I have wanted to do for a while is give Linux a try, Ubuntu appears to be a very popular distro so I have been trying to install it.  I have a lot of experience with DOS and Windows but absolutely none with Linux.

I have Windows XP installed, and intend to use a GAG loader on floppy because I am too afraid of screwing my MBR given my lack of experience in installing Linux.

My installation problem is the following error:
[I]Base system installation error
The debootstrap program exited with an error (return value 1)
check target/var/log/bootstrap.log for the details[/I]

After pressing CTRL-ALT-F3 (I don't know what this does exactly but i read it on another thread) it shows the following:
[I]tar: ./usr/share/man/man3/Locale ::gettext.3pm.gz :Invalid argument
tar: ./usr/share/man/man3/Locale ::gettext.3pm.gz :Invalid argument[/I]

I have searched and searched and it seems plenty of people have had this problem, but the only actual solution posted was reburning the CDs, and yet even people using the pressed CDs have this problem.  I have no problems with my burner, I have used several types of media and they all have the same result.  I have successfully downloaded the install iso 3 times and checked it for errors using MD5 checker and the integrity checker in the installer.  Interestingly there are two files which are of zero bytes size which always have an MD5 error, but it seems this is well known also.  I find it difficult to believe that precisely the same write error causing an identical install problem could happen over several disks.

I would appreciate any information or suggestions on what I can do next, thanks for your help.

System:
P4 506 2.66GHz
Intel P5RD1-VM
Seagate 120Gb SATA HDD
1Gb Kingston PC-3200 DDR RAM
CD-R/W/DVD-ROM & FDD

---

### Post by Kapre on 2005-12-29
[QUOTE=silvero]Hi all,

I have just built a new system and one of the things I have wanted to do for a while is give Linux a try, Ubuntu appears to be a very popular distro so I have been trying to install it.  I have a lot of experience with DOS and Windows but absolutely none with Linux.

I have Windows XP installed, and intend to use a GAG loader on floppy because I am too afraid of screwing my MBR given my lack of experience in installing Linux.

My installation problem is the following error:
[I]Base system installation error
The debootstrap program exited with an error (return value 1)
check target/var/log/bootstrap.log for the details[/I]

After pressing CTRL-ALT-F3 (I don't know what this does exactly but i read it on another thread) it shows the following:
[I]tar: ./usr/share/man/man3/Locale ::gettext.3pm.gz :Invalid argument
tar: ./usr/share/man/man3/Locale ::gettext.3pm.gz :Invalid argument[/I]

I have searched and searched and it seems plenty of people have had this problem, but the only actual solution posted was reburning the CDs, and yet even people using the pressed CDs have this problem.  I have no problems with my burner, I have used several types of media and they all have the same result.  I have successfully downloaded the install iso 3 times and checked it for errors using MD5 checker and the integrity checker in the installer.  Interestingly there are two files which are of zero bytes size which always have an MD5 error, but it seems this is well known also.  I find it difficult to believe that precisely the same write error causing an identical install problem could happen over several disks.

I would appreciate any information or suggestions on what I can do next, thanks for your help.

System:
P4 506 2.66GHz
Intel P5RD1-VM
Seagate 120Gb SATA HDD
1Gb Kingston PC-3200 DDR RAM
CD-R/W/DVD-ROM & FDD[/QUOTE]

Silvero - I would suggest try out the LiveCD first (you can d/l it too) burn it on the slowest possible speed (4x) and try it out. Then if you like the OS, try d/l the full install and be sure to check the integrity of the d/l. Burn it also on the slow speed (4x). Try it out and post again. 

K

---

### Post by silvero on 2005-12-29
OK I gave the live-cd a try, first time everything went smoothly until it hung on 'starting hotplug system'.  

I had a search around for some answers and then tried again with the onboard sound disabled, this time it went past that point, but then stopped with: 'Failed to start the X server' - it is likely that it is not set up correctly.

Looking over the extra information on-screen it appears to be a problem with my onboard video.  A quick search around reveals that I am not alone in having problems with ATI video, but one answer was to edit the /etc/X11/xorg.conf file and change the driver to VESA.  Presumably once the OS is up and running I then may be able to install a specific ATI driver.  I don't know how I can do this with the live-cd so I would appreciate any help.

Alternatively, if there is a way to install the OS on my HDD then I could edit the file as above and examine the logs etc from Windows which would aid troubleshooting, again any help would be great, thanks!

---

### Post by rikard_grankvist on 2006-01-26
I had the same error because I was trying to install with FAT32 as the file-system on my root partition. Got the same exact error message. I solved it by using EXT3 instead.

---

### Post by bonzodog on 2006-01-26
um, also, you cannot use GAG as a bootloader for ext3 or reiserfs. I have a friend who wanted to use it, but  investigated their site, and ext3 and reiserfs are unsupported as the developer of it is no longer interested. But, yeah, you need to use ext3 or ReiserFS as the default FS for all your linux dirs.

---

### Post by Mustard on 2006-01-26
[QUOTE=silvero]OK I gave the live-cd a try, first time everything went smoothly until it hung on 'starting hotplug system'.  

I had a search around for some answers and then tried again with the onboard sound disabled, this time it went past that point, but then stopped with: 'Failed to start the X server' - it is likely that it is not set up correctly.

Looking over the extra information on-screen it appears to be a problem with my onboard video.  A quick search around reveals that I am not alone in having problems with ATI video, but one answer was to edit the /etc/X11/xorg.conf file and change the driver to VESA.  Presumably once the OS is up and running I then may be able to install a specific ATI driver.  I don't know how I can do this with the live-cd so I would appreciate any help.

Alternatively, if there is a way to install the OS on my HDD then I could edit the file as above and examine the logs etc from Windows which would aid troubleshooting, again any help would be great, thanks![/QUOTE]


I'm not sure how you would do it on a LiveCD either, what type of prompt are you dropped to when it fails?  Is it prompting you for login or do you have a login already and its just asking for a command?

With regards to installing ubuntu without GAG (ie using Grub, the standard boot installer), do you have an XP install disk?  I believe its not that hard to fix the MBR with your XP install disk should things go awry. Its covered in a number of threads in the forum if you feel like reading (and it seems you research all your stuff quite well :) ).

---

