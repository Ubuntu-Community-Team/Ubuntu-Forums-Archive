---
title: "Copy from CDROM failed"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by mmarif4u on 2008-03-23
i am trying from last one hour to copy video file from cdrom to my HDD,but no luck.i also tried root access,but same problem.

How can i copy files from cdrom.

---

### Post by quinnten83 on 2008-03-23
> **mmarif4u said:**
> i am trying from last one hour to copy video file from cdrom to my HDD,but no luck.i also tried root access,but same problem.

How can i copy files from cdrom.

I've never heard of that before.
Usually I just select the file and copy it to where ever I want.
Do you get an error message saying what happens?
 Also for troubleshooting, have you tried copying from the command line?
your cd rom is in the folder /media
 i think the command would then be 
```

cp /media/cdrom/myfile /home/myusername/my location
```

you might have to use sudo, but I am not sure.
If you do get an error msg, please tell us exactly (As in step by step) what you are doing and also paste the output of the console here...

---

### Post by mmarif4u on 2008-03-23
I tried the terminal this time and get this error which is same when i am trying to copy by right click.

> root@ANL-Laptop:~# cp /media/cdrom0/MPEGAV/AVSEQ01.DAT  /Desktop
cp: reading `/media/cdrom0/MPEGAV/AVSEQ01.DAT': Input/output error

---

### Post by quinnten83 on 2008-03-23
There is something wrong with either this particular CD or with your CD rom drive.
do you have the restricted media packages installed?
if not

sudo apt-get install ubuntu-restricted-extras

be aware that this will also start a Java installation, be careful with that, I didn't finish it correctly and it broke my apt-get. you should be fine though, so don' t panic.

Have you tried copying from another CD to be sure the media is not corrupted and also, why in heavens name are you working as root?

---

### Post by mmarif4u on 2008-03-23
i tried another cds with same .DAT format.same result.
I came to root for access permissions.i was thinking may be it is bcoz of permissions.

---

