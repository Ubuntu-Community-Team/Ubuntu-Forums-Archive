---
title: "Easy questions:Permission to write to disc."
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-07-01
I have a USB external hard drive, I want to copy some files to it, it says I don't have permission to write to it (or delete from it)... how do I get permission?

I'm getting sick of these permission issues in Ubuntu, annoying... I'm supposed to be in 'full control of my computer' with Linux, right?  Doesn't seem like it.

---

### Post by apjone on 2007-07-01
Permissions with linux are hard to get your head round at first. 
you could do a 
```

sudo chown -R username /where/disk/is/mounted

```

and that would make you owner. Thats what I do, may not be correct way, but it works for me.

---

### Post by aberadam on 2007-07-01
Thanks, I just tried it but it didn't work:

> adam@adam-desktop:~$ sudo chown -R adam /media/New Volume
Password:
chown: cannot access `/media/New': No such file or directory
chown: cannot access `Volume': No such file or directory
adam@adam-desktop:~$ 



---

### Post by apjone on 2007-07-01
ahh that is because of the space , try this 

```

adam@adam-desktop:~$ sudo chown -R adam "/media/New Volume"

```

If you have a path with spaces either
a) put the path inside " " quotes
b) escape the space using a "\" like 

```

adam@adam-desktop:~$ sudo chown -R adam /media/New\ Volume

```

---

### Post by aberadam on 2007-07-01
> adam@adam-desktop:~$ sudo chown -R adam/media/New Volume
chown: `adam/media/New': invalid user
adam@adam-desktop:~$ 


Invalid user?

All Iwant to do is copy to a USB external drive!  Christ...

---

### Post by aberadam on 2007-07-01
Thanks, I tried them both but neither worked:

> adam@adam-desktop:~$ sudo chown -R adam "/media/New Volume"
chown: changing ownership of `/media/New Volume/Backup.bkf': Read-only file system
chown: changing ownership of `/media/New Volume/System Volume Information/MountPointManagerRemoteDatabase': Read-only file system
chown: changing ownership of `/media/New Volume/System Volume Information/tracking.log': Read-only file system
chown: changing ownership of `/media/New Volume/System Volume Information': Read-only file system
chown: changing ownership of `/media/New Volume': Read-only file system
adam@adam-desktop:~$ adam@adam-desktop:~$ sudo chown -R adam /media/New\ Volu
bash: adam@adam-desktop:~$: command not found
adam@adam-desktop:~$ sudo chown -R adam /media/New\ Volume
chown: changing ownership of `/media/New Volume/Backup.bkf': Read-only file system
chown: changing ownership of `/media/New Volume/System Volume Information/MountPointManagerRemoteDatabase': Read-only file system
chown: changing ownership of `/media/New Volume/System Volume Information/tracking.log': Read-only file system
chown: changing ownership of `/media/New Volume/System Volume Information': Read-only file system
chown: changing ownership of `/media/New Volume': Read-only file system
adam@adam-desktop:~$ 


---

### Post by apjone on 2007-07-01
sudo chown -R adam /media/New Volume

needed a space between adam and /media  

my bad :(

---

### Post by apjone on 2007-07-01
what filesystem is the usb drive, if it is NTFS you will need some other bits

---

### Post by aberadam on 2007-07-01
With the space:

> adam@adam-desktop:~$ sudo chown -R adam /media/New Volume
chown: cannot access `/media/New': No such file or directory
chown: cannot access `Volume': No such file or directory
adam@adam-desktop:~$ 


It could be NTFS, I first used this drive with XP...

---

### Post by apjone on 2007-07-01
if you do a
```

mount | grep "/media/New Volume"

```
it will tell you the file system, if it is ntfs check out

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by aberadam on 2007-07-01
I got it working with ntfs-3g. 

Thanks a lot apjone!

---

### Post by apjone on 2007-07-01
no problem, thats what we are here for

---

### Post by davidjmayo on 2007-07-01
adam

this won't fix your permissions problems but this may help you as you seem to have a little trouble with your filenames in the command line

> While Linux supports long file names which may contain embedded spaces and punctuation characters, limit the punctuation characters to period, dash, and underscore. Most importantly, do not embed spaces in file names. If you want to represent spaces between words in a file name, use underscore characters. You will thank yourself later.

rename your files for example New-Volume or New_Volume (look through the file system and they are all like this (I saw this on a quick check of a few directories)

also remember new-volume and New-Volume would be two different filenames so are two different files.

source of quote [http://linuxcommand.org/lts0020.php](http://linuxcommand.org/lts0020.php)

You can rename your files when you need in your file manager by right click and then rename

---

### Post by aberadam on 2007-07-01
Thanks david!

---

