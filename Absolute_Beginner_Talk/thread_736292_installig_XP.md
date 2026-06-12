---
title: "installig XP"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Incite on 2008-03-26
I currently have Gutsy Gib and I want to intall xp as a duel boot but the GRUB boot manager wont read the xp boot disk.

Can I remove the GRUB and replace it with a microsoft friendly Booter?

---

### Post by northern lights on 2008-03-26
That issue should not be related to GRUB whatsoever.

Have you checked your BIOS? I.e. whether the CD drive you're using is set as bootable and first in the order?

---

### Post by stchman on 2008-03-26
> **Incite said:**
> I currently have Gutsy Gib and I want to intall xp as a duel boot but the GRUB boot manager wont read the xp boot disk.

Can I remove the GRUB and replace it with a microsoft friendly Booter?

If you install XP AFTER you install Ubuntu XP will wipe out the boot loader that Ubuntu installed.  You will just need to reinstall grub.  You can do this using the LiveCD.

---

### Post by Incite on 2008-03-26
Well i put in the xp disk and it does not read it at all when i do a install.

---

### Post by iSplicer on 2008-03-26
You need to go to your BIOS, and make sure CD boot is before Hard disk boot. If GRUB is loading, it is booting your hard drive before your cd.

---

### Post by Incite on 2008-03-26
I have cd is 1st on boot order. Also when i put in the xp disk while i am logged onto linux it says 

Invalid mount option when attempting to mount the volume 'UDF Volume'.

---

### Post by drzoo2 on 2008-03-26
Sounds like your XP disk is damaged. Does it work on another PC?

---

### Post by northern lights on 2008-03-26
The fact that Linux can't mount the CD shouldn't be too disturbing - not that I've ever tried to mount a Windows Setup Disc in Ubuntu, but the same error occurs with media burnt in Windows, if you don't choose compatible filesystems.

If your drive is indeed the first boot device, I'm clueless. Have you tried making it the only one?

---

### Post by exWin4eva on 2008-03-26
it won't mount ext3 can't mount the nt file system. IF YOU ARE GOING TO INSTALL XP YOU ARE GOING TO RE-WRITE THE MBR and make your 7.10 un-bootable. you can format your 7.10 partition which will be partition=1 (sda1) then format it with ntfs and re-install your 7.10. to sda2 which will then add your grub back to the mbr giving you your boot and other os choices

---

### Post by Miljet on 2008-03-26
You DO realize that you can't run the XP install from within Ubuntu don't you? You have to reboot with the XP install disk in the drive.

---

### Post by Bölvaður on 2008-03-26
Grub is very Windows friendly, it is totally OS neutral. Windows makes a mess when it is installed and that is a..... <insert ugly words>

When you get Windows running ok click on the url -> [Recovering Ubuntu After Installing Windows URL ]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Incite on 2008-03-26
> **exWin4eva said:**
> it won't mount ext3 can't mount the nt file system. IF YOU ARE GOING TO INSTALL XP YOU ARE GOING TO RE-WRITE THE MBR and make your 7.10 un-bootable. you can format your 7.10 partition which will be partition=1 (sda1) then format it with ntfs and re-install your 7.10. to sda2 which will then add your grub back to the mbr giving you your boot and other os choices

How do i do that

> **Miljet said:**
> You DO realize that you can't run the XP install from within Ubuntu don't you? You have to reboot with the XP install disk in the drive.

I know.

---

### Post by northern lights on 2008-03-26
> **Incite said:**
> [QUOTE=exWin4eva;4593709]it won't mount ext3 can't mount the nt file system. IF YOU ARE GOING TO INSTALL XP YOU ARE GOING TO RE-WRITE THE MBR and make your 7.10 un-bootable. you can format your 7.10 partition which will be partition=1 (sda1) then format it with ntfs and re-install your 7.10. to sda2 which will then add your grub back to the mbr giving you your boot and other os choicesHow do i do that[/QUOTE]
It ain't instructions. "Win4eva" (?!) is simply telling you what Windows would do if you were to manage the disc to boot...

Does it do that on any other comp by the way? You might just have a broken Cd also...

---

### Post by Incite on 2008-03-26
My disk is probably damaged then cause its not booting even in my vista machine.

---

