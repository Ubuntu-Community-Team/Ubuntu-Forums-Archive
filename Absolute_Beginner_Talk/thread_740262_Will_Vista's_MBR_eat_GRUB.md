---
title: "Will Vista's MBR eat GRUB?"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2008-03-30
Alright, here's my setup (in terms of drives)...

My board is so ancient it'll only recognize 130gb / partition.  So with my 200gb hard drive, it'll only read 130, then I gotta take the remaining 60 (10gb loss) and allocate it as a different partition.

The 130 is a windows XP system - the new partition I made out of the 60GB I formatted as EXT3 and that's how I'm using Ubuntu - which I use every day.

Now I found a 120gb hard drive in my computer - and it has an old XP partition (last year) - no useful data now, it needs to be formatted.

I wanted to throw vista on it - but due to my sys specs we're not sure if it can handle it - whether it can or can't I don't really care, that's not my issue.  My issue is simply that I don't want to install Vista on that second hard drive, then have it overwrite GRUB with its MBR.

First off, where exactly is GRUB/MBR stored?  I thought it was at the beginning of the partition, but if I have GRUB on one, and a VISTA MBR on the other - since I have 2 SATA hard drives - which one will show up when I boot?

Or say I "upgrade" my XP partition (the 130gb).  How would I stop it from overwriting GRUB, or would I need to let it go then re-install GRUB (which quite simply appears to be a pain in the ***).

I was thinking that if I don't wanna mess w/ the boot things and decide not to put vista on there - I'd try to use the 120gb hd as a disk image backup for my 60gb ubuntu partition.  Though I haven't found a program that would back it up.  I heard rsync is good, but apparently you need to back it up to a different computer - as in it needs another UNIX system to "catch" the image.  Though I'd guess you'd need another linux distro to re "insert" the image anyways, no?

Does anybody have any feedback at all? :-\

---

### Post by Duck2006 on 2008-03-30
If it does you just need to reinstall grub again, or you can load EasyBCD in vista and use it to load ubuntu.

[http://www.freewarefiles.com/EasyBCD_program_21892.html](http://www.freewarefiles.com/EasyBCD_program_21892.html)

---

### Post by Syndacate on 2008-03-31
> **Duck2006 said:**
> If it does you just need to reinstall grub again, or you can load EasyBCD in vista and use it to load ubuntu.

[http://www.freewarefiles.com/EasyBCD_program_21892.html](http://www.freewarefiles.com/EasyBCD_program_21892.html)

You mean use EasyBCD **instead** of GRUB?

---

### Post by prismpirate on 2008-03-31
Vista will eat grub, yes :)

EasyBCD edits the MBR to allow booting of ubuntu of it, although if you want grub you can easily do that from the ubuntu live cd.

A tutorial to dual boot Vista and Ubuntu is shown here, Vista First 
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")

---

### Post by bumanie on 2008-03-31
There are some easybcd tutorials on triple booting vista,xp and ubuntu. Just google 'How to triple boot with easybcd'.

---

