---
title: "DVD Problem with Xine"
date: 2005-07-26
forum: Absolute Beginner Talk
---

### Post by Weta on 2005-07-26
Hello

Sorry - I have tried to apply previous advice on Ubuntu Forums about Xine, but when we attempt to play a DVD we still get two error messages: “There is no input plugin available to handle 'dvd:/'.  Maybe MRL syntax is wrong or file stream source doesn't exist.” and “The source can't be read.  Maybe you don't have enough rights for this, or source doesn't contain data (e.g. not disc in drive). (/dev/dvd)”

Our system details are:
1.  libdvdcss2 is installed
2.  We have a DVD/CD R/RW (and one floppy drive)
3.  The DVD is under the IDE block.device as “/dev/hda, with three “Volumes” under it (hda1, hda2 and hda5)
4.  There are no “dvd” folders listed in our /dev folder
5.  The /dev folder contains lots of “x-special/device-block” files, including four files labelled “hda, hda1, hda2, and hda5”.

An xine-check advises:
1.  no xine-config found
2.  There are no input [and other] plugins.....  You should probably reinstall xine-lib...
3.You don't have a /dev/cdrom device.

As per previous advice, I have tried the command “sudo ln -sf /dev/hda /dev/dvd” followed by “sudo hdparm -d 1 $DVD_DEVICE”.  I also tried reinstalling Xine, but this process aborted installing gstreamer0.8-lame liblame0 - after asking me whether or not to continue (to use additional disk space).  

I am still new to Linux, but any advice welcome about what I should do next.  Thank you.

---

### Post by heimo on 2005-07-26
Are you sure it's hda? Is it primary master / "first" ide device on the first controller? Then it's hda, but those hda1 hda2 hda5 suggests to me that it's a hard disk and your dvd drive is probably hdb (slave on primary contoller) hdc (master on second controller) or hdd (slave on second controller). Try removing the symbolic link you created (you did that with ln) - use ```
sudo rm [filename]
``` and create a new one with valid device.
EDIT: Uh, I hate when I do that. [filename] should be /dev/dvd

You try mounting the dvd at first to find which device is correct. Put a cd or dvd in, and try
 ```
cd
mkdir mntdvd
sudo mount /dev/hdb mntdvd
ls -al mntdvd
sudo umount mntdvd

``` 
repeat for hdc and hdd if neccessary. Check /etc/fstab, you should probably have a line with */dev/dvd /media/dvd *or something similar in it. If xine still doesn't work, try mounting the dvd first and then starting xine. Actually, if this works, I guess, by default, totem should start automaticly to play that dvd.

Post your findings - others will pop up and give better instructions.

---

### Post by Weta on 2005-07-26
Thank you.  The device is listed under "IDE Device (master)", which itself is under "IDE Host Controller".  

I tried removing the symbolic link, which resulted in the message "cannot remove `/dev/dvd': No such file or directory"  

I do have a /media/cdrom0 folder, but it does not appear linked anywhere.

I'll try mounting the DVD when I get home from work this evening.

Thanks again.

---

### Post by odin on 2005-07-28
I also have a "little" problem with xine.I can play all kind of videos but I dont understand why the sound is off.I checked the volume and everything is ok but I dont hear anything  ](*,)  any idea?

thank's in advance  :grin:

---

### Post by heimo on 2005-07-28
[QUOTE=odin]I also have a "little" problem with xine.I can play all kind of videos but I dont understand why the sound is off.I checked the volume and everything is ok but I dont hear anything ](*,)  any idea?

thank's in advance  :grin:[/QUOTE]

Is it xine problem? Have you tried playing the same video on totem or vlc or any other player? Does other sounds on Gnome work? There're various threads about sound related problems, but you need to narrow down the possibilitites, check that card works and so on. Lot's of possible reasons for sound not working.

---

### Post by odin on 2005-07-28
sound is working in gnome(when log in and every time I click somewhre with the mouse)so I guess is a xine problem.I'll try with totem.

---

### Post by Weta on 2005-07-28
Thanks again Heimo

I have now managed to reinstall Xine following the Guide (i.e. Codecs, DVD Playback and Associate Xine).  I thought that I'd do this as a check that this wasn't causing problems.

I wasn't sure what mounting a DVD as you suggested was going to tell me so didn't do this (sorry).  I did however find /etc/fstab, and discovered /media/cdrom0 associated with /dev/hdc.  So it looks like the DVD/CD is hdc - which doesn't appear under the IDE devices.

Is this enough information for you to be able to tell me what folders and symlinks I should have under the /dev and /media directories to get things running again?  For example, do I actually need a /dev/dvd folder (and, if so, how do I create it)?  I have tried to sort this based on multiple threads, but am still confused.  

By the way, xine-check advises that there are no plugins, but I am hoping that this will be resolved when I sort the fodlers and symlinks out.

Thanks

---

### Post by Weta on 2005-07-30
The lack of reference to a DVD drive on the Device Manager, the suggestion that it was probably the hard drive, and the /etc/fstab reference to /dev/hdc led me to wonder whether the DVD was actually connected to main board.  Especially as the PC had been in to the shop for a warranty replacement of a noisy case fan.... Turns out the DVD wasn't connected to the board!  

DVDs and CDs seem to run now... The drive spins fast and loud playing CDs.  I'll have a look for any advice about this, and how to find and remove symlinks that I created but don't need.  Thanks again for the help...

---

### Post by heimo on 2005-07-30
For lowering the speed of CD-rom, you can use 

 ```
sudo hdparm -E 2 /dev/hd?
```
(2x, for device hd?)

---

