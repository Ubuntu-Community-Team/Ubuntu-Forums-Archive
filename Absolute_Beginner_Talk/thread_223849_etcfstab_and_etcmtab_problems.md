---
title: "/etc/fstab and /etcmtab problems"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by sarum on 2006-07-27
Hi there, When I try to play a CD or DVD I get this message "special device /dev/hdc(hdd) does not exist.
I have searched Google Linux, where there are nearly 16,000 entries under this heading. Which would suggest that its not an uncommon problem. There are some solutions; and warnings about messing with the  /etc/fstab file. But nothing specific to Ubuntu (Breezey in my case).My CD is old and may be faulty; the DVD was new in January, and both used to work. I've recently bought an external modem. But I am always down loading things (I'm an elderly newby to computers), and stay with Ubuntu because of the help available. I hope some body can help me with this one.............Sarum

---

### Post by ciscosurfer on 2006-07-27
Please post your /etc/fstab```
cat /etc/fstab
```

---

### Post by sarum on 2006-07-27
~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  vfat   iocharset=utf8,umask=000  0    0
fawcett@ubuntu:~$

Thanks for you reply..........Sarum

---

### Post by ciscosurfer on 2006-07-27
At first glance, it looks to me like you are trying to dual-boot your system (Ubuntu Linux and Windows (98 perhaps?).  I am troubled by this setup b/c even if this is your intention, I don't believe both systems should be mounted to the same partition (in my experience, they need to be seperate...I apologize in advance if this doesn't make sense)  From the looks of your fstab, however, your cdrom(s) are setup correctly.  Let me do some research and get back to you.

EDIT: the vfat line may be your windows recovery partition (you don't have any read/write/execute permissions set via fstab so that's my best guess with that line).

---

### Post by infoseeker on 2006-07-27
Please post
> sudo fdisk -l
BTW 'l' = small 'L' (just in case) :)

---

### Post by sarum on 2006-07-27
Thanks to both of you for replies.
First Sisco: Yes this was once in a LAN relationship with my other MS computer but is now on its own and so doesn't need anything to do with Millenium Edition. How would I get rid of, is it vfat.
Infoseeker, herewith the results of your request:-

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2341    18804051   83  Linux
/dev/hda2            2342        2434      747022+   5  Extended
/dev/hda5            2342        2434      746991   82  Linux swap / Solaris
Thanks again...Sarum.

---

### Post by sarum on 2006-08-03
Hello again. You may be interested to know that the computer stopped working altogther; just would not start. The geek man in our local shop has 'phoned to say the fault is in the gaming card, which I've never used. He assures me that once that's put right, then all will be well with the dvd and cd.
Thankyou for your replies
Sarum

---

### Post by ciscosurfer on 2006-08-03
You graphics card has nothing to do with your previous problem.  But perhaps you did have a faulty graphics or audio card...then perhaps that's good to fix.  But your geek man is wrong to say that that was the problem you were having (the errors you posted have absolutely nothing to do with either your graphics card nor your audio card).

---

### Post by sarum on 2006-08-04
I also was very supprised at the geek's diagnosis. I'm old, and new to computers and even newer to Linux, so I didn't question him on the matter.But the computer has been returned; and upgraded to Dapper Drake and is working perfectly - minus the grafic card. A problem with screen resolution I shall try to resolve through FAQ on this excellent site. I was charged for 2 hour's work, including collection and return.
Once again thanks for your interest in this rather strange case.
Cheers Sarum.

---

### Post by ciscosurfer on 2006-08-04
Glad to hear everything (almost) is back to normal.  And even though this thread is devoted to your original issue, let's try to hammer-out the graphics/screen resolution problem while we're here anyway: can you describe further what specifically is the graphics issue?

---

### Post by sarum on 2006-08-04
Thanks for your reply, I've actually posted a question last evening after failing to find what I wanted. 'Screen Resolution stuck@ 640x480'is the heading. The problem is that everything on the desktop is large. I thought that altering the resolution to larger numbers made it all smaller. When I go to 'system>Prefs:>Screen Res:' I get a dialog box which would suggest that by clicking on the up/down arrows, there would be a choice; but there isn't.Left or right click just highlights the '640x480'. And by 'large' I mean that some pages have the bottom line(containing things like 'forward/quit etc)are off screen. I'd be interested and grateful for you thoughts; either here or on the heading mentioned above.
Sarum.

---

### Post by sarum on 2006-08-07
Great success following advice under thread Screen stuck @ 640x480; thanks to all concerned...Sarum

---

