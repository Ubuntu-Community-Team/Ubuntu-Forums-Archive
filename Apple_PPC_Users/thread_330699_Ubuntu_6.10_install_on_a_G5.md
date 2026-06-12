---
title: "Ubuntu 6.10 install on a G5?"
date: 2007-01-03
forum: Apple PPC Users
---

### Post by GrammatonCleric on 2007-01-03
Hi,

I'm having the hardest time installing 6.10 on a G5.   I am using a the PowerPC version of 6.10.  I'm able to boot off the cd, start the install, accept the auto partition of the drive, go through install and all looks good.  So I select reboot, services shutdown and the CD Ejects.  So far no issues.  The system reboots  followed a little mac/folder icon in the center of my screen.  Tried holding down the option key during the boot process and I get three icons a refresh button on the left a picture of a hard drive with a penguin in the center and a arrow pointing right on the right side.   If I click on the right arrow I see a screen that flashes "First stage Ubuntu" then the fans  in the  G5  spin up and  go nuts.  

I've installed Ubuntu on tons of workstations (PC) and servers without any issues but never on any Apple hardware.  Am I missing something?

Thanks,
GC

---

### Post by 3rdalbum on 2007-01-04
Known problem.

[http://www.ubuntuforums.org/showthread.php?t=319880]("http://www.ubuntuforums.org/showthread.php?t=319880")

Ubuntu's support for PowerPC is lacking, otherwise they'd incorporate the fix from Debian. Apparantly, it's not harmful to have the fans going at full-speed during the install, just like how an electric toothbrush only SOUNDS like it's drilling a hole in your teeth :-)

---

### Post by GrammatonCleric on 2007-01-04
Thanks!  I should also add that the system never boots.  It just sits there with the fans spinning out of control.

Thanks,
GC

---

### Post by stmiller on 2007-01-04
[https://launchpad.net/~ubuntu-powerpc](https://launchpad.net/~ubuntu-powerpc)

Ben Collins makes the kernel images for PPC. I had a long email conversation with him with the problems of Ubuntu and G5 machines, but he refused to believe me there was any problem at all. So no changes are going to be made unfortunately. Feel free to contact him and let him know the problems you are having. He just blew me off, and could care less. Maybe you will have better luck.

---

