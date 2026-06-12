---
title: "Forgot Username -- What now?"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by tech01 on 2006-04-10
My dear friend support tech02, installed Ubuntu and very conveniently forgot the user name he used to install the program. Is there a way to find a solution to the problem.](*,) ](*,) ](*,)

---

### Post by truNWA on 2006-04-10
the only way i can think of is an uninstall and reinstall, because u need a user name to get into all the terminal stuff.

---

### Post by sYs^ on 2006-04-10
Boot with a liveCD and check the /etc/passwd file (of course not on the livecd, on that partition where he installed Ubuntu).
There will be his username too :p

---

### Post by opus on 2006-04-10
Do you have a copy of  the Ubuntu live CD?  Any of them should work, ie: 5.10 Breezy Badger or 6.04 Dapper Drake Flight 6 (or 5, 4, etc).  Boot from the live CD.  

This is where it will get tricky.  You will need to mount the partition that your current Ubuntu is installed on.  This will be named /dev/hda1 or something.  If you already know, great.  If not try the following command:
```
sudo fdisk -l /dev/hda
```
If that gives an error, try using /dev/hdb or /dev/hdc.  Fdisk will list that partitions currently setup on your hard drive.  If you let the installer setup the partitions for you there should be one big partition listed as "Linux".  Note the device name for that one. For this example, we will assume it is /dev/hda2. Then:
```
mkdir /media/hda2
mount /dev/hda2 /media/hda2
ls /media/hda2

```
If that shows a bunch of folders like usr, bin, sbin, boot, media, usr, and tmp, you found the right one.  Otherwise, repeat the steps above until you find it.

Once you've found the right partition:
```
sudo gedit /media/hda2/etc/password
```
All of the users setup on the system are listed in that file.  Most of these are system users, but your user account is in there somewhere.

Aaron

---

### Post by tmahmood on 2006-04-10
you don't even need to do ALL that!!!!
just goto /home folder of your Linux installation. when you create an user it also creats a folder named as [username] in the /home directory.

---

### Post by sYs^ on 2006-04-10
[QUOTE=opus]
Once you've found the right partition:
```
sudo gedit /media/hda2/etc/**password**
```
All of the users setup on the system are listed in that file.  Most of these are system users, but your user account is in there somewhere.

Aaron[/QUOTE]

It's passwd, not password :p
[B]
tmahmood:[/B] You have got the point, lol :>

---

### Post by tmahmood on 2006-04-10
and you don't even need live CD if you can work with Terminal. just boot into recovary mode (from grub menu) and root prompt type

```

cd /home
ls

```

you'll get the list of folders assigned to the users.

---

### Post by opus on 2006-04-10
Wow.  That is a lot easier.  Thanks for making all of my hard typing work obsolete.  :)

I forgot about the recovery mode, and the ls /home folder would be MUCH easier.

Aaron

---

