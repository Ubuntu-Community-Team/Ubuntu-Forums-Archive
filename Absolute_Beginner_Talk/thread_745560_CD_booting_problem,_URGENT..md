---
title: "CD booting problem, URGENT."
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Colex on 2008-04-04
I've downloaded teh ubuntu 7.10, and made an iso copy of da ****.
Than, using partition magic 8.0 i formatted teh XP and the disk, and convert it to ex2. Clean as a baby's ***. 
Than, when i reboot teh comp, the ubuntu cd just doesn't want to boot. The XP's one, on the other hand does (nothing strange here), but i can't install it (also, nothing strange, ex2). 

*Why teh 'buntu do3sn't wnt t0 strt?* :confused:

I suppose, that the problem is linked to the wubi-cdboot.exe file?  :)



P.S. Sorry for the language, just a happy day today.

---

### Post by bubba_169 on 2008-04-04
Did you use the burn image to disc option in your burning software or did you just copy the ISO file to the cd? You need to use the burn image to disc option to make the cd bootable. A big clue, if you did it wrong there will be only 1 file on the cd...

---

### Post by Biggy on 2008-04-04
insert Ubuntu 7.10 CD and boot from Ub Live CD.Click install in desktop and in Ubuntu installation wizard you can create new partition,and install it.

you dont ned to use partition magic.

sorry for my bad english ..

---

### Post by Colex on 2008-04-04
No, i didn't do it.

I'll rewrite the cd in nero, and try to make it bootable. I'll be here in a while.

---

### Post by lavinog on 2008-04-04
> **Colex said:**
> I've downloaded teh ubuntu 7.10, and made an iso copy of da ****.
are you saying you burned the iso to disk?  if so, does this disk not boot?

> 
Than, using partition magic 8.0 i formatted teh XP and the disk, and convert it to ex2. Clean as a baby's ***. 
Than, when i reboot teh comp, the ubuntu cd just doesn't want to boot. The XP's one, on the other hand does (nothing strange here), but i can't install it (also, nothing strange, ex2). 

did you wipe the hd completely with part magic?
the install disk could have done this for you.
the XP install disk boots but wont let you wipe the hd and reinstall?

> 
*Why teh 'buntu do3sn't wnt t0 strt?* :confused:

I suppose, that the problem is linked to the wubi-cdboot.exe file?  :)

I thought wubi was only on 8.04?

what iso did you download?
did you check the md5 sum?
how did you burn the iso?

---

### Post by Colex on 2008-04-04
> **Biggy said:**
> insert Ubuntu 7.10 CD and boot from Ub Live CD.Click install in desktop and in Ubuntu installation wizard you can create new partition,and install it.

you dont ned to use partition magic.

sorry for my bad english ..

I know that, first I've installed the ubuntu on NTFS with the XP on the disk. But now the disk is apsolutely clean, and it's ex2, so i can't install the XP.

I guess that the problem is in the bootable cd-thing.

---

### Post by lavinog on 2008-04-04
> **Colex said:**
> I know that, first I've installed the ubuntu on NTFS with the XP on the disk. But now the disk is apsolutely clean, and it's ex2, so i can't install the XP.

I guess that the problem is in the bootable cd-thing.

the windows xp disk should give you the option to erase the ext2 partition and reformat as ntfs.
You have to use the full version and not just the upgrade.
If you are using one of those computers that use a recovery partition instead of a disk then it is possible that you lost your chance to recover windows.

---

### Post by Colex on 2008-04-04
I don't want to recover XP, I'm fine with ubuntu. 

Now, how to make a bootable ubuntu 7.10 cd?

If the question is already been asked here, than please give me a hyperlink.

---

### Post by Colex on 2008-04-04
[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

Ubuntu 7.10 CD finished.

i386  (P4 1.6ghz northwood)
winmd5sum
wrote by infra recorder at 16x (52x max)
Bios - CD booting first

Everything by the book, every detail controlled, and still, when i try to start the ubuntu cd, "PRESS ANY KEY TO REBOOT SYSTEM". (XP cd does work, floppy does work, so no smartbootmanager here).

Please help me, I'm desperate!

---

### Post by bubba_169 on 2008-04-05
Are you using the alternate cd? If not try that as it might be a compatability issue...

---

### Post by mgranet on 2008-04-05
You still appear to be burning the ISO file to disk, not the image. There will usually be an option to burn to disk as image, that is what you want to do. This will automatically make the CD bootable.

---

### Post by Colex on 2008-04-05
My CD has quite a lot of files on it. I didn't burn the iso on. I was using Infra record.

---

### Post by bubba_169 on 2008-04-05
If you are still having problems try installing this on your windows machine:

 [http://isorecorder.alexfeinman.com/isorecorder.htm]("http://isorecorder.alexfeinman.com/isorecorder.htm")

After installing this, you should be able to just right click on the ISO file and then choose copy to CD. This will make it much simpler...

EDIT: If your CD has lots of files on it then ignore this message :)

---

### Post by Colex on 2008-04-05
The only way i could install ubuntu was when i had XP on. NTFS partition.

Despite i was really pleased to install ubuntu from a blank HDD, the only way i see is thru XP.

:(

---

