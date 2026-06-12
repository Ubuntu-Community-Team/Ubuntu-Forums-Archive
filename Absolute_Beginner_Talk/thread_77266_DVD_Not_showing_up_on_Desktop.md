---
title: "DVD Not showing up on Desktop"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by Cud on 2005-10-16
Hi,
I have a Philips DVD burner, running hoary, and I can play DVDs usin VLC, and burn, but when I want to FIND a data DVD I cant locate it anywhere. Not in "places" or using a file browser. Probably Im missing something really obvious.....
 Any Ideas?
Thanks

---

### Post by Lord Illidan on 2005-10-16
Have you checked in /media ?

It should show up on Desktop...though..

Can you give us your /etc/fstab file?

---

### Post by Cud on 2005-10-16
Here's the content of /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I thought maybe adding
/dev/hdd	/media/cdrecorder udf,iso9660  ro,user,noauto  0     0
would help

cdrecorder is a mount point (I think) which shows up in /media. 
Would that help?

Also as additional info, the DVD burner shows up in the Device manager.

Thanks very very much.

---

### Post by Cud on 2005-10-16
Oops I forgot
when I 
ls -l /dev/dvd
I get
lrwxrwxrwx  1 root root 3 2005-10-15 11:03 /dev/dvd -> hdd

---

### Post by Cud on 2005-10-16
O.K
so now I did the following
sudo mkdir /media/dvd
sudo ln -s /dev/hdd /dev/dvd
I got the message
"ln: `/dev/dvd': File exists"

Then I went ahead and edited /etc/fstab and added the following line:

/dev/hdd        /media/dvd      udf,iso9660 ro,user,noauto  0       0

Now when I put DVDs in the drive I get a "Blank cd-r Disk" Icon.
I can now find the DVD player in "places" but it tells me that the DVD in the DVD   burner is blank. I tried a couple of DVDs just to be sure.
VLC still plays the DVDs.
Thanks again

---

### Post by Cud on 2005-10-16
Just a note to say that it worked!!!
All I had to do was reboot.

---

