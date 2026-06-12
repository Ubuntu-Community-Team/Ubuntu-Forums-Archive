---
title: "Lion and NTFS"
date: 2012-02-29
forum: Apple Hardware Users
---

### Post by Condor Cluster on 2012-02-29
Hi,

I realise this might be the incorrect place to ask this, but I'll try anyway...

I recently tried to get my white Macbook 10.6 to read a usb stick formated in NTFS.
To get Lion to read it, I followed this 'hack' to get NTFS read & write to work > First go to Apple logo on the top  of the corner and clic "about this mac". then select "more info" and  push the button "system report" . Then select the seccion "USB" to see  where the usb hdd. like this:[[IMG]https://discussions.apple.com/servlet/JiveServlet/downloadImage/2-15673982-19335/450-312/Screen+Shot+2011-07-21+at+7.46.03+PM.png[/IMG]]("https://discussions.apple.com/servlet/JiveServlet/showImage/2-15673982-19335/Screen+Shot+2011-07-21+at+7.46.03+PM.png")
we nee the BSD, in this case my usb hdd is disk1s1
 
we open Terminal and we type the following:
 
sudo mkdir /Volumes/usb1
 
it will ask for your password. then we type the following:
 
sudo mount -t ntfs /dev/disk1s1 /Volumes/usb1/
 
and you will see on your desktop the usb hdd mounted. I hope it will help temporary. 



I realise that doing things like this come at a risk, and although it seemed to work (I was able to read & write to usb stick), it seems to have caused problems when trying to use my external 1Tb usb drive (FAT32).

How can I go about 'undoing' this hack I stupidly followed?

Any help much appreciated,

Thanks.

:redface:

---

### Post by wyliecoyoteuk on 2012-02-29
use the umount command to unmount the drive.
Not sure, but that and a reboot should restore the automount on the Mac.

If not you may have to repeat the mount command e.g.:

sudo mount -t vfat /dev/disk1s1 /Volumes/usb1/

more info here:
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by MisterGaribaldi on 2012-02-29
There was a project called MacFUSE which has now been superseded by OSXFUSE. This provides a means to add file system support to Mac OS X. Here are the links for what you need:

GitHub: [OSX FUSE](http://osxfuse.github.com/)
Tuxera: [NTFS-3G](http://www.tuxera.com/mac/tuxerantfs_2010.12-RC.dmg)

---

### Post by MisterGaribaldi on 2012-03-05
Hey, **Condor Cluster**, did you ever get your problem resolved?

---

