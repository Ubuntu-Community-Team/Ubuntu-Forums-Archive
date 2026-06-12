---
title: "I can't see Ubuntu files in windows"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by Firestorm21 on 2006-11-06
Hi I couldn't find this or I overlooked it. I'm pretty new to linux so I'm still learning. I was wondering how I can get windows to show my files. I have my hard drive set up this way
50MB Dell utility partition (fat32)
40GB Windows XP partition (ntfs)
8GB Ubuntu partition (ext3)
512MB swap space (swap)
1.5GB storage space (fat32)

In windows on my storage partition I can put files files on it and see them in Ubuntu, but if I put files on it in Ubuntu, windows can't see them but it knows that there is files there. windows will show the size used and if i fill up the drive it windows knows it and asks to run their cleanup tool. 

I was wondering how or if there was a way to get windows to see these. It would be very helpful because i have no other way for me to transfer files between the 2 OS's. Thanks

---

### Post by bigken on 2006-11-06
this might be what you are looking for [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Firestorm21 on 2006-11-06
Thanks. that was really fast. I'll go try that now.

---

### Post by Firestorm21 on 2006-11-06
:( Well. very close but not quite what i was going for. This lets me access the main linux partition but windows will still not show the files on the storage. i may just get rid of the storage and move the swap space to the end of the drive. is there any great way of doing this without majorly messing up my linux/windows installs? i just want to be sure before i mess it up and lose all my hard work.:)

---

### Post by bigken on 2006-11-06
windows may not understand the file type ?

---

### Post by bigken on 2006-11-06
I bet if you save the files in your ubuntu home folder and use the fs driver for windows you will be able to read them ;)

---

### Post by Firestorm21 on 2006-11-06
All the files on there at the moment are just .jpg .wmv .mpg 's
and the drive is a fat32 so windows should be able to see them. Does ubuntu write fat32 files different than windows?

Edit: sorry. didnt read fast enough. the fs driver worked. i can see the main linux part. i was just wondering about why the windows can't see the ubuntu files on the other fat32 storage drive

---

### Post by bigken on 2006-11-06
> **Firestorm21 said:**
> All the files on there at the moment are just .jpg .wmv .mpg 's
and the drive is a fat32 so windows should be able to see them. Does ubuntu write fat32 files different than windows?

Edit: sorry. didnt read fast enough. the fs driver worked. i can see the main linux part. i was just wondering about why the windows can't see the ubuntu files on the other fat32 storage drive

Sorry I dont realy know I have had this problem with fat pen drives (usb) so now I only use ext3 ;)

---

### Post by Firestorm21 on 2006-11-06
Thanks for you help. Do you know know if the qtparted tool will work for resizing the main ubuntu drive? now that I can get to the drive I don't really need the storage drive. Will it work without causing problems in ubuntu?

---

### Post by bigken on 2006-11-06
yep use the gparted [liveCD]("http://gparted.sourceforge.net/livecd.php") just delete the fat32 and move it next to your ext3 and then resize it ;)

---

### Post by Firestorm21 on 2006-11-06
Thanks.  I'll go do that now.

---

