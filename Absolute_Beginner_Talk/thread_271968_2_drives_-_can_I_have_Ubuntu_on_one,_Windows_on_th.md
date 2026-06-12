---
title: "2 drives - can I have Ubuntu on one, Windows on the other"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Eugene Carvalho on 2006-10-05
I have Windows on one SATA drive.  Can I remove the drive temporarily (unplug it) from the Motherboard, then install Ubuntu on the other drive.   

What I would like is to be able to chose which system boots by selecting the preferred drive in the BIOS at startup.       

If I leave the two drives in place when I install Ubuntu then I have to choose Windows each time i boot.     and      Will the system partitioning software be able to see the  other drive if I do this?:

---

### Post by Kateikyoushi on 2006-10-05
Yes you can do it the way you wrote.

Ubuntu installs a bootloader onto your system. When you start the computer you can select which OS to boot.

With two hard drives it seems to install the boot loader to the pata drive.
You can also disconnect the sata one install ubuntu and add the windows drive to the boot menu, it takes only a minute.

---

### Post by bulldog on 2006-10-05
Yep you can do so,but you have to manual add the windows partitions to your fstab.

If you have the possebillity to set the drive where you want to install Ubuntu as the master boot device and your windows as secundary it would be easier though.

---

### Post by geekchic9 on 2006-10-05
I don't know about SATA drives. I have 2 PATA drives, one with Windows and one with GNU/Linux. With Windows already on the first hard drive, I installed Ubuntu on the second drive, and Ubuntu automagically configured itself to be the default OS on the computer. If I choose to do so in GRUB, I can always reboot and start Windows when necessary. Of course, I don't know about SATA drives, so YMMV. Good luck.

---

### Post by bulldog on 2006-10-05
> **geekchic9 said:**
> I don't know about SATA drives. I have 2 PATA drives, one with Windows and one with GNU/Linux. With Windows already on the first hard drive, I installed Ubuntu on the second drive, and Ubuntu automagically configured itself to be the default OS on the computer. If I choose to do so in GRUB, I can always reboot and start Windows when necessary. Of course, I don't know about SATA drives, so YMMV. Good luck.

You can decide by yourself which OS will boot by default.
It's a minor change in your menu.lst.

---

### Post by geekchic9 on 2006-10-05
> **bulldog said:**
> You can decide by yourself which OS will boot by default.
It's a minor change in your menu.lst.

Thanks, I didn't know that--that information may come in handy one day.

---

### Post by bulldog on 2006-10-05
> **geekchic9 said:**
> Thanks, I didn't know that--that information may come in handy one day.

Go to this section and alter the default 0 in what you want.
To find your number start counting your menu.lst entry's starting with zero.

0,1,2,3 and so on till you reach the desired boot candidate.

This number you set instead of default 0

# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

---

### Post by Bartender on 2006-10-05
I woulda thought that if you unplugged your Windows drive and installed Ub to a second drive, then put the first drive back in, you'd have trouble getting to Ub.  Assume there must be some manual changes made to grub? Can anyone point me to a guide for this?  I've been thinking about using two separate drives (one Win, one Ub) and wondering what would be the best and safest way...

---

### Post by bulldog on 2006-10-05
> **Bartender said:**
> I woulda thought that if you unplugged your Windows drive and installed Ub to a second drive, then put the first drive back in, you'd have trouble getting to Ub.  Assume there must be some manual changes made to grub? Can anyone point me to a guide for this?  I've been thinking about using two separate drives (one Win, one Ub) and wondering what would be the best and safest way...

Well I have one IDE and a Sata disk.

I have windows on the IDE drive and Grub was original here located.

What I did was to make my sata disk master boot device and installed Grub in this MBR and restored the windows bootloader with the recovery console.

So I can boot windows by grub or by altering the boot order in BIOS.

Windows will always boot even without Grub and Ubuntu will always boot by Grub or in case of disaster,with the live cd.

---

### Post by Bartender on 2006-10-05
So, bulldog -
If you were starting out fresh, you'd just install Windows to HDD #1, plug in HDD #2, go into BIOS, set the optical drive as boot, install Linux to HDD #2, then go back into BIOS and set HDD #2 as first boot device? 
You'd have to leave HDD #1 in place during Linux install so that grub saw the Windows drive, right?

---

### Post by gn2 on 2006-10-05
> **Bartender said:**
> I woulda thought that if you unplugged your Windows drive and installed Ub to a second drive, then put the first drive back in, you'd have trouble getting to Ub.  Assume there must be some manual changes made to grub? Can anyone point me to a guide for this?  I've been thinking about using two separate drives (one Win, one Ub) and wondering what would be the best and safest way...

Leave Windows drive as master, fit Ubuntu drive as slave.

Disconnect power to Windows drive.

Install Ubuntu and Grub to slave drive.

Re-connect power to Windows drive.

At boot time press F8 (or other key depending on PC model) to bring up boot device list

Select desired drive and boot.

You can set default OS by rearranging the BIOS boot order to suit.

Remember to have PC switched off when connecting/disconnecting drives, and take anti-static precautions of not working in carpeted area and touch chassis with both hands before handling components.

---

### Post by bulldog on 2006-10-05
> **Bartender said:**
> So, bulldog -
If you were starting out fresh, you'd just install Windows to HDD #1, plug in HDD #2, go into BIOS, set the optical drive as boot, install Linux to HDD #2, then go back into BIOS and set HDD #2 as first boot device? 
You'd have to leave HDD #1 in place during Linux install so that grub saw the Windows drive, right?

Not quite,Sata is also a master drive.

I go to the bios and change the bootorder to what I want and install what ever I want.

Then go to the bios and alter it again.

Never had to unplug a hdd.:D 

I install GRUB where the Ubuntu install is and leave the windows bootloader where it is.
Than alter the menu.lst so windows will boot even if it's not at the first boot device,by mapping ther hdd's.

---

### Post by Eugene Carvalho on 2006-10-05
Note to Bartender:

You are right.  If you install Ubu to drive 2 without Drive 1 (windows) in place, then plug drive 1 back in and try booting to Ubu the  boot fails.

Drive 1 can stilll boot windows, though.

What I want is Windows on 1, Ubuntu on 2, and the default boot on 1.  Both drives are SATA. 

It looks like I have to install Ubu with windows present, then change the boot preference.  What is the exact sequence to do this?

---

### Post by Kateikyoushi on 2006-10-05
Select in bios to boot from the ubuntu hard drive.
This will boot grub from ubuntu's hdd, then you can modify the grub menu to boot windows by default.

---

### Post by Mr Doom Bringer on 2006-10-05
I have two HDDs in my comp, and I attempted to install on just one of them, the slave which had practically nothing on it anyway, and inadvertantly installed it onto my Windows disk. It partitioned the free space on it, and everything went along fine. When I start up the computer in DOS it saks me which OS I would like to run, Ubuntu, Ubuntu in debug, some other Linux thing or Windows. Windows works fine, and I didn't loose any of my data for it.:-D

---

### Post by Mr Pink57 on 2006-10-05
> **bulldog said:**
> Not quite,Sata is also a master drive.

I go to the bios and change the bootorder to what I want and install what ever I want.

Then go to the bios and alter it again.

Never had to unplug a hdd.:D 

I install GRUB where the Ubuntu install is and leave the windows bootloader where it is.
Than alter the menu.lst so windows will boot even if it's not at the first boot device,by mapping ther hdd's.

Sata drives to not have a master/slave there is no need for them.  I would just change the order thru ubuntu in the menu.list as doing it this way seems to be more work then its worth.

I use two sata drives (not in raid) and I just always install winblows first then linux so grub will reconize it.  Also the winblows bootloader dosent reconize linux last I checked.

pink

---

