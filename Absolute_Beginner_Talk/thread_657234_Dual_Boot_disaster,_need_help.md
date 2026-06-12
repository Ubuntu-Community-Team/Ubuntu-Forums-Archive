---
title: "Dual Boot disaster, need help"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by kizmet_x on 2008-01-03
I had bought a new hard drive for linux. The day before the hard drive arrived, I reinstalled Windows XP. When I installed Ubuntu (7.10 64-bit on a core 2 duo), it installed fine but would keep rebooting into XP. I did a manual partition so I could set up a fat32 shared partition, so I figured I messed up the partition. I then rearranged my partitions, used the new hard drive for windows and one of my old hard drives for Linux. Same situation, keeps booting to XP.

Then I tried to repair GRUB on the LiveCD, using a method on another thread. I dont remember the exact commands, I got them straight from the thread, but its something like this:
sudo grub
find /home/boot/stage1
mount (hd0,0)
setup (hd0)
quit

This didnt work, still went straight to XP.

Then I tried the Super Grub disk. Burned it onto a CD, selected Linux, fix boot menu, then something else. Well when my computer restarted, it booted with GRUB, but when I selected the Linux partition, it gave something like "Error 17:Cannot mount partition" and on Windows XP it gave something like "Error 13: Cannot execute .exe", so I couldnt boot into either one. Then I had to use the Windows XP recovery console to rebuild the boot loader.

Needless to say, I am going to have to reinstall Ubuntu. What steps can I take next time to ensure that the dual boot install goes well? Thanks in advace for the help.

---

### Post by kellemes on 2008-01-03
> **kizmet_x said:**
> 
What steps can I take next time to ensure that the dual boot install goes well? Thanks in advace for the help.


Sorry for the short answer but it's the best I can give..
You need to know what you're doing. :popcorn:
I think the best startingpoint is.. [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by logos34 on 2008-01-03
This is the kind of problem you run into often with mixed IDE and SATA hard drives.  Try switching the hard disk boot priority in the Bios so that the ubuntu drive is first.

---

### Post by kizmet_x on 2008-01-03
> **logos34 said:**
> This is the kind of problem you run into often with mixed IDE and SATA hard drives.  Try switching the hard disk boot priority in the Bios so that the ubuntu drive is first.

Upon a clean install of Ubuntu, along with a configuring of GRUB in the terminal, this method indeed went straight into GRUB, with the menu between Ubuntu and Windows. However, when I try to go to Ubuntu it gives error 17:cannot mount partition. When I try to go to Windows, it gives error 12: cannot find file specified (or something similar to that).

---

### Post by CCNA_student on 2008-01-03
I think that you were supposed to type mount(hd0,1), not mount(hd0,0).

---

### Post by Sbarton on 2008-01-03
I think kellemes has pointed you to a really helpful site, though the page shown is for the Alternate CD.
You say that you have 2 drives now, OK!   XP I take it is 32bit your Ubuntu is _64bit_.? I don't know if this works or not?
 However, this is what I would do now, backup all info you wish to save! Reinstall XP on the master drive, then install Ubuntu 32bit on slave drive (64bit if it isessential). Grub boot loader I believe will install on mbr probably (HD0,0).
This should give you a boot menu to choose XP or Ubuntu
regards

---

### Post by logos34 on 2008-01-03
> **kizmet_x said:**
> Upon a clean install of Ubuntu, along with a configuring of GRUB in the terminal, this method indeed went straight into GRUB, with the menu between Ubuntu and Windows. However, when I try to go to Ubuntu it gives error 17:cannot mount partition. When I try to go to Windows, it gives error 12: cannot find file specified (or something similar to that).

Ok, so you're definitely booting the ubuntu drive and you get grub menu but choosing either OS gives above errors.  

On the ubuntu entry press 'e' to edit.  'Root' line should read (hd0,0)...if not 'e' again to change it...then 'enter' and 'b' to boot.  If it works make the change permanent:

gksudo gedit /boot/grub/menu.lst

The error for windows may be due to incorrect 'root' or no ['map' commands]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

If still no luck, reinstall Ubuntu with the windows drive disconnected (just the power plug will do).

---

### Post by kizmet_x on 2008-01-03
> **Sbarton said:**
>  Reinstall XP on the master drive, then install Ubuntu 32bit on slave drive (64bit if it isessential). Grub boot loader I believe will install on mbr probably (HD0,0).


This is the tip that worked! I am typing this on my Ubuntu install right now. Thanks to everyone for helping :)

---

### Post by logos34 on 2008-01-03
> **kizmet_x said:**
> This is the tip that worked! I am typing this on my Ubuntu install right now. Thanks to everyone for helping :)

Why didn't it do that the first or second time?  XP drive was master and grub should have installed by default to (hd0), the windows MBR.  Hmm...(I know it can't have anything to do with 32- or -64 bit (I have both))

---

### Post by kizmet_x on 2008-01-03
> **logos34 said:**
> Why didn't it do that the first or second time?  XP drive was master and grub should have installed by default to (hd0), the windows MBR.  Hmm...(I know it can't have anything to do with 32- or -64 bit (I have both))
I really dont know. Im guessing its because I tried to set up a fat32 partition to share files between the two op systems. I probably jacked something up. I redid my partitions and reinstalled everything and it works fine now.

---

