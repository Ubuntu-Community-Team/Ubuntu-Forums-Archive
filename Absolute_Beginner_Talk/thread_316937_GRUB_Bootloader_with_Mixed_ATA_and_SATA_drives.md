---
title: "GRUB Bootloader with Mixed ATA and SATA drives"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by beaker on 2006-12-11
Hi all,

I've been using Ubuntu in a VMWare environment and have now taken the next step and installed Ubuntu on my PC alongside Windows XP Pro.

Just a bit about what's in my PC:

 o AMD Athlon 64 3400+
 o SiS WinFast motherboard
 o 2 x 120Gb IDE Disks 
 o 1 x 160Gb SATA Disk
 o Realtek Ethernet etc

After what appears to have been a successful installation of Ubuntu onto one of the 120Gb IDE (ATA) disks, and the GRUB bootloader was apparently installed, the bootloader doesn't get a look in when starting my PC.

What I remember seeing during the GRUB setup, it said it was writing the bootloader to hd0, but XP is installed on sd0 (assume this is the SATA naming convention?).  

The SATA disk seems to take priority over the ATA disks when my system boots, but I can't find anything in the BIOS which allows me to alter the priority.

My question is this, can I get GRUB to install into the SATA MBR, and would this allow me to dual-boot properly?

All your advice is welcome.

BeakZ

---

### Post by adaptr on 2006-12-11
The good news is: yes, you can :)

The slightly less good news is that you'll have to experiment, but no worries - the most logical option should work for 90% certain.

What happens is that your BIOS sees the SATA disk as disk **zero** on boot, so it boots from that - this is where your Windows bootloader is located.
But as soon as Grub is run, it sees the SATA disk as disk **two**, in effect the last disk in your system.
GRUB has little or no idea what the BIOS sees.
What you have to do, then, is fool GRUB into accepting the SATA disk as its own boot disk.
The easiest solution is to boot the Install CD again, and when you get to Ubuntu, start the Terminal.
Now you can run Grub:
> grub
It will present you with a prompt (>); type EXACTLY the following:
> root (hd2,
and press TAB.
It should now present you with a list of partitions on the SATA disk.
Choose the one that has your root (Ubuntu) partition on it - it will be of type **ext2**.
Type its number and press TAB again; it should complete the command for you.
When you press ENTER, it will tell you if it could successfully access the partition.
Next, install grub on the SATA drive:
> setup (hd2)
and press ENTER.
You should see a short list of commands fly by, which should all succeed.
Last but not least, you will have to edit the Grub configuration to point to the correct drive:
> gedit /boot/grub/grub.conf
and change the (hd0) to (hd2).
Save the file, and reboot!
If all goes well, you should see Grub, with the option to boot Ubuntu or Windows.
If it doesn't boot Windows from grub you may have to "fake" the drives for it, by mappig hd0 to hd2 and vice versa.
**man grub** to find out how...

---

### Post by gn2 on 2006-12-11
Have you read this: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

