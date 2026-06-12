---
title: "Dual Boot Questions 7.10[Solved]"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by SpAcKs on 2007-11-13
Hello all!  I'm in the middle of installing 7.10 onto my laptop which was currently only running XP.  For reference, I have been following the instructions on this site; [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/").   Everything was going very smoothly until I got to step #8 under the 'Installing Ubuntu Linux' section.  I have an 80 gig hard drive partitioned like so:

60gb  ntfs  windows
14gb  ext3  ubuntu
2gb  linux-swap
4gb  fat32

The install went clean without any errors, however upon rebooting, my laptop is only loading back into XP and not giving me a boot option.  I do realize that I have to create an ubuntu.bin to direct the boot up process.  However, my lack of Linux knowhow is preventing me from finishing the install process.  Any help would be greatly appreciated.

---

### Post by SlalomMan on 2007-11-13
If you are dual booting, you can use the GRUB bootloader which installs automatically with Ubuntu. However, it looks like that guide is directing you towards using the Windows bootloader. It looks as if you don't create the Ubuntu.bin file, but it is created through the install process in the FAT32 partition...I would love to help more, but I used GRUB, and I, too, am pretty new to linux, but I hope this helped.

---

### Post by SpAcKs on 2007-11-13
Thanks for the feedback...I'll look into the method that you tried.  I guess my real question is...is there a trick to making the commands work under #8?  I have tried to run those commands from the command prompt, Applications --> Accessories --> Terminal, but I keep receiving a 'Permission denied' message.  I guess that is why I'm stuck.

---

### Post by SpAcKs on 2007-11-14
Just to update this thread...I did get the dual boot to work.  The problem was resolved by typing 'sudo' before the codes to make and mount the new directory.  I am able to boot into Ubuntu and XP, but now I have bigger fish to fry.  I need to find ATI drivers for my chipset and I need to get the wireless nic working.  Please let me know if anyone has any suggestions on how to accomplish those tasks.

---

### Post by bulldog on 2007-11-14
Download envy for the driver.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

No drivers for the chipset are needed.

---

### Post by Sef on 2007-11-14
I am closing this thread since the problem has been solved, and I started [a new thread]("http://ubuntuforums.org/showthread.php?p=3769302#post3769302") for the problems mentioned.

---

