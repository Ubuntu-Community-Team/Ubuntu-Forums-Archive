---
title: "Need Help..almost ther"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by KimoSaber on 2007-12-19
Upgraded to new computer. Tried various Live CD's with no luck. Found out problem. I had to go to the BIOS, loaded default BIOS. I then enable my USB keyboard/mouse. 

However, I tried installing Ubuntu in IDE drive. I'm trying to install Ubuntu with two drive system. Primary drive is SATA. Second drive is IDE. It's master with CD/DVD slave. I will probably have to go to BIOS on bootup an select IDE(Ubuntu) drive as first priorty for it to work. I understand that it's almost impossible to get it to work SATA/IDE setup.  

SATA drive is recognized as SCS13 (0,0,0) sda-500.1GB ATA.
IDE drive is recognized as SCS17 (0,0,0) sdb-61.7 GB ATA.

I have selected SCS17 and created 8 GB swap file and 42 GB mount partition. The problem I having is when selecting Bootloder. It wants to install Grub loader in (hdo).

Which drive is that SATA or IDE? I don't want to mess with the SATA drive. I want to install Grub  loader in second IDE drive (SCS17).

Do I install Grub loader in (hd1) for IDE (SCS17) drive?

Thank you for you  help.

---

### Post by macogw on 2007-12-19
hd0 = sda
hd1 = sdb
I believe

---

### Post by Hospadar on 2007-12-19
that's probably what you want to do.  If it doesn't work, you can always just reinstall and put it in the other drive.  also if you are really worried, you could just unplug the sata drive during installation, then plug it in after you install (while the computer is off).  That's what I always do, it's a little extra work, but works every time.

---

### Post by KimoSaber on 2007-12-19
Macgow, I don't want to make a mistake. I don't want to mess up the Vista Bootloader. I'm running XP/Vista on the SATA drive. I'm using right now the Ubuntu Live CD. Is there a command that I can type in the terminal?
 
Thanks.

---

### Post by perlluver on 2007-12-19
hdo = ide hard drive
sda = Sata or Scsi Disk.

But as above poster stated, unplug the SATA when in doubt.

---

### Post by KimoSaber on 2007-12-19
I will unplug the SATA drive. The SATA drive is recognized in the Ubuntu Install as SCS13 (0,0,0) Sda. The IDE drive is recognized as SCS17 (0,0,) sdb). 

I was hoping that Ubuntu would recognize the SATA drive on the Grub loader on the IDE drive. It would give me an option to boot from. I want it to try it without uplugging it for that reason.

Thanks.

---

### Post by KimoSaber on 2007-12-19
I unplug the SATA drive and it didn't work. I went to BIOS and set CD/DVD primary. The Ubuntu disk didn't boot up. The screen stayed frozen on CD/DVD prompt.

I had to connect the SATA drive back. I had tried twice for my computer to load up Ubuntu.

Any ideas?

---

### Post by KimoSaber on 2007-12-20
I'm a little bit confused. Why Ubuntu recognizes the IDE drive as sdb. The SATA drive as sda.
Why is IDE=Hdo and Sda=SATA? Therefore Hdo should be the IDE drive?:confused:

---

