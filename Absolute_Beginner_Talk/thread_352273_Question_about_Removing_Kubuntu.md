---
title: "Question about Removing Kubuntu"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Dimka on 2007-02-03
hi.
I always wanted to move to Linux and i was suggested to try the Ubuntu dist.
well, genome looks very bad and i found the KDE version...

I Installed it and found out that i can't configure my modem (dsl using nic) or connect to the Internet. 

Now since i don't have a use for it, i want to remove linux from my computer.
I've installed it on a separate HDD (not separate partition).

I know that i can just re partition the drive and format it. but there is a minor problem...
Kubuntu installed a boot loader "grub" or something like that. so how do i get rid of it? so the pc will boot into windows instead of showing me the selection?

---

### Post by jordanmthomas on 2007-02-03
Use your Windows XP installation disc to reboot into recovery mode and once logged in, type
```
fixmbr
```
This will install Microsoft's bootloader to the MBR and Grub will be removed.

---

### Post by taux on 2007-02-03
Hi,

I think what you should is this:

1) Set the windows partition as bootable (you can do this using fdisk)
2)

I think grub can be installed in the same partition as linux is or in MBR (master boot record), you might had to select this option during installation. If grub is installed in the same partition as linux formatting entire partition shall do the trick. However if it sits in MBR you have to remove it from there. I don't know how to do it in linux, but in windows i once did it with command

```
fdisk /mbr
```

[http://support.microsoft.com/kb/69013](http://support.microsoft.com/kb/69013)

However make sure that windows partition is bootable, because if not after removing grub you will be staring at blank screen.

When computer has one disk and is booting it first checks the MBR if MBR is empty it searches for bootable partition and boots it. You have 2 HDD so i am not sure how the booting sequence is going then. Maybe Master HDD is checked and then slave HDD?

These are some ideas about removing Kubuntu. Do some more reading, because i am not a pro:)

Good luck

---

### Post by Dimka on 2007-02-03
thanx :-)
that helped me alot...

p.s. in Israeli forum they said that I should have typed "pppoeconf" in the terminal and that should have started the Adsl connection wizard... can anyone confirm? (I might not quit yet...)

---

