---
title: "Backup Mac Data thru Ubuntu LiveCD"
date: 2009-10-29
forum: Apple Hardware Users
---

### Post by wreckingcru on 2009-10-29
I have a macbook running Leopard. In an effort to upgrade to Snow Leopard, Apple screwed up my Leopard install and now I have a non-working macbook.

I wanted to backup some of my data to a USB drive via Ubuntu LiveCD before I try reformatting with the original install OSX cd. 

Here is my problem:

I can't get "copy" access to the hard drive directories. I used "gksudo nautilus" to launch it as root, so I can view the files. However, whenever I try to copy the data over, Ubuntu won't allow me citing lack of permissions. I tried right-clicking and changing the permissions, but couldn't do that either. The user on the /home/username/ directories is listed as User#501.

Any help???

---

### Post by Aemaeth on 2009-10-29
Have you tried sudo chown or chmod? if not try

sudo chmod 7777 /(foldername) from the terminal

---

### Post by wreckingcru on 2009-10-29
I tried that, but I get <folder name>: read-only file system

What do i do?

---

### Post by Wiebelhaus on 2009-10-29
You have to install read and write abilities , read ability is out-of-box not write (afaik). Install hfsplus and hfsutils from the repositories. There's also third party projects out there to [google knows]("http://www.google.com/search?q=ext2fsx&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a").

---

### Post by wreckingcru on 2009-10-29
I tried this after installing hfsplus and hfsutils,

```

ubuntu@ubuntu:~$ sudo mount -t hfsplus /dev/sda1 /mnt/osc/
mount: wrong fs type, bad option, bad superblock on /dev/sda1
```


My mac drive is at /media/Macintosh HD  and is getting mapped to /dev/sda1.


I'm a bit of a newbie, so please help!

---

### Post by Wiebelhaus on 2009-10-29
> **wreckingcru said:**
> I tried this after installing hfsplus and hfsutils,

```

ubuntu@ubuntu:~$ sudo mount -t hfsplus /dev/sda1 /mnt/osc/
mount: wrong fs type, bad option, bad superblock on /dev/sda1
```


My mac drive is at /media/Macintosh HD  and is getting mapped to /dev/sda1.


I'm a bit of a newbie, so please help!

Post the output of:

```
sudo fdisk -l
```

I'm getting off work in about ten minutes , so I won't be near a PC , but the person who walks you through it will need that output.

Cheers and good luck , I'll check back tomorrow.

---

