---
title: "Problems with dvdrw/cdrom and ubuntu 6.06"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by bobbycheetah on 2006-08-15
When I put in an audio or data cd, an icon should appear on my desktop.  I understand this as Ubuntu's way of automatically "mounting" the disc.  My previous version of Ubuntu (just before 6.06) worked fine.  With a data disc, I have to go to System -> Administration -> Disks which brings me to Disks Manager.  On left, I click on CDROM. On right, under properties tab my dvdrw/cdrom device is listed (Optoritedev rw dd0203).  Type: CD-ROM, Device:/dev/hdc,  Speed: Not Avail,  Status: Data Disc Inserted.  Under the Data CD-ROM tab:  Access Path /media/cdrom0,  Size: Not Avail,  Status: Inaccessible.  There is a button labeled "Enable".  When I click that, the cd data disc size is shown, and a button to "browse" is shown.  At this point, I can look at the contents of the cdrom.  If I push the physical eject button on my dvdrw/cdrom - nothing happens.  I have to click the "disable" button for that to work.   Now for the audio cd symptoms:  Properties tab: Type:CD-ROM, device /dev/hdc,  Speed:not avail,  Status:Audio Disc inserted.  Audio CD-ROM tab: Audio CD Information. Number of Songs:8  Duration:38:46. There is a button to "Play". When I click on this, nothing happens, no activity on the dvdrw/cdrom.  I know my sound works because mp3's will play.  Is there anything I can do, besides re-install?  Like I said before, my previous version of Ubuntu was fine. Sorry this is so long winded.  Just wanted to be thorough.

---

### Post by skale on 2006-08-15
Don't worry, there's no problem at all. When you click "enable", you are *mounting* the cdrom drive, basically hooking the contents of the drive to a folder, usually /media/cdrom. When you click "disable" you are *unmounting* it. You cannot eject a mounted drive, you have to unmount it first. Windows does everything automatically, so you don't have to think about (one of the nicer features, typing "sudo mount -t vfat /dev/fd0 /media/floppy" just to read the damn floppy, then typing "sudo umount /media/floppy" so the computer does not confuse itself can be fairly consuming). Linux, on the other hand, does not mount everything by default, although Ubuntu does. If you want it to mount automatically at bootup, go here:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by bobbycheetah on 2006-08-15
Thanks for your reply.  I understand about the mount/unmount part, but my point is that my previous version of Ubuntu never had this problem. I never had to mount/unmount via the command line.  I would insert an audio or data cd, and an icon would appear on my desktop - (indicating that Ubuntu had "mounted" it) and I would be able to either play the cd with a player, or browse the data cd.  I never did anything special to make this happen.  Now, after upgrading to Ubunto 6.06, I can't play an audio cd. Thanks again.

---

### Post by bobbycheetah on 2006-08-18
I finally just re-installed. Problem solved. Now, on to other problems.

---

