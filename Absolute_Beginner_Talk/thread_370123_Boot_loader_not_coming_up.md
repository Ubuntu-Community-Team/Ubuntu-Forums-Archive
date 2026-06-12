---
title: "Boot loader not coming up"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Thrasonic on 2007-02-25
I've successfully installed Ubuntu onto a PATA drive.  Before installing I had a SATA drive with XP installed.  My idea was to dual boot and put Ubuntu on on the PATA drive while leaving my XP installation alone.  I ended up having to use the alternative install CD and it finished and said I needed to remove the CD and reboot the computer, at which time a boot loader is supposed to give me options for booting.  Well, the PC rebooted and it went straight into XP.  How do I get the boot loader to work so I can choose between operating systems?

---

### Post by taurus on 2007-02-25
Did you install GRUB to MBR, usually /dev/hda?

---

### Post by Thrasonic on 2007-02-25
It's hard to say.  The installation said that it was going to do that so I assume so.  Before installing Ubuntu XP booted off of a lone SATA drive.  I installed the PATA drive along side the existing SATA drive and the installation said it was going to install the boot loader.  the installation recognized the XP installation and recommended installing the boot loader and I said yes.  Is there some way to check this without having to disconnect the SATA drive or something?

---

### Post by taurus on 2007-02-25
How did you set the jumper on the back of your PATA?  Did you set it at a master drive or a slave drive?

---

### Post by Thrasonic on 2007-02-25
Not entirely sure.  I believe I set it up as master on its IDE controller.  I can't remember if it's on the IDE controller by itself or not.  I have 2 IDE deevices now - the hard drive and a DVD RW drive.  How would you set this up knowing about the SATA drive.

---

### Post by taurus on 2007-02-25
If you connect your PATA drive to the same ribbon cable with your CD and your CD is bootable, then I think your PATA harddrive is set to slave.  Does your PATA drive uses the middle connection of the ribbon cable?

I guess you have to install GRUB to the MBR of your SATA drive then, /dev/sda.

---

### Post by Thrasonic on 2007-02-25
How do I install GRUB to the MBR of my SATA drive?

---

### Post by taurus on 2007-02-25
When you get to the screen regarding bootloader, it will ask you where you want to install it.  You can either use the default which is usually /dev/hda but in your case, you can't install GRUB on a slave drive.  Therefore, you would tell it to install to /dev/sda.

---

### Post by Thrasonic on 2007-02-25
Perfect.  So to be clear I need to install Ubuntu again and when it comes to loading the GRUB tell it to install to /dev/sda, right?

---

### Post by Thrasonic on 2007-02-25
bump

---

### Post by Thrasonic on 2007-02-25
Is there a way to install the GRUB from XP?  That way I won't have to go through the Ubuntu install again...

---

### Post by Thrasonic on 2007-02-25
Okay, I reinstalled Ubuntu and when it got to the last page where it detected XP and offered to install GRUB it didn't give me the option of telling it where to install the boot loader.  It only gave the option of installing GRUB on hda.  Is there some other way of installing GRUB or do I need to figure out something else?

---

### Post by confused57 on 2007-02-25
> **Thrasonic said:**
> Okay, I reinstalled Ubuntu and when it got to the last page where it detected XP and offered to install GRUB it didn't give me the option of telling it where to install the boot loader.  It only gave the option of installing GRUB on hda.  Is there some other way of installing GRUB or do I need to figure out something else?

Can you boot Ubuntu with hda selected as the first booted hard drive in bios?

---

### Post by Thrasonic on 2007-02-25
Yes, I can!  You're brilliant.  Thanks.  I can now boot into it.

---

