---
title: "Why does Ubuntu mount drive in /media and not /mnt"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-02-13
Why does Ubuntu mount hard drives in /media and not /mnt as, apparently, most (maybe all) other distros do?

---

### Post by highneko on 2007-02-13
That's a good questions. I'm curious too. Maybe ubuntu is just cool and different? Maybe it's for security reasons? Maybe they thought new users would make more sense of it? In any case I like it. Do you like it? :3

---

### Post by lamego on 2007-02-13
They have done a different interpretation of the standard for linux file systems structure:
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

---

### Post by ricardisimo on 2007-02-13
I mounted my new drive in /mnt, as per the recommendation of a kind soul right here in Ubuntu Forums, so it's certainly not a rule, maybe just a flavor.

---

### Post by Jucato on 2007-02-13
More than trying to be cool or different, they are following the most current Filesystem Hierarchy Standard, which says that removable media should be mounted to /media and not /mnt. Although the FHS doesn't mention USB drives, it was written in a time when those things were not in widespread use.

I guess the problem is whether you could consider hard drives as removable media or not. I think the rationale for mounting hard drives to /media by default comes from the purpose of /mnt to be a place where the "system administrator may temporarily mount a filesystem as needed." 

Some distros are following this trend, Mandriva for example.

---

### Post by akshaysrinivasan on 2007-02-13
May be because drives mounted in /mnt are not displayed on the GNOME desktop.

---

### Post by ricardisimo on 2007-02-13
Is that true? How about on KDE? So if I had mounted my new drive in /media it would appear on my desktop without my having to form a symbolic link to it, etc.?

---

### Post by Patrick K on 2007-02-13
I have KDE, which I rarely use. The drives are mounted in /media but don't show up on the desktop.

---

### Post by coolen on 2007-02-13
The way I see it, any partition not mounted as some integral part of the Linux filesystem is going to be used for storage, just as a CD or USB drive would be. Granted, they're not nearly as portable, but many use them for information they need access to from both Ubuntu and Windows.
I have a fat32 partition in which I keep all of my music, for example, and if I ever decide to reinstall Windows on my first partition, it'll be really, really neat. It's also handy to have all of my additional filesystems located in the one place.
Besides, the rationale for the standard is for programs to be able to easily find dependencies and essential commands, know where to install to, and so on. Basically, to ensure that a program written on a SUSE box can run well on a Debian machine without a lot of tinkering. Hard drives mounted in either /mnt or /media are unlikely to contain any vital components which such programs may need, so you can really pick which one you prefer and not worry about it.
Apart from all that, I prefer /media, just because the name looks nicer. I've never liked words without vowels.

---

### Post by OBnascar on 2007-02-13
> **ricardisimo said:**
> Is that true? How about on KDE? So if I had mounted my new drive in /media it would appear on my desktop without my having to form a symbolic link to it, etc.?

I run Ubuntu gnome and Kubuntu KDE 6.10, both show desktop icons using "/media"

---

### Post by Patrick K on 2007-02-14
> **OBnascar said:**
> I run Ubuntu gnome and Kubuntu KDE 6.10, both show desktop icons using "/media"

Interesting. I installed the KDE-desktop into Gnome-Ubuntu (Edgy) and not Kubuntu, so maybe that the reason the drive icons don't show in KDE. I didn't do anything to keep them from showing.

---

### Post by OBnascar on 2007-02-14
> **Patrick K said:**
> Interesting. I installed the KDE-desktop into Gnome-Ubuntu (Edgy) and not Kubuntu, so maybe that the reason the drive icons don't show in KDE.

Good point - and I did not do anything special to make them show.......lol

---

