---
title: "GrubEd with Vista/ubuntu ?"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Milt888 on 2007-03-04
Has anyone used GrubEd with Vista and Ubuntu?
It works great with XP/Ubuntu. I have Vista on another computer,(hda), and need to put 6.10 on the same machine, on it's own HDD; ie. hdb.
From what I've read, I gather that grub will overwrite the Vista MBR even though the're on different drives. Is this correct? What I'm after is to dual boot Vista and Ubuntu using GrubEd if possible. Great little prog.

---

### Post by Ek0nomik on 2007-03-04
I don't have a lot of experience with GRUB, but from my understanding, so long as you install Windows first, and than Ubuntu, you should be ok.  If you do it the other way around, Windows will overwrite the MBR.

---

### Post by Milt888 on 2007-03-04
Windows is already installed, but I thought that grub would overwrite the Vista MBR. But I really know very little about Linux so...

---

### Post by Tomosaur on 2007-03-04
Vista will overwrite the master boot record - there's no way around it. You should install Vista, then re-install grub. If it's a new machine, then install Vista, then install Ubuntu.

GrubEd is only an editor for Grub - it does not monitor the operating systems installed on your machine. 

Once Vista is installed, you need to boot from the Ubuntu LiveCD, and reinstall grub. Grub should detect that Vista is installed and add an option to boot into it.

---

### Post by Milt888 on 2007-03-04
O.K. I think I'm straight now Tomosaur. It's a new machine with Vista already installed.
As I said, I want to put ubuntu on the second HDD, so when grub is installed with ubuntu, it should see Vista, right?
Thanks for the info. and thanks for that great little GrubEd.

---

### Post by Tomosaur on 2007-03-04
Yep, Grub should see Vista and add it to the grub menu :)

---

### Post by puccaso on 2007-03-10
but because vista isnt like xp in any respect now in regrads to booting.

there is no boot.ini
and extra's like winload etc..

i heard that if u grub over the mbr,
vista wont boot.
because it requires complete control over its partition (has to be active) and the mbr..


i have been stuck with vista because of this

have you had any luck?

---

