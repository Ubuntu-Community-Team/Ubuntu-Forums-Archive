---
title: "Changing Location of /home"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by happy-and-lost on 2006-09-25
I have Ubuntu dual booted with WinXP at the mo, and I have a FAT32 "sharing partition" which I keep all my documents/music/etc. on which is labeled as /media/sda5

I want to make that directory my /home. How do I do that without losing anything on either my existing /home directory or the directory which will become /home?

---

### Post by wieman01 on 2006-09-25
You mean you want to install **/home** on "sda5" which happens to be a FAT32 partition? Oh man, I would not recommend that.

Have your personal files, etc. on "sda1" so that you can share between Windows & Linux, but don't create your /home folder on it.

---

### Post by happy-and-lost on 2006-09-25
Why not? Would having /home on FAT32 cause system instability?

---

### Post by monktbd on 2006-09-25
i strongly do not recommend that.
fat32 does not support proper file permissions.

if you want an easier access to that partition you can mount it in a subdirectory of /home/youruser.

so just mount /media/sda5 to /home/youruser/mydata or whatever folder name you would like.


what advantage would you get from that anyway? you can add bookmarks that then show up in the places menu if that is what you need for easier access.
is there any reason why having that disk your /home would make things easier?

---

### Post by stilus on 2006-09-25
I fully agree with wieman01. fat32 has only a fraction of the filesystem security attributes native linux filesystems have. Not to mention problems with captial filenames (capital versus normal letters for instance). 
Really, just keep your /home where it is :)

what you could do ofcourse, is use 
```
ln -s
``` (see the man page) to make a softlink to it.

Kind regards,
stilus

---

### Post by happy-and-lost on 2006-09-25
Ah right.

It's not that big a deal, it's just a strict-organisation-of-computer-files fetish I have.

---

### Post by wieman01 on 2006-09-25
> **happy-and-lost said:**
> Ah right.

It's not that big a deal, it's just a strict-organisation-of-computer-files fetish I have.
Same here, so I understand your point. But keep it simple and create a FAT32 partition just for data & files as the other have highlighted. This way you can share & do backups easily.

Then mount the FAT32 partition to **/data** for instance. That'll do. Good luck.

---

### Post by CatKiller on 2006-09-25
> **stilus said:**
> I fully agree with wieman01. fat32 has only a fraction of the filesystem security attributes native linux filesystems have. Not to mention problems with captial filenames (capital versus normal letters for instance). 


Actually, the thing that got me was that you can't have symlinks on a FAT partition. Nasty.

And files get fragmented. Stupid antiquated filesystem ](*,)

---

### Post by MrHorus on 2006-09-25
> **CatKiller said:**
> Actually, the thing that got me was that you can't have symlinks on a FAT partition. Nasty.

And files get fragmented. Stupid antiquated filesystem ](*,)

If you really want you could mount your windows drive somewhere like /home/someone/windows for example?

---

### Post by happy-and-lost on 2006-09-25
It's not a big issue. It mounts automatically as sda5 and appears on my desktop.

Cheers for your help anyways :)

---

### Post by CatKiller on 2006-09-25
> **MrHorus said:**
> If you really want you could mount your windows drive somewhere like /home/someone/windows for example?

I already do ;) Actually, at /data/fat and /music.

I came across this particular limitation when attempting to copy my .wine folder to a FAT32 partition, since I didn't have much space on my ext3 partition at the time. I have since made my ext3 partition large enough for my needs.

---

