---
title: "New user -No Grub and drive disappeared"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by emsai on 2007-10-06
My system
Win XP 
AMD Athlon 64  4000
Asus/Nvidia 6800 GPU
Corsair 2gb
WD 40 gb ide = c Drive
WE 74 Raptor = d Drive

Problem
Loaded Ubuntu onto C drive; can view it when I boot to Ubuntu from the ubuntu CD.  
When I turn off the machine and reboot (CD drive empty), it boots directly to win xp on my d drive, as it usually does, but c drive does not show up on My Computer.  It does show up via Programs, acccessories, system tools.   I cannot access c drive.  I get no Grub from which to select ubuntu or win xp.  

Thanks

Ed

---

### Post by overdrank on 2007-10-06
> **emsai said:**
> My system
Win XP 
AMD Athlon 64  4000
Asus/Nvidia 6800 GPU
Corsair 2gb
WD 40 gb ide = c Drive
WE 74 Raptor = d Drive

Problem
Loaded Ubuntu onto C drive; can view it when I boot to Ubuntu from the ubuntu CD.  
When I turn off the machine and reboot (CD drive empty), it boots directly to win xp on my d drive, as it usually does, but c drive does not show up on My Computer.  It does show up via Programs, acccessories, system tools.   I cannot access c drive.  I get no Grub from which to select ubuntu or win xp.  

Thanks

Ed

Hi maybe this links will help
You may try to reinstall the grub
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
And if you have to edit the grub this link will help
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
Hope this helps and good luck!

---

### Post by mgmiller on 2007-10-06
You will probably need to tell your BIOS to change the boot order so it sees your Ubuntu drive as the first boot option.  

Once you do that, grub should then give you the choice of which OS to start, assuming when you installed Ubuntu, you told it not to disturb the windows disk.  It should have seen it, though and the migration assistant should have brought in various settings, etc.  

The reason My Computer in windows can't see the Ubuntu drive is because it is now formatted in the EXT3 file system, which Windows doesn't support natively.  It can be seen in your system tools just as any new unformatted drive would be.  

Don't use system tools to mess with the drive or you will break Ubuntu.  
You can add EXT2/3 capabilities to windows by adding a driver.  It's called ext2fs.sys and you get it here:
[http://www.fs-driver.org/]("http://www.fs-driver.org/")
Be careful using this as I have heard it can mess up Linux drives if you use it to write to the drive and something in windows freezes.

---

### Post by emsai on 2007-10-11
Thanks for the response.

My boot sequence is:  CD, Hard Drive, Hard Drive, and  Removable media.  The identity of the boot-up hard drive is not specified.  I have two hard disks:  D contains WinXPsp2 and C contains Ubuntu.

D drive is the one I boot from.  C drive is shown as a slave to my CD drive under the MAIN tab in my bios.  D drive is shown as the Master SCSI drive.

I think you are right - the solution is in the bios.  Or it may be in the way the C drive is connected to the mobo, as a slave to the optical (CD) drive.  Probably both.

Is it possible to get Grub (where?) and install it on D drive, the WinXP boot-up drive, and use it from there to switch between D &C (WinXP and Ubuntu?)   

I am about mid to low-mid in tech capabilities.  I assembled my current PC from components, and installed a new hard drive the OS and all software, so I do have a basic understanding of the system.  I also back up (Acronis 10) religiously.  Suggestions?

---

### Post by mgmiller on 2007-10-11
I would change things around a bit.  I don't like having hard drives slaved to optical drives, it slows them down.  (Don't forget to change the jumpers if you move the drive)  
If possible, have the hard drive on its own connector to the motherboard or slaved to another hard drive.
Somewhere in your BIOS you will find the area where you specify the boot order.  You should be able to change the order of the booting hard drives from there.

Failing that, if they are both pata drives, just swap the cables so the ubuntu drive is connected where your windows drive is now.  Since you are telling me D is master scsi, it makes me think maybe it is a sata drive, so you may not be able to do that.

Please tell me the kinds of drives, parallel or serial and how many and what kinds of mobo connectors there are for them.

---

