---
title: "Changing Permissions?"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by skatiN64 on 2006-06-19
When I try to access my slave drive, a message pops up and says I don't have permission. When I try to change the permissions the message simply says can't change permissions.  Although it's possible that it also says sorry...
anyone have any experience with this? 
help please thanks

---

### Post by digby on 2006-06-19
Do you know what filesystem is on your slave drive?  If you don't know the answer to that, does it hold windows and what version?

I don't think what you're after will be at all difficult, but we need just a bit more info.

---

### Post by Zed on 2006-06-19
Can you show us the contents of your /etc/fstab?

---

### Post by aysiu on 2006-06-19
It's very likely one of these two links will help you:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by skatiN64 on 2006-06-19
wow thanks I had no idea people would respond that fast
There is no os on the drive. I'm not trying to run multiple os's here, though maybe I will if this don't work out.
The drive is formatted in ntfs.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

thanks again

---

### Post by steveneddy on 2006-06-19
Follow <b>aysiu's</b> advice and go to her website. It is very comprehensive and easy to follow. Take my advice and follow hers (hers?)...

anyway, it worked for me.
-SE

---

### Post by Princey on 2006-06-19
[QUOTE=skatiN64]wow thanks I had no idea people would respond that fast
There is no os on the drive. I'm not trying to run multiple os's here, though maybe I will if this don't work out.
The drive is formatted in ntfs.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

thanks again[/QUOTE]

Because your drive is ntfs, you'll have to manually mount it. Can you post the output of ```
sudo fdisk
``` This will enable us to point you how to mount your ntfs drive. Ayisu has a very good guide he has pointed out, but from your fstab entries, the drive in question isn't listed. You'd have to give the output of the code I gave to find out which drive it is to have it successfully mounted.

---

### Post by skatiN64 on 2006-06-20
well you guys aren't gonna believe this but it asks for a password and then won't let me type anything. I can hit enter, but it just says wrong password. I even reset it just for kicks.
Ayisu's guide should do the trick if I can get past this bug. any ideas? please
and
don't lol 
sorry for the bad grammer, I'm not sure how that happen...](*,)

---

### Post by aysiu on 2006-06-20
Instead of hitting enter, just type your password.

You won't see your password. You won't even see *****, but your password will be accepted. Don't worry.

---

### Post by skatiN64 on 2006-06-20
heh
I think I tried that at one point when I was typing fstab instead of fdisk
I don't have the internet on that pc so I've been kinda running back and forth
but it payed off
It's all working. thanks for the awesomeness
Even though I've never used linux before today, I'm sure I could now help others with this problem... although that's probably all =D

---

