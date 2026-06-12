---
title: "Fat32 drive - mount at logon"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by AnotherMuggle on 2007-08-01
I have a shared fat32 drive which I can manually mount but I am prompted for my admin. password.

How do I get the drive to mount at logon without prompting for a password?

Thanks,
Tom Kear.

---

### Post by reckless2k2 on 2007-08-01
are you mounting it via fstab? i'd suggest via fstab and the user/pass can be in the syntax or you can hide it.

---

### Post by AnotherMuggle on 2007-08-01
> **reckless2k2 said:**
> are you mounting it via fstab? i'd suggest via fstab and the user/pass can be in the syntax or you can hide it.

Sorry, I'm a new user so that means nothing to me :(

---

### Post by Inxsible on 2007-08-01
> **tomkear2006 said:**
> Sorry, I'm a new user so that means nothing to me :(

Is this an external drive?

if yes, you should use pmount to mount it
Install pmount if you dont already have it

```
sudo aptitude install pmount
```
Then use it like
```
sudo pmount /dev/Xd*? MOUNT_POINT
```where X = s or h
*= a,b,c,d....
?= 1,2,3,4...
MOUNT_POINT  - is a name of your choosing eg. MyDrive, or MyFATDrive. Refrain from using spaces in the names as you will have to use quotes to access it later and is a pain in the a$$, IMHO

it will mount the drive under /media for you and create a folder with the mount point name that you provide. So make sure you don't already have a folder with that name under /media

---

### Post by ugm6hr on 2007-08-01
This explains it all:
[http://www.psychocats.net/ubuntu/mountwindows#fat32](http://www.psychocats.net/ubuntu/mountwindows#fat32)

Just substitute */dev/hdb1* for */dev/[COLOR="Red"]your-fat-drive-number[/COLOR]* and */fat_files* for */media/[COLOR="Red"]your-mount-point[/COLOR]*

---

