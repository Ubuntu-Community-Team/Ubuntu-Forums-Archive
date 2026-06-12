---
title: "Dual Booting xUbuntu Feisty and OSX (separate hard disks)"
date: 2007-04-18
forum: Apple PPC Users
---

### Post by brunometal on 2007-04-18
Hello , this is my first post here, my name is Bruno I'm XUbuntu and PowerPc user from Brazil.

I have a old MAc G3(green/white) 500mhz, 256 RAM with MacOsX 10.3.9 installed

I Run XUbuntu 7.04 from live CD very well and now i want to install xUbuntu to HD, but My MacOs HD do not have free space..

what I want to do if possible.

I want to put another blank hard disk as master, and macOsX harddisk as slave (ide chanel 1)
my CD-rom is on ide chanel 2

i Know that i can boot MacOsx from slave( ide chanel 1), but my question is..
[B]
If I Install XUbuntu on First(master) hard Disk , ? will Grup manage the boot between xUbuntu(master) and OSX (slavedisk) ?[/B]

What I have to do (if possible) to do that ?  
what lines i have to put in menu.lst to make boot with OSX on secondary hard disk?

thanxs !

---

### Post by grazie on 2007-04-18
Most combinations of New World Mac HW and Open Firmware have no problems booting from primary/secondary IDE, SCSI or an external Firewire. However your B&W PowerMac cannot boot from external Fireware drives. However, primary or secondary IDE booting should be no problemo. The easiest way of correctly setting the boot config is to let the installer do everthing for you, but you do have the option of manual settings up partitions as required. I'd recommend the former option.

---

### Post by brunometal on 2007-04-18
ok, thanxs !!

I will try to let the xUbuntu installer do everything

but if I need to do it manualy , what I have to do?

consider that the macOs partition is hdb5 and Xubuntu partition will be hda1

---

### Post by linear on 2007-04-18
You'll need to edit yaboot.conf (PPC does not use Grub).

You can find some instructions in the wiki, [here]("https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot").

---

### Post by brunometal on 2007-04-18
Thank you !!

Everything works fine with yaboot !!

:)

---

