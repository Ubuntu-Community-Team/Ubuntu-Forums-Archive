---
title: "Accessing Windows partition from Ubuntu"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Patsy on 2007-03-10
Hi

I am trying to access my Windows partition from Ubuntu.  Looking at the instructions it assumes your Windows location is /dev/hda1 whereas mine appears to be /dev/hda2.  Any advise on how to sort this (assuming it's possible) will be very much appreciated.  My Windows OS crashed and won't load  any personal settings and my daughter's much slogged on essay is in there. Unfortunately she didn't save it in shared folders on our network and has no back up copy (took days to write). Can't load personal settings in safe mode and recovery process doesn't work.  No Windows CD and master CDs do not work.

---

### Post by Iarwain ben-adar on 2007-03-10
A simple
```
 mkdir ~/windows
```

And a ```
sudo mount /dev/dha2 ~/windows
```

Will do :D


Iarwain

---

### Post by dstew on 2007-03-10
Larwain means sudo mount /dev/**hda2** ~/windows of course. A typo.

---

### Post by Patsy on 2007-03-10
> **Iarwain ben-adar said:**
> A simple
```
 mkdir ~/windows
```

And a ```
sudo mount /dev/dha2 ~/windows
```

Will do :D


Iarwain

Thanks. Now as a complete Ubuntu novice do I type the first code, then press enter or something and then type the second code and what does 'only root can do'?  What is root?

Thanks:)

---

### Post by taurus on 2007-03-10
Try something like these from a terminal, assuming it's an ntfs filesystem.

```
sudo mkdir /media/hda2
sudo mount -t ntfs /dev/hda2 /media/hda2 -o nls=utf8,umask=0222
ls -la /media/hda2
```
Use the same password that you log in with when it asks you to enter a password.

---

### Post by dstew on 2007-03-10
The message "Only root can do that" means that an ordinary user cannot mount disks, only a user with "root" privleges. The "root" user can change everything in the computer.

However, the root user can do a lot of damage if he or she doesn't know what he or she is doing. In Ubuntu, the root user account is disabled for that reason. However, sometimes you need root privleges to do things, like edit configuration files or mount disks. The sudo command (pronounced "soo doo", meaning superuser do) gives you root privleges for a short time, about 5 minutes, so you can do some limited administrative work. Because it times out, it prevents you from continuing to work as root and by mistake making a mess of your system. If you see the message "Only root can do that", just repeat the command with sudo in front of it. It asks you for your password, and then it will complete the command.

---

### Post by Patsy on 2007-03-11
> **taurus said:**
> Try something like these from a terminal, assuming it's an ntfs filesystem.

```
sudo mkdir /media/hda2
sudo mount -t ntfs /dev/hda2 /media/hda2 -o nls=utf8,umask=0222
ls -la /media/hda2
```
Use the same password that you log in with when it asks you to enter a password.

Thank you so much everybody who helped me with this.  I am unbelievably grateful.  I have successfully mounted windows partition and retrieved my daughter's work. Thank you again:)

---

