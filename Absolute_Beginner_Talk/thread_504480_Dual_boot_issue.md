---
title: "Dual boot issue"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by rojer on 2007-07-19
Hi,

I am running win XP on 1 Sata drive.

I installed ubuntu onto second ide drive with the sata drive disconnected.

All installed ok started having some fun.  I then reconnected the sata drive.  On boot up it went direct into ubuntu.  On the next boot up it went direct into XP (  and ever since).

I went into bios settings to change boot order but all I can choose is Hard drive or CD.  I then tried F12 on startup and still can only choose hard drive.

From windows I cannot see the Ubuntu drive (ithink this is normal) bios does see the drive.

My aim is to boot normally into windows (for other users) and when I want I can choose to boot ubuntu.

Any help would be appreciated. 

Thanks in advance

---

### Post by mlentink on 2007-07-19
Is there any particular reason why you disconnected the sata drive with windows?

You see, when you install ubuntu form the live-cd, the installer gives you a choice where you want to install ubuntu, en then sets it up exactly as you want it, i.e. with a menu on boot-up that allows you to choose between  OSs.
In this case, i assume your sata drive is the primary drive in the system, there is a MBR (Master Boot Record) which point to a bootlaoder with Windows only, since the ubuntu installer never could write to it. 

My first instinct would be to reinstall ubuntu with the sata-drive attached. But maybe one of the whizzes on this forum knows a smarter/quicker way?

---

### Post by TygerTung on 2007-07-19
I had the same issue then I looked into it a bit more and in the bios there was a hard drive boot order.

Just select the hard drive with linux on it and you will be sweet as!

---

### Post by LaRoza on 2007-07-19
Yes, if you set the computer to boot from Linux first, (switch it in CMOS or switch the drives) you can easily edit grub.

You can, in grub, set Windows as the default.

(I do not have the grub settings available, I am in school)

---

### Post by gn2 on 2007-07-19
Connect both drives and re-install Grub : [http://ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

---

### Post by rojer on 2007-07-20
gn2

Thanks for the advice, I followed the link and did what it told me.  I still have the same problem.

I think what I have done is reinstall grub where it was, but infact I need it to be on the WinXP drive.

Not sure what to change to do this.

---

### Post by mlentink on 2007-07-20
Like I posted earlier, because you disconnected the SATA drive when installing Ubuntu, it, plus GRUB, was installed on your secondary drive. Your SATA-drive is the primary one, and it holds only the MBR with a pointer to XP. If you want to dual boot, you must make sure that GRUB is installed on the MBR of the Windows disk.

My thought was that reinstalling Ubuntu after you had re-attached the SATA drive would be easiest, because that would put GRUB on your windows drive, but perhaps there's a quicker way

Changing the boot order of your drives will not help you, since it would only change the situation to booting the other OS exclusively.

---

### Post by rojer on 2007-07-20
mlentink
After some reading I thought it would be the safest way.

Yes I am looking for a faster way to do it.

But thtanks for the advice, just don't stuff up the win install.

---

