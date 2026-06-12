---
title: "Install Ubuntu now, add Windows later?"
date: 2007-06-11
forum: Apple Intel Users
---

### Post by Torajima on 2007-06-11
I want to triple boot, but I haven't had much luck creating a slipstreamed XP disc. So can I partition my drive 3 ways, leave OSX on one, install Ubuntu on another, and just add Windows later? Or does windows have to be installed before Ubuntu?

And can VMware be set up to use an existing Ubuntu partition?

---

### Post by SoggyCornflake on 2007-06-11
> **Torajima said:**
> I want to triple boot, but I haven't had much luck creating a slipstreamed XP disc. So can I partition my drive 3 ways, leave OSX on one, install Ubuntu on another, and just add Windows later? Or does windows have to be installed before Ubuntu?

And can VMware be set up to use an existing Ubuntu partition?

Microsoft OSes tend to not play nice with other OSes.  Installing XP after installing something else usually means you lose whatever you installed first.

Most Linux Distros have learned to deal with this fact of life.

---

### Post by jackmc on 2007-06-11
what about running windows in VMware? Works well enough for me :)

---

### Post by ronocdh on 2007-06-12
> **jackmc said:**
> what about running windows in VMware? Works well enough for me :)
How is support for 3D acceleration in VMWare? I ask because it is a common reason for virtualization, Parallels has added it to P3, and I personally triple boot solely to game. =)

---

### Post by ronocdh on 2007-06-12
> **SoggyCornflake said:**
> Microsoft OSes tend to not play nice with other OSes.  Installing XP after installing something else usually means you lose whatever you installed first.

Most Linux Distros have learned to deal with this fact of life.
I second this. I believe you should install XP first, then Ubuntu. XP will definitely overwrite your MBR, making it impossible to boot into Ubuntu, and you'll have to set up GRUB again.

---

### Post by kopilo on 2007-06-20
possible if you have two hard drives... simply change the boot order in bios when you go to install windows, and install it on a different hard drive to the linux one... then just swap it back and reinstall grub or lilo.

---

### Post by ronocdh on 2007-06-20
> **kopilo said:**
> possible if you have two hard drives... simply change the boot order in bios when you go to install windows, and install it on a different hard drive to the linux one... then just swap it back and reinstall grub or lilo.
Thank you for the thought, but the Intel Macs do not have BIOS, as they are EFI-based.

---

### Post by Torajima on 2007-06-20
This thread is still going? I installed both XP and Ubuntu on my Mac last week... running fine except for trackpad and external monitor issues (connecting laptop to external monitor crashes x server).

---

### Post by ronocdh on 2007-06-20
> **Torajima said:**
> This thread is still going? I installed both XP and Ubuntu on my Mac last week... running fine except for trackpad and external monitor issues (connecting laptop to external monitor crashes x server).
Search for trackpad problems in this forum. You'll find plenty of hits about Gsynaptics and/or Qsynaptics. I'm sure there's a lot on external monitors, too, but that's more hardware dependent, and so make sure you know which model of Mac the poster is referring to.

---

### Post by kopilo on 2007-06-23
> **ronocdh said:**
> Thank you for the thought, but the Intel Macs do not have BIOS, as they are EFI-based.
*the following is not recommended for anyone with a laptop due to the difficulty of physically doing it*

Ahh sorry, not really a mac person, but maybe it is possible to achieve the same effect by changing the jump pins (manually changing the boot sequence) on the drives. 
OR
Just remove the drive with the ubuntu install when you go to install windows, that way it physically can not think that the missing dive is the boot drive and thus installing on the other drive. However  when you put the other drive back in, I`m not sure which drive the Mac will think is the boot drive, or how that can be set.

Alternatively

Ubuntu can also be installed on a usb stick or external drive, which may be another way of getting around having to install windows first...

---

### Post by ronocdh on 2007-06-23
> **kopilo said:**
> Ahh sorry, not really a mac person
Nobody's perfect.
> maybe it is possible to achieve the same effect by changing the jump pins (manually changing the boot sequence) on the drives.
This is a joke on most models of Macs. These systems aren't designed to be torn apart, for better or for worse.
> OR
Just remove the drive with the ubuntu install when you go to install windows, that way it physically can not think that the missing dive is the boot drive and thus installing on the other drive. However  when you put the other drive back in, I`m not sure which drive the Mac will think is the boot drive, or how that can be set.
OP stated that the triple boot would be performed by partitioning a single drive three ways.
> Ubuntu can also be installed on a usb stick or external drive, which may be another way of getting around having to install windows first...
Macs don't easily boot from USB. Better results with FireWire, perhaps, but mostly only when formatted to HFS+. Search more within this forum for info on booting from external drives with a Mac. It's a pain.

---

