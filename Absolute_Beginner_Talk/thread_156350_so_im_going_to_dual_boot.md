---
title: "so im going to dual boot"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by mr.champagne on 2006-04-06
i have a usb hdd that i want to use to bckup the docs i have on here but i dont have permision to copy wy do i not have permission ](*,) i am the USR!!!! i need permission to copy files from one storage device to another quickly

so my questions are:
1. why are permissions nesescary when there is only one user

2. how do i copy the files onto my usb hdd

thx.

---

### Post by Qrk on 2006-04-06
Its easy enough to get permissions, paste this into a terminal. However, I think you should already have copy permissions, however.

```
gksudo nautilus
```

I assume you want to copy your entire hardrive? You can probably get away with just copying your home folder and the contents of /var/cache/apt/archives. But it depends on what you want to do.

---

### Post by mr.champagne on 2006-04-07
i onlywnat to copy a few files out of my home/USERNAME Dir. but even with nautilus i run into the permission problem

---

### Post by aysiu on 2006-04-07
[QUOTE=mr.champagne]
1. why are permissions nesescary when there is only one user[/quote] [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

> 
2. how do i copy the files onto my usb hdd Usually, you plug it in, it shows up on your desktop, and you drag-and-drop files into it. If you're having problems with it showing up, try this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Make sure the drive is plugged in and on first.

---

### Post by ferebee on 2006-04-07
[QUOTE=aysiu][http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

 Usually, you plug it in, it shows up on your desktop, and you drag-and-drop files into it. If you're having problems with it showing up, try this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Make sure the drive is plugged in and on first.[/QUOTE]

Also, if it's formatted with ntfs, you won't be able to copy files to it 
whether you have permissions or not, unless you want to try this:
[http://ubuntuforums.org/showthread.php?t=142481]("http://ubuntuforums.org/showthread.php?t=142481")
As the post says, **[COLOR="Red"]this is risky[/COLOR]**, so you might not want to.

Could the files not be burnt to a cd or dvd?

---

### Post by Ob1 on 2006-04-07
I'm having the same problem.

---

### Post by mr.champagne on 2006-04-09
ahh it is ntfs oh well thx 4 the help

---

### Post by Sef on 2006-04-09
> i dont think its ntfs but i could be mistaken

To check what it is, type in the terminal sudo fdisk -l (see below)  and post it here, so we can help you more:

Applications > Accessories > Terminal

sudo fdisk -l

This will list your partitions.

---

