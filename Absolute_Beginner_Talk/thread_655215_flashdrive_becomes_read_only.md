---
title: "flashdrive becomes read only"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by basilwatson on 2008-01-01
this has happened before but this time I cannot use another program to format the disk to carry on using it 

What happens is , as you use it normally ( its the flash for my phone , windows mobile 6) , so as I use a card reader to put files on and off between Phone ( mobile 6 )  laptop Ubuntu 7 , and work , PClinux 07.

Somewhere between all three , the disk has become read only , user ( root )  .

I have tried formating in Gparted , windows and allowed all users ( chmod 777 /media/disk 

and it comes back read only , can do the business 

Any suggestions ??


Kind regards and happy new year to everyone 

Stephen

---

### Post by kelvin spratt on 2008-01-01
Try Kmformat its in the repros it format anything just make sure you select your flash drive. Or in windows use this Hp flashdrive format tool  [http://files.filefront.com/HPUSBFWEXE/;8576665;/fileinfo.html](http://files.filefront.com/HPUSBFWEXE/;8576665;/fileinfo.html)
hope this helps you?

---

### Post by basilwatson on 2008-01-01
tried both , still Read only 

Ho was the same as windows  , and kmformat installed but wouldn't work tried both command line and manual install 

So back to square one 

with a very expensive  4 gig micro card that is read only !

  Ideas ?  how can you give it permission 

Stephen

---

### Post by Sef on 2008-01-01
I have the same problem.   Here are some [suggestions]("http://ubuntuforums.org/showthread.php?t=618166") that have been given to me.

---

### Post by basilwatson on 2008-01-01
It remains read only 

 Try gpared once again then I am out of Ideas 

Anyone ??
Stephen

---

### Post by basilwatson on 2008-01-02
bump

sorry 
Stephen

---

### Post by eternicode on 2008-01-02
Have you tried manually unmounting it then manually remounting it with the "-o fmask=0000,dmask=0000" switch?  'Twould be a temporary fix, but it might allow usage until you get a permanent fix.

Read-only automounting could also be the result of a corrupted filesystem.  If the drive is FAT32 (most USB flash drives are), first unmount it, then try

```
fsck.vfat -af /dev/sdb1
```

Obviously, replace /dev/sdb1 with the main partition of the flash drive.

Also, what does dmesg say?  I don't know whether or not it gives info about remounting things ro.

---

