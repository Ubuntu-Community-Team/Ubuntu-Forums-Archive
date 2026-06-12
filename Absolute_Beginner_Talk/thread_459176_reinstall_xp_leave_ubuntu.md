---
title: "reinstall xp leave ubuntu"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by xtang on 2007-05-30
I know this will not be simple but...

Windows XP has deteriorated again as usual, so is it possible to reinstall windows xp and somehow retain my ubuntu partition?

---

### Post by taurus on 2007-05-30
Yes, but XP will overwrite your GRUB so you need to install it again to be able to boot into Ubuntu (and XP).

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by Cypher on 2007-05-30
If you re-install XP to the partition it already currently resides on, it will not affect/touch Ubuntu. However, upon  installation, it will overwrite GRUB with it's own boot manager and you will only be able to boot into XP.

You will then need to use the Recovery CD to get back to Ubuntu to re-install GRUB so that you can onec again boot into Ubuntu and XP..

---

### Post by plcdfa on 2007-05-30
Yes it is. Just leave alone the linux partitions in windows installer. After xp is up and running you',ll have to boot the Ubuntu Live CD (the install cd) and run grub-install from a terminal to get the grub menu back.

---

### Post by Sparkster185 on 2007-05-30
I haven't done this myself, but I believe it will ignore the other partitions on the HD (assuming you don't tell it to re-format the disk) and only touch the ntfs partition.

Do note that it will destroy your GRUB (your boot loader) setup, so you'll only be able to boot to Windows.  There are applications out there that you can run as boot-CDs that will fix the bootloader.

---

### Post by meborc on 2007-05-30
just install windows in its old partition and not on the linux one... then you need to reinstall grub as windows overwrites the MBR... 

this is what you need then - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

EDIT: :D i'm getting old... or is there just way tooo much ubuntu-love here in the forums just now?! ... 4 people faster than me... i must work on my typing muscles :D

---

### Post by plcdfa on 2007-05-30
I'm not fast enough. :)

---

### Post by Inxsible on 2007-05-30
> **xtang said:**
> I know this will not be simple but...
 
Windows XP has deteriorated again as usual, so is it possible to reinstall windows xp and somehow retain my ubuntu partition?
 
When I read your subject line, i thought you were leaving Ubuntu for good. I came in to try and stop you ;)
 
yes you can re-install Windows XP and leave Ubuntu the way it is. The only problem is that the Windows installation will over-write the MBR. So you will have to re-install the GRUB again. 
 
Its not that trivial, but it can be done !

---

### Post by xtang on 2007-05-30
ok thanx alot guys

lol, yeah i just realized my post title was a bit misleading:D

---

### Post by Inxsible on 2007-05-30
What the hell !!!!
 
5 replies even before i finished typing !!
 
Operation OverKill is now complete !!!

---

### Post by deeteesbeard on 2007-05-30
Do you have just one disk, split into two partitions?

It should be possible, in theory. When you boot from the xp cd and start the install process it will detect that you have an existing xp install and ask you if you want to repair it, if you choose 'no' you can then choose which partition you want to install on.

You'll probably need to reinstall grub again afterwards though.

---

### Post by Cypher on 2007-05-30
> **plcdfa said:**
> I'm not fast enough. :)
Me neither..but then Taurus always seem to be able to beat me..:)

---

### Post by deeteesbeard on 2007-05-30
Yeah, that was quick! :o

Choose you favourite reply ;)

---

### Post by meborc on 2007-05-30
[QUOTE=Cypher]Me neither..but then Taurus always seem to be able to beat me..:)[/QUOTE]
maybe forum mods have an edge over us here?

CONSPIRACY ;)

---

### Post by plcdfa on 2007-05-30
And that's what we call a helpful community. :D

---

### Post by Cypher on 2007-05-30
> **meborc said:**
> maybe forum mods have an edge over us here?

CONSPIRACY ;)
Ohh..I like that theory..maybe they have a mod-favoring delay built into the forums? Like ABC's 5-second delay after the Super Bowl debacle??

I'll go along with that if that means I'm second best to the Mod with my reply..:-D

---

### Post by ronmarley1 on 2007-05-30
Another option for restoring GRUB is the Super Grub Disk.  It's has fixed problems for me twice.  Very easy to use.
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by taurus on 2007-05-30
> **meborc said:**
> maybe forum mods have an edge over us here?

CONSPIRACY ;)

There is no conspiracy here (:-$) and I come in peace!  :wink:

---

