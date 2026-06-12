---
title: "slight hang up in ubuntu install on g3"
date: 2005-01-23
forum: Apple PPC Users
---

### Post by questionasker on 2005-01-23
ive followed installonoldworldmacs FAQ very close, and i think ive done everything right.

but when i get to the part about copying my vmlinux and ramdisk from /boot to the mac harddrive, i get a

    code:

cp: cannot create regular file [link to selected partition

    code:

no such file or directory



anyone know what to do? it is rather annoying not havin hfs support for mount. grrr.....

thanks for any help.

---

### Post by questionasker on 2005-01-25
did i not give enough info?
or is there just no1 available that has the level of expertise needed for such a task :P

---

### Post by DirtDawg on 2005-01-25
If I'm not mistaken, Ubuntu is for New World Macs only. Apparently you found an instillation guide for oldworld? Anyway, here's another thread from someone with the same problem:
[http://www.ubuntuforums.org/showthread.php?t=12137](http://www.ubuntuforums.org/showthread.php?t=12137)
Sorry I'm not too much help (I'm a semi-n00b), but your thread looked lonely.   :D   
Good Luck.

---

### Post by tonyB on 2005-01-25
[QUOTE=questionasker]did i not give enough info?
or is there just no1 available that has the level of expertise needed for such a task :P[/QUOTE]

Well, I don't have any expertise, but ...  I'm just starting to try to install on an oldWorld G3 myself, and I'm a little surprised to hear claims it's not supported.  Here is an address that discusses doing exactly that:

 [https://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs](https://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs)

If I understand your question, the answer should be about half-way down the page.

Good luck.

tony

---

### Post by DirtDawg on 2005-01-25
[QUOTE=tonyB]Well, I don't have any expertise, but ...  I'm just starting to try to install on an oldWorld G3 myself, and I'm a little surprised to hear claims it's not supported.  Here is an address that discusses doing exactly that:

 [https://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs](https://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs)

tony[/QUOTE]

Right on! Glad to hear "old-skool" Macs work with Ubuntu as well. Sometimes you gotta love being wrong.  :D

---

### Post by questionasker on 2005-01-25
[QUOTE=DirtDawg]Right on! Glad to hear "old-skool" Macs work with Ubuntu as well. Sometimes you gotta love being wrong.  :D[/QUOTE]
 well, my old-school mac doesnt seem to wanna run ubuntu...
==
yeah, thats the faq im folloeing. everything goes good untill im supposed to copy the files...

---

### Post by farruinn on 2005-01-25
Yes, Ubuntu very much works on OldWorld macs =)

Sounds like you haven't mounted the mac partition.  Perhaps you haven't chroot'd correctly?  If you have, make sure you mount the correct hfs partition and that you're copying to that partition.  Could you reply with more info perhaps?

~Nathan

---

### Post by questionasker on 2005-01-26
[QUOTE=farruinn]Yes, Ubuntu very much works on OldWorld macs =)

Sounds like you haven't mounted the mac partition.  Perhaps you haven't chroot'd correctly?  If you have, make sure you mount the correct hfs partition and that you're copying to that partition.  Could you reply with more info perhaps?

~Nathan[/QUOTE]
 ok, ill try to give more info.
==

my hd (IDE, i dont know why, @ HDC) partitions:
hdc1->
|------> 
|------> 
------->
hdc5-> all regular mac stuff, i dont know what.
hdc6-> primary mac partition, hfs filesystem, 350MB
hdc7-> / partition, reiserfs filesystem, 3.5GB
hdc8-> swap partition, 300MB

---

### Post by questionasker on 2005-01-26
farruinn, in another post you said something about runnin ubuntu on a g3.
would you tell me what you did to copy the files?

---

### Post by farruinn on 2005-01-26
The method I used was after installing I used the Debian boot floppies to get into a shell.  Though these floppies are a bit dated, the kernel at least has hfs support.  I believe I posted details and a link to the boot floppies on [http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs](http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs)

Actually, today I've been exploring the install CD because according to some developers/maintainers I've spoken with, the install CD should have hfs support which would be grand.  As of yet I've had no luck, but I'll be sure to post my findings.

~Nathan

---

### Post by lubod on 2005-01-27
To questionasker:

Nice to hear Ubuntu can be installed on Old World Macs, I have it on a New World Mac now but have a couple of older Macs to play with.

You may have been tripped up by the stream of consciousness style of the wiki entry
What he says, near as I can tell:

First copy the files from his tarball to the Mac partition BEFORE beginning the install!

Then allow the installer to finish as usual, except loading some kernel modules for ethernet/scsi as needed. Most Macs of the PPC 604 era, 8500 and similar use MESH for onboard SCSI, MACE for ethernet (they are chipset names, acronyms I assume.)

Then reboot into Mac OS, reconfigure miboot/bootx to use the 'normal' kernel and initrd.gz

farruinn: nice idea to use debian boot floppies, I gotta try that when I try beige Macs! Hopefully I can get Quik or similar to work so I don't need a Mac OS partition, hard drive space is at a premium and an all Linux setup would be nice :)

---

### Post by questionasker on 2005-01-28
but his kernel and such wouldnt work on my comp would it, if we had diff hardware, no?

---

