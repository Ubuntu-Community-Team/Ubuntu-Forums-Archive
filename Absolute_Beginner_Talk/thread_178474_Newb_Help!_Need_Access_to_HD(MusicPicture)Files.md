---
title: "Newb Help! Need Access to HD(Music/Picture)Files"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by Devin22 on 2006-05-17
Ok everyone. Im rather new to Ubuntu. I really need to get access to my music and pictures so I can start working more with Linux. Mainly my pictures. I have 2 HDS. 

My first(C:)HD Is an 80 GIG (22GIG Of which are for Linux) the rest for xp. Now I have a 2nd(D;) HD Which is a 120 . It contains all of my music/pictures and editing software(Already looking into Win4Lin). Question is ..Where and how the hell do I find these ? Keep in mind I hardly know up from down right now. So good examples/walk throughs would be great. Thanks alot!


Devin

DevinLeFevere.Net

---

### Post by slimdog360 on 2006-05-17
How is the hard drive partioned, ie NTFS, FAT32 etc

---

### Post by Devin22 on 2006-05-17
Opps ..NTFS

---

### Post by Mustard on 2006-05-17
Step 1. in this process would be to see what linux calls these partitions. You can find that out with this command..

```
sudo fdisk -l
#list all partitions that linux can see
```

After that you can either manually mount or permanently mount those partitions on 'mount points'.  The mount points are just folders specifically created to mount another file system on.  The convention in linux is to have permanents mount in /mnt folder and removeable mounts in /media folder.  Most people would be mounting their windows folders under the /media folder by creating new folders like /media/windows or /media/storage.

Have a look at this link and see if it helps with the process..
[http://www.psychocats.net/linux/mountwindows.php](http://www.psychocats.net/linux/mountwindows.php)

This guide below has a section on mounting both FAT and NTFS partitions.  Just look through the index at the top of the webpage...
[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)
Hmmm..its a pretty big index, so I might throw a link in to the specific section you are looking for..
[http://easylinux.info/wiki/Ubuntu#Windows](http://easylinux.info/wiki/Ubuntu#Windows)

---

### Post by slimdog360 on 2006-05-17
[QUOTE=Devin22]Opps ..NTFS[/QUOTE]

^ what that guy said

---

