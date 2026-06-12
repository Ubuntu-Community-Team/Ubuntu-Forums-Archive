---
title: "Installing Windows over Ubuntu"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2007-05-28
Cheers,

I have been using Ubuntu full time on my Home PC since October of last year, and I am very impressed with it.
But recently I got a project that requires me to work on Windows, unfortunately the Client requires a full Windows implementation so I cant use the knowledge I have garnered in linux, which is a pity really.

My question now is, will it be posible for me to install Windows and dual boot it with Ubuntu without messing with my existing Ubuntu setup? Yes, I did tried VMware and VirtualBox, but the performance is just disappointing.
Or do I have to re-install Ubuntu?

Thanks.

---

### Post by mikewhatever on 2007-05-28
It is possible to dual boot if you have sufficient free disk space to create a partition for Windows. Just resize one of the existing ones. You do not have to reinstall Ubuntu, but will have to reinstall Grub to the MBR and then manually add an entry for Windows to the menu. [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

The thread title indicates you want to remove Ubuntu and install Windows.

---

### Post by ugm6hr on 2007-05-28
Depends on which version of Windows too.  If Vista, then EasyBCD is simpler than reinstalling GRUB to MBR.

Probably sensible to use fat32 for the Windows partition too.  I know ntfs-3g is out there, and I plumped for NTFS with my dual-boot, but I'm forever frightened it'll make a mess of my Windows partition!

---

### Post by delphiguy on 2007-05-28
Thanks for the info.  I'll check that out as soon as I receive my copy of Windows as I dont have a licensed copy of Windows.  As for which Windows? I'm guessing that they'll be providing with Vista, just dont know which Vista.

I have 5 HD on my system, 4Sata and 1IDE all of them are formatted as ext3, the IDE is my boot drive at the moment.  What Im planning to do is that maybe dual boot from the IDE and just leave all the remaining HD to ext3 because from what I understand there is a plugin or driver in Windows that will allow it to read ext3 formatted HD, whether it is safe for me to do that I dont know.

---

### Post by ugm6hr on 2007-05-28
> **delphiguy said:**
>  What Im planning to do is that maybe dual boot from the IDE and just leave all the remaining HD to ext3 because from what I understand there is a plugin or driver in Windows that will allow it to read ext3 formatted HD, whether it is safe for me to do that I dont know.

It should be fine:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Also - EasyBCD:
[http://neosmart.net/software.php](http://neosmart.net/software.php)

---

### Post by Computer Guru on 2007-05-28
If you are looking to READ only, IFS is safe. But if you want to read and write, you'll have to use the other Ext2FS for Windows, **Which, despite their claims, is NOT Vista safe, and results BSODs.**
 
And yeah, EasyBCD should be able to do the trick with just one click :)

---

### Post by delphiguy on 2007-05-28
Another question.  My boot drive is 100GB there is where my Ubuntu is installed.  And theres plenty of free space there because I store all my files in another harddrive.  So I wish to use 50GB of it for Windows, is there 
a safe way for me to resize my existing partition without affecting my Ubuntu?  Is there some kind of tool that will allow me to do this? 

Thanks

---

### Post by mikewhatever on 2007-05-29
Gparted Live CD [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

