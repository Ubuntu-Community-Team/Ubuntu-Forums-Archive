---
title: "Unstable Booting"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by okey666 on 2007-08-20
I installed Ubuntu 7.04 Feisty Fawn after difficulty with booting from live cd see:
[http://ubuntuforums.org/showthread.php?t=527106]("http://ubuntuforums.org/showthread.php?t=527106")

I fixed this by swapping my SATA drives around. A few days after that X crashed and I could not recover it ( I'm no good at all this config file editing). I then reinstalled Ubuntu using my external   USB DVD drive. I had this problem before the reinstall but even more so now, when I boot about 4 times out of 5 the boot freezes at the splash screen and the hardrive appears to be inactive.

Does anyone have any idea what the problem could be?
I am running a self built system with:
Abit AB9 Quadro GT motherboard
Intel E6600 Core 2 Duo on a LGA775 slot processor
Palit nVidia 8600 GT graphics card
2GB DDR2 dual channel ram
250 Hitachi SATAII hard drive
CD/DVD +/- RW SATA drive

it also has an Award Bios

I am not dual booting and had great difficulty installing any other operating system.

---

### Post by ajgreeny on 2007-08-20
Next time it freezes hit **Ctrl+Alt+F1** to go to the command line and see where it all stopped,
or, at boot up when you see the word grub, hit esc to show the grub menu and hit **e** (for edit), navigate with the cursor keys to the kernel line, hit **e** again and delete the words **quiet** and **splash** from that line.  Hit **enter** to accept the changes, then **b** to boot and you will see all the boot messages instead of the splash screen for that boot up only.  It will revert to splash at all following boots.

If you want to change your grub for the time being so that it shows these messages every boot up, backup and then edit the /boot/grub/menu.lst as root by typing in terminal:-
**sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak**
then
**gksudo gedit /boot/grub/menu.lst**
again deleting the words quiet and splash from the kernel line of the kernel you boot normally.  Exit and save the edited file.
Now update grub with:-
**sudo update-grub**

Once you have found the problem with your boot up sequence (hopefully you will) you can reverse these grub changes by putting back the words **quiet** and **splash** in the kernel line.

---

### Post by jdfreshwater on 2007-08-20
It might help if you tried to boot into recovery mode, and see if you are getting any error messages on the boot.  This should give you information if it is trying to search for an unfound network or something like that.  Recovery mode is avaible by hitting Esc(I think it comes up) and choosing it in the grub menu.

---

### Post by Hobo Joe on 2007-08-20
Did you ever get your graphics cards drivers running before this happened?

---

### Post by okey666 on 2007-08-20
> **Hobo Joe said:**
> Did you ever get your graphics cards drivers running before this happened?
I have always had these problems even when the drivers were not  installed. And now I do have them the problem persists.

---

### Post by okey666 on 2007-08-20
I will try and get up the no splash screen boot next time I have the opportunity.

---

### Post by okey666 on 2007-08-24
It is like the Live CD problem I had. After waiting for a while 4 errors come up that look like:
[68.484622] ata1.00: failed to set xfermode (err_mask=0x4)

and then it says:
/bin/sh: can't access tty; job control turned off (initramfs)

Will try F1 next time I boot.

---

### Post by okey666 on 2007-09-02
I tried F1 and it came up with the same message!

---

