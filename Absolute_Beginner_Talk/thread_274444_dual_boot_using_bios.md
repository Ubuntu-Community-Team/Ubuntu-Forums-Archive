---
title: "dual boot using bios"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by wendon on 2006-10-09
My system have two sata drives.The first have xp installed,i would like to install dapper on the second drive.I will be installing  grub on the second drive,i dont want to mess with my mbr.Can i select which OS to boot using my bios setting.I am a newbie

---

### Post by CatKiller on 2006-10-09
Yes you can.

To be safe, though, remove the Windows drive before you install Ubuntu. Only put that drive back in once Ubuntu can boot itself.

You want to keep each operating system as unaware of the other as you can.

---

### Post by gn2 on 2006-10-10
> **wendon said:**
> My system have two sata drives.The first have xp installed,i would like to install dapper on the second drive.I will be installing  grub on the second drive,i dont want to mess with my mbr.Can i select which OS to boot using my bios setting.I am a newbie

Just disconnect the power lead to the windows drive when you install Ubuntu on second drive.

Change your BIOS boot order so that the desired default OS drive is first in the boot order, then there should be a button press that lists your boot devices at boot time, when you want to boot other OS (on mine it's F8 for example)

Access to/from both drives can be configured later if desired.

---

### Post by wendon on 2006-10-10
Where should i put grub

---

### Post by gn2 on 2006-10-10
> **wendon said:**
> Where should i put grub

On the same drive as Ubuntu.

You must make sure the Windows drive is not powered, so you can just accept the default install settings if you wish.

Effectively you are creating a separate single boot system.

Benefit of this is no corruption of MBR on Windows drive.

With this solution, each OS is booted by it's own loader.

The choice of which to boot is done by selecting the drive to boot from the list of devices given at boot time by pressing F8 (or whatever key depending on BIOS version)

This completely removes the difficulties associated with having two OS's on the one hard drive. 
E.G. if Windows falls ill with a nasty infection, you can re-install it without affecting Ubuntu drive in any way. (remember to disconnect Ubuntu drive though)
Don't have to edit Grub for changes during updates.
Easier to remove OS if you want a change.

---

### Post by willcox on 2006-10-30
ok  asumming that I have unpowered the windoze drive, should I have to connect the jumper of the ubuntu's drive as a master or slave?  and once installed ubuntu, what drive is going to be the master?

---

### Post by confused57 on 2006-10-30
> **willcox said:**
> ok  asumming that I have unpowered the windoze drive, should I have to connect the jumper of the ubuntu's drive as a master or slave?  and once installed ubuntu, what drive is going to be the master?
Here's another option for dualbooting with 2 hd's:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

