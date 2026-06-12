---
title: "MDSUM - where?"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by Wikzo on 2007-03-17
I want to check the file hashes for the Xubuntu .iso-file, but now the whole Ubuntu.com is getting new design and I can't find the place with all the MDSUM-numbers. Can anyone tell me where it is? Thanks :)

---

### Post by louis_nichols on 2007-03-17
It's contained in the iso file itself. you just have to mount it as a loopback device and read the file. The command is this:

sudo mount -t iso9660 -o loopback *iso-file* *mount-point*

---

### Post by Wikzo on 2007-03-17
I got Windows XP and a file hash-plugin. Now I want to compare the MDSUM in the iso-file with the correct number ... just to be 100% sure it is okay.

---

### Post by wpshooter on 2007-03-17
> **Wikzo said:**
> I got Windows XP and a file hash-plugin. Now I want to compare the MDSUM in the iso-file with the correct number ... just to be 100% sure it is okay.

IMO, it is much more important to check the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu.

---

### Post by bodhi.zazen on 2007-03-17
Check this link : [http://www.ubuntuforums.org/showthread.php?t=290339](http://www.ubuntuforums.org/showthread.php?t=290339)

---

### Post by Wikzo on 2007-03-17
Thanks. I found it by myself on the downloading site :)

[http://ftp.cw.net/xubuntu/releases/6.10/release/MD5SUMS](http://ftp.cw.net/xubuntu/releases/6.10/release/MD5SUMS)

---

### Post by Wikzo on 2007-03-17
New question: Will the Xubuntu cd work as a live session like Ubuntu does?

I won't boot it up, if I can't try it out before installing :)

**EDIT:** Oh, sorry ...

"Minimum system requirements

To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only required you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 64 MB RAM, but it is strongly recommended to use at least 128 MB RAM."

Heh :P

---

