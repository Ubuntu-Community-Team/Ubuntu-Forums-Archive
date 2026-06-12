---
title: "Dangerous noob desperate for help!"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by epsulliv on 2007-01-29
Hello...

here is my dilemna...i was a past windows user and got so frustrated i decided to switch to ubuntu after my buddy passed a cd along...have used ubuntu for the past 6 months and have loved every minute of it with a few non issue drawbacks...i ran it as a live cd for a while but i liked it so much i went ahead and installed it in the place of windows on my hard drive...i need to know what i need to do in order to properly install windows back on my computer...i appreciate your time...thanks..


eric

---

### Post by miseljt on 2007-01-29
Personally, I've only been using Ubuntu for a straight couple of weeks, but I think I've decided to stick w/ Virtual Box for my Windows stuff. 

[http://www.ubuntuforums.org/showthread.php?t=347157&highlight=virtual+box](http://www.ubuntuforums.org/showthread.php?t=347157&highlight=virtual+box)

It's fairly easy to install and you don't have to reboot if you want to do a dual-boot similar system.

---

### Post by epsulliv on 2007-01-29
i checked it out but to be honest, I am not really sure what it can do for me...i think id prefer to just windows it up for a minute...then ill come crying back to linux...

---

### Post by kvonb on 2007-01-29
Just place your Windows CD in the drive and boot from it, follow the instructions.

It will automatically erase the entire hard disk and install Windows.

---

### Post by pvilleSE on 2007-01-29
If you are installing XP alongside Ubuntu you can install XP on a free partition then boot the live cd and then reinstall grub.  If you are installing Vista see my comment at the bottom.

[INDENT]> sudo grub
grub> root(<harddrive>, <partition>)
grub> setup (<harddrive>)
grub> quit[/INDENT]

<harddrive> is the harddrive you have ubuntu installed on ex: hd0; if you don't know what harddrive, type in the command up to that part and press tab twice.
<partition> is the partition you have ubuntu installed on; if you don't know what partition, type in the command up to that part and press tab twice again  The partition that is of type ext2fs or ext3fs is your partition with linux installed on it if you used the default file system during install.

Then reboot, grub should come up and you should be able to choose to boot Ubuntu.  When I did this mine did not boot so I had to highlight the line for Ubuntu then press 'e' and then edit the line
'root       (hd0,0)' to 'root     (hd0, 2)' since it had the wrong partition set and then I had to edit the next line 
change part 'root=/dev/hda1' to 'root=/dev/hda3' once again it was set to the wrong partition
then I had to push 'b' to boot with the edits, but they are not permanent so I will change them later.

Once you get booted, run 'gksudo gedit /boot/grub/menu.lst' in a terminal

Then scroll to the bottom of the file and add the following
[INDENT]title   Microsoft XP
root    (<harddrive>, <partition>)
makeactive
chainloader +1[/INDENT]

Then if you had to edit the grub file to be able to boot make the same edits here in the file.  Then everything should be working.


If you are installing Vista, that is what I just did.  I had to copy my partition running Ubuntu to an external harddrive then erase the harddrive and install Vista, then copy my Ubuntu partition back and then redo grub like mention above.  It would not let me install Vista until I did not have a linux partition on the same harddrive.  What you all need to do depends on the version of Vista, I did this with the business version.

If you need to resize your partition to make room for windows you can download a live cd called GParted livecd(just google for it).  You can also use this live cd to reinstall grub.  It boots gnome and is pretty self explanatory on how to use.

---

