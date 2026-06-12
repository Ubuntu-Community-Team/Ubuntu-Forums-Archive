---
title: "Dual Boot Installation Problems, Please Help"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by geekboy314 on 2008-02-13
I have an old Dell dimension 2400 with a 200gb maxtor in it, with xp pro.  I have the original hard drive from the machine, a 40gb western digital, that i want to put in as a slave and install ubuntu on. I attatched the two correctly on the 80 pin ATA cable, making sure to use the correct jumpers for master (maxtor) and slave (WD).
     At first, everything went well, the 6.o6 cd booted, installation started, saw the 40gb drive.  The partitioner thing started, and it went _really slowly_.  It said it was "looking for file systems", but for the longest time it sat at 0%, then went to 9%, then hung.  I waited about 16 hours (snow day today + yesterday... woohoo)  and still at 9%.  So i closed the installation and shut down, taking out the live cd.
     When i tried to boot up again, i got POST, but afterwards it beeped and and a message came up that said it couldnt find primary drive 0 or primary drive 1.  Before, i had booted windows with the second drive in, and everything was fine, it showed up as G in windows.  So what happened?
     My xp is fine, when i connect the maxtor with the single cable without the WD everything boots perfectly.  When i connect the second drive, i cant even boot from the ubuntu cd.  All i can think of is that  i've completely bricked the WD 40gb or I have a bad master/slave cable.

     Any help would be greatly appreciated!

---

### Post by stalkingwolf on 2008-02-13
I have run across this several times.  In my case it has usually ended up being a HDD "flaking out."
Try plugging the 40gb in by it self as master.  If it still acts the same it is a good bet that it is the drive.
You can also try jumpering it as CS ( cable select).  I have had times when a drive just would not work as slave but worked fine as CS.

Good luck.

---

### Post by Yuki_Nagato on 2008-02-13
I believe one can only install their operating systems onto one master hard drive.  That means you would have to have the 40 Gig hard drive as additional storage space.  There will need to be free space on your Maxtor Hard drive.

---

### Post by geekboy314 on 2008-02-13
So, i plugged the WD 40gb in as master, and still "primary drive 0 not found".  Same with cable select.  Does this mean the drive is bricked?  It spins up, i can hear it.  Is there any way to fix this?

---

### Post by Therion on 2008-02-13
Here's what I suggest you do.

Unplug the power cable from the back of what will be the Slave drive.
Boot from the LiveCD and install Ubuntu.
Get your install updated, and squared away.
Shut down, reconnect the power cable to the Slave drive and reboot.
Immediately pop into your BIOS and check the settings regarding Boot Device Priority and that both drives are being recognized and for what they are (Master is the boot drive, Slave drive is... well... a slave drive).
Make any necessary changes, Save and continue booting.
You should be golden.

---

### Post by geekboy314 on 2008-02-13
What you're saying sounds like installing ubuntu on the 200gb maxtor.  i dont want to touch that drive, except for putting grub in the MBR.

---

### Post by Therion on 2008-02-13
So you have Windows installed on the 200GB Maxtor drive then; and you want to Dual Boot Windows XP and Ubuntu off that one drive... Is that correct?

---

### Post by geekboy314 on 2008-02-13
I have windows on the 200gb Maxtor, and I want to install ubuntu on the 40gb which will be attatched as a slave.  when i attatch the 40gb in any configuration (as master, slave or cable select) the bios sees no drives at all attatched to the system.  I've ruled out bad cables.  Is my 40gb drive bricked?

---

### Post by Ac_David on 2008-02-13
I would say you also want to make sure that Windows gets installed first before you install ubuntu. It will make it easier to configure a dual boot later on.

---

### Post by geekboy314 on 2008-02-13
Windows is already installed on the 200gb maxtor.  I just want to know what happened to the 40gb drive.

---

### Post by Therion on 2008-02-13
Okay, there are two issues here:

**1.  Dual Booting.**
Dual booting on two different physical drives is going to be a pain.  If the "slave" drive has an OS on it, it's not really a "slave" is it?  Your best bet for dual booting is to install Windows and then install Ubuntu on the *same drive*, letting GRUB overwrite the MBR so it can handle the dual booting scenario.

**2.  The 40GB Slave: Whiskey, Tango, Foxtrot?!**
Unplug the power cable from the Boot drive.  Plug in the "missing" 40GB drive and set it up as the Master drive for now, both via the jumper and the IDE cable.  Restart the PC and enter the BIOS.  Is the drive being recognized in the BIOS?  If it is, your drive should be fine.  If not, then yes, I would have to say it's a doorstop.

---

