---
title: "Removing Ubuntu and/or changing the order of boot."
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by UbieNubie on 2006-08-21
August 21, 2006 5:06pm

I need a little help.  I have an XP Professional Computer with 1 Gig memory.  I’m using XP Pro and Dapper Drake 6.06 LTS. 
 I originally had a 250 Gig drive and updated it to a 500 Gig Seagate.  I used Seagate’s install disk to copy the old drive to the new and changed pins to make the 500 Gig unit my main Hard Drive.  I partitioned the 500 G drive with 3 partitions.  One for linux and one for Sun’s Solaris and the main one for XP Professional.  I am unable to install Solaris, but was able to install Ubuntu.  However, in installing Ubuntu it placed itself in the proper Linux partition without asking and installed a multiple system boot.  The computer now places the following script on screen upon turning on the machine.  If I do nothing it boots to Ubuntu.

Ubuntu, kernel 2.6.15-26-386
Ubuntu, kernel 2.6.15-26-386  (recovery mode)
Ubuntu, kernel 2.6.15-26-386
Ubuntu, kernel 2.6.15-26-386  (recovery mode) 
Ubuntu, kernel 2.6.15-26-386
Ubuntu, kernel 2.6.15-26-386  (recovery mode)
Ubuntu, memtest86+
Other operating systems:
Microsoft Windows XP Professional
Microsoft Windows XP Professional

Originally it had only the first four lines and then it added the 5th and 6th.  It also boots from either the new 500 G drive or the old 250 G drive in XP if I chose.  Everything seems to work properly, but strange things have happened.  I checked the disk with Partition Magic and it says the main partition is ‘BAD’. However, it works fine, but Partition Magic won’t work on it at all.  Windows does not recognize that there is a Ubuntu partition.  It recognizes the Solaris partition simply as another partition, but Ubuntu and it’s swap partition don’t show up.

I would like to remove Ubuntu completely and reinstall it on another computer to continue learning and return the 500G disk to normal.  I cannot find anyway to do so or to get to the boot sector to reduce the lines or order of boot. I now have to ‘Enter’ down 8 times to boot from my 500 G HDD in XP or 9 times to boot in XP on the old 250G disk.

Help Please and Thanks
UbieNubie

---

### Post by Shortgeek on 2006-08-21
If you boot from a LiveCD, you MIGHT be able to repartition, and run some command to reset the MBR, but I don't know the command. Don't do it unless you know about the command.

---

### Post by confused57 on 2006-08-21
Here's a link for uninstalling Ubuntu(repairing mbr):

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

To read Linux partitions in Windows you need:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

In Ubuntu you can open your /boot/grub/menu.lst file to see what the root partitions are for the entries you see in grub:
```
cat /boot/grub/menu.lst
```
The menu.lst is as in list, not first.
If you want to edit your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Here's a dualboot guide(ignore dualboot part) explaining editing your menu.lst:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

