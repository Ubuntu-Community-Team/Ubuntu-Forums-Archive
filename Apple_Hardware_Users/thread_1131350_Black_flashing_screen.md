---
title: "Black flashing screen"
date: 2009-04-20
forum: Apple Hardware Users
---

### Post by kaouki on 2009-04-20
Hello there,

I am dying to use ubuntu-studio on my macbook1,1. To be safe I installed everything first on an external usb drive. I made a small HFS Refit partion and took the standard values to partion the rest of the disk in a ext3 and swap partion.

The installation went flawless the second time ( I first had a Grub error 15).

The problem is that when I am booting the distro I end up with a black screen with some flashing lines after the splashscreen.

Does anyone know how to solve this problem?

Thx

Anthony

---

### Post by cyberdork33 on 2009-04-20
well, if you are getting it to boot from an external device at all you are doing better than most. Usually you have to use grub-efi for that to work.

---

### Post by kaouki on 2009-04-21
I found a quick workaround for the black screen: I boot in Recovery mode, choose to reconfigure de X server and the resume to normal boot. Ubuntu boots fine.

My new problem is the following: I need to perform these steps at every boot although X.org saves his configuration. Is there a way to fix this?


For the external disk, this is how I did it:

1. Create with diskutil (in os x) a small partition called REFIT and make it bootable. 
2. Perform a manual install of Refit (Put the files in it and run the script) on the newly created partition.
3. Insert the ubuntu install disk, and perfom the installation. Choose the Freespace on the external disk (the one with the REFIT partition, and partition your ext3 and swap (I took the default)
4.Finish the installation
5. Boot with the ALT key pressed, choose Refit
6. In Refit, choose to boot Linux.

---

### Post by cyberdork33 on 2009-04-21
..

---

### Post by cyberdork33 on 2009-04-21
> **kaouki said:**
> I found a quick workaround for the black screen: I boot in Recovery mode, choose to reconfigure de X server and the resume to normal boot. Ubuntu boots fine.

My new problem is the following: I need to perform these steps at every boot although X.org saves his configuration. Is there a way to fix this?
Can you post your xorg.conf

> **kaouki said:**
> For the external disk, this is how I did it:

1. Create with diskutil (in os x) a small partition called REFIT and make it bootable. 
2. Perform a manual install of Refit (Put the files in it and run the script) on the newly created partition.
3. Insert the ubuntu install disk, and perfom the installation. Choose the Freespace on the external disk (the one with the REFIT partition, and partition your ext3 and swap (I took the default)
4.Finish the installation
5. Boot with the ALT key pressed, choose Refit
6. In Refit, choose to boot Linux.
yes, but this doesn't work for most. It is interesting that it works for you. Usually if you try to boot a "legacy OS" from a external device, rEFIt will give you an error about Apple firmware not supporting the ability to boot from external devices.

---

### Post by tomthumb99 on 2009-04-21
I get a solid black screen, my X windows is now shot, my base 8.10 OS boot up is fine.  Sad part was that from Synaptic manager, I was just install webcam software; not looking for a jump to the 'studio' version.

Any way to back out or remove 'Ubuntu-Studio' cleanly??  I can get to the tty prompt and run apt-get??

---

