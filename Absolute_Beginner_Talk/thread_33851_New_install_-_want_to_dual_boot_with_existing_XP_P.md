---
title: "New install - want to dual boot with existing XP Pro"
date: 2005-05-12
forum: Absolute Beginner Talk
---

### Post by Edmund Hon on 2005-05-12
Hi there, right now I'm seriously thinking of installing Ubuntu on my system. I'm a newbie as far as Unix/Linux is concerned, though not to computers in general. I'm using XP Pro SP1 right now, and I plan on installing a 2nd HD for Linux (the 1st HD with it's single NTFS partition is pretty full anyway). 

Is it possible to setup a dual boot mechanism when I install Ubuntu on the new HD? I know I can change the BIOS setup to pick which HD to boot from, though that seems a bit clumsy.

---

### Post by Jace on 2005-05-12
Grub or Lilo will be your boot loader. No need to mess with the BIOS.
Download the .ISO image then burn the image to disk. I used N.T.I burning software.
Make a backup of your important data. Just in case.
Put the new burned Ubuntu cd in and reboot. Follow the steps. 
Keep in mind you need 2 partitions. 1 for the O/S and 1 for the swap file. 
It will ask you, hey I have found 2 drives, which one you want me to install on. Be sure to pick the correct one.
Use the Guided install it will work for the instance.
Keep in mind if there is any data on the 2nd drive it will be gone.
If you have data on it, use Partition Magic to create a partition, then use the Guided install.

---

### Post by Kurai on 2005-05-12
I dsid that exept w/ home.
What i did was the expert install.  When it asked for the partion i resized the windows partion then told it tho use the free space automaticly then let it configure grub as well when you get there.

---

### Post by xmastree on 2005-05-12
I'm doing this.

What I did was remove the primary master (XP) disk, and install another as slave. This is where I wanted to install ubuntu.

I then booted from the CD, installed it using the default settings on hdb, the only hard disk abvailable.

Once installed I reinstalled the XP disk, and I can select which disk to boot from.

Works fine for me, but I'm not sure you (Edmund) have the option to choose at boot time like I do. Your question suggests that you need to go into the BIOS to select. With mine, I hit escape at the right moment and I get a menu of all the disks, USB,network, whatever and can select.

---

