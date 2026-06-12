---
title: "checking md5sum of a burned CD"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by samare on 2006-08-24
Hi,

I just wanted to know the MD5 value of a recorded CD. So, I issued a command as "md5sum /dev/cdrom".
But I'm getting the following error with that command.

[42951239.620000] Buffer I/O error on device hdc, logical block 51776
[42951239.840000] Buffer I/O error on device hdc, logical block 51777
[42951239.070000] Buffer I/O error on device hdc, logical block 51778
[42951239.300000] Buffer I/O error on device hdc, logical block 51779
[42951239.530000] Buffer I/O error on device hdc, logical block 51780
[42951239.770000] Buffer I/O error on device hdc, logical block 51781
[42951239.000000] Buffer I/O error on device hdc, logical block 51782
md5sum: /dev/cdrom: Input/output error

Somebody please tell me the reason for these errors. Actually I'm checking the md5 value of a RedHat CD which I downloaded from RedHat. I checked the md5checksum of the ISO image and it's the same as in RedHat site. And the ISO image size also the same. But the CD test failed when testing the CD and installation also getting failed. I just wanted to know has anything happened while burning the ISO to the CD. You may think why Redhat users are in Ubuntu forum. Well,I've already installed WinXP,Ubuntu6.06 and now I want install RehHat(multiboot).Please help

samare

---

### Post by moma on 2006-08-24
Burn a new CD.  Burn with _slow_ speed.
---

This is howto get MD5SUM from a CD image.
[http://www.troubleshooters.com/linux/coasterless.htm#rawread](http://www.troubleshooters.com/linux/coasterless.htm#rawread)
The "rawread" script is given on that page. Copy/paste the script to a file. Make it executable 
$ chmod +x rawread 

And run it.
$ ./rawread /dev/cdrom | md5sum 
or  
$ ./rawread /dev/cdrom > cdrom.iso 
and md5sum cdrom.iso file.

---

### Post by bodhi.zazen on 2006-08-24
Rather then md5sum /dev/cdrom

Address the cd via it's hax

On my box the cdrom is hda

Thus
```
md5sum /dev/hda
``` worked fine.

>  md5sum /dev/hda

587e6acba46cf946a1f5867b2b107d03  /dev/hda

Which is in fact the correct md5sum for that particular CD.

Also if you burn with K3b it will give you the md5 sum of the iso file and check the integrity of our burned CD. I have found K3b to be the most reliable burner.

The above script looks cool though.

---

### Post by samare on 2006-08-24
Hi:) ,

Thanks a lot for all the support. I did burn a new CD with slow speed as moma said. And I checked the md5 value as bodhi said. Now the MD5 value of new CD is same as the original iso image.

samare

---

### Post by bodhi.zazen on 2006-08-24
congrats.

Consider k3b, it allows me to burn at full speed, more reliable.

It does give some error messages when starting the program which can be ignored.

---

