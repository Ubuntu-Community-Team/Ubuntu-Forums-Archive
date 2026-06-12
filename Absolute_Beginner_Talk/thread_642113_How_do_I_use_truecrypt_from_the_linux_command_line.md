---
title: "How do I use truecrypt from the linux command line?"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by steelmole on 2007-12-16
I have a true crypt volume that works fine in windows, and I want to use it in ubuntu.  I have true crypt installed.  I think the volume is sda6, something like that, but I don't know where this is, or how exactly to use the command line version of truecrypt.

---

### Post by fmbugdadi on 2007-12-16
Below is a link to a page that may have the information you need:

[http://polishlinux.org/howtos/truecrypt-howto/]("http://polishlinux.org/howtos/truecrypt-howto/")

Here is another link to a forum specifically for truecrypt users which I highly recommend:

[http://forums.truecrypt.org/]("http://forums.truecrypt.org/")

it appears that the truecrypt forum is down temporarily, try later.....

---

### Post by steelmole on 2007-12-16
Aha, I got it to work.  Is there any way to make a script or something so that I don't have to type so many commands at the command line, i just have to type my password?

---

### Post by Dr Small on 2007-12-16
> **steelmole said:**
> Aha, I got it to work.  Is there any way to make a script or something so that I don't have to type so many commands at the command line, i just have to type my password?
Yes. Just spill the exact commands out here, and I should be able to make it into a bash script.

---

### Post by llamakc on 2007-12-16
Yes. What are all of the lines you're typing?

---

### Post by fmbugdadi on 2007-12-16
Goto the first link that I listed, then scroll down to automatic mounting after reboot.

---

### Post by steelmole on 2007-12-16
well the first thing was something like :
sudo mkdir /mnt/tc
then i did truecrypt -u /dev/sda6 /mnt/tc
then i have to give my passphrase.  It'd be nice to be able to do this in one click.  Also unmounting would be useful, which is : truecrypt -d /mnt/tc

I'm not really sure about most of this (i only started linux a few days ago, i don't really understand the filesystem).

---

### Post by Greevous on 2007-12-28
I've tried to mount an encrypted partition on a USB device, but when I try to mount with 
```
truecrypt /dev/sdg2
```
I get this error: 
```
Enter password for '/dev/sdg2': 
device-mapper: reload ioctl failed: Invalid argument
Command failed
```

I can't figure out why I can't mount this partition, and the truecrypt forums are down. :(

---

