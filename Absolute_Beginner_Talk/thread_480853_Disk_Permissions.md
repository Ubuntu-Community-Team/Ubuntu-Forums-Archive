---
title: "Disk Permissions"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Eldar11 on 2007-06-21
I have an extra drive that is the slave drive on my computer.  it is a 20GB ATA EIDE HDD and when I access it through my other drive, I dont have any permissions set to me, and I cant do anything with the drive.  I have already wiped it and re-formatted it to ext3 just like my other drive, but it still wont let me in. any ideas?

---

### Post by yabbadabbadont on 2007-06-21
As an example, let us assume that this drive is mounted at /media/mydrive.  While the drive is mounted, open a terminal window and run ```
sudo chown youruser:youruser /media/mydrive
```  Substitute your real username for "youruser".  After that, you should be able to create files/directories on that drive as you like.

---

### Post by Eldar11 on 2007-06-21
Thank you! I've had this drive for a while and I only have a 10GB to work off of other wise so I need this extra space, Thank you!

---

### Post by ndicostanzo on 2008-04-13
I am having the same problem. After I typed in the command chown gave the message "operation not permitted." I am working as the root user, so shouldn't I have the permissions to do this? Can anyone offer any advice?

thanks so much for any help in advance!

---

### Post by hyper_ch on 2008-04-13
is it a fat32 or ntfs drive?

---

### Post by keeler1 on 2008-04-13
You might also want to try editing your /etc/fstab to mount the drive with your user id as the drives owner.

There is a column in the fstab which asks for options.  For this you need to put uid="your user id"  Then when the drive is automounted, it is mounted with your permissions with you as the owner.  This even works for windows filesystems.

I have attached my fstab so you can see where I put the uid=.

---

### Post by ndicostanzo on 2008-04-13
no such luck, didn't seem to change a thing. The disk wasn't even on the list in the fstab file. I added it, and added uid:1000(my user id) under the options column, but nothing. I know this is really really bad, but I enabled graphical root user login and tried writing to the disk that way, it worked fine. Is it really horrible just to go about it that way? This is just a file server, and the volume that I'm having these problems with is just going to be used for backup. I'm using the app "Keep," so everything should be automated and I shouldn't need to mess with it hardly ever. The disk that is being used for the file server itself, and is being accessed by the rest of the users remotely, is the disk that ubuntu itself is running off of, and there are no permissions problems there, so it's not like root would be used any other time. Or is using root, even for that, something that isn't even an option?

Thanks!

---

### Post by julien.fs on 2008-05-23
Hello the command

```
sudo chown -R username:username /media/data-2

```

worked well for me. Now my problem is I need to grant access permission to at least two users. How to do that?

---

### Post by Norwal on 2008-06-11
:)Thanks Yabba.  I had a Fat32 Partition I converted to Ext3 and now it is useful.:)

---

### Post by hyper_ch on 2008-06-12
> **julien.fs said:**
> Hello the command

```
sudo chown -R username:username /media/data-2

```

worked well for me. Now my problem is I need to grant access permission to at least two users. How to do that?

chowning on ntfs/fat32 does nothing ;)

---

