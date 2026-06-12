---
title: "Am I losing my mind?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by 67GTA on 2007-03-19
I have another thread about editing partitions and not being able to boot. I figured I had better start a new one for this. I will try to make this as short as possible. Here goes...

Edited partitions
Dual boot(Ubuntu/Kubuntu)
Got rid of Kubuntu
Kept Ubuntu(only OS on disc)
Computer would not boot afterwards

My computer was trying to boot Edubuntu after going through some kind of weird Intel(r) boot agent screen? I have never had Edubuntu on my PC. My daughter does. Our PC's are connected by a router. She shares an ethernet/satelitte connection from my PC. I finally got My PC to boot and I had her OS on my screen. She had two disk icons on her desktop that were sda1 and sda5(my root and swap partitions). I understand the concept of networking and all, but I have never set one up, and she is only 7, and could not have done this by accident. I unhooked the ethernet cable from her computer and my screen locked up. I then tried to boot up again without being connected to her computer and got the Intel boot agent again. It said the following:

Intel Boot Agent FE v4.1.17
Boot Agent PXE Base Code
Client MAC ADDR:(lots of numbers)
GUID:(even more numbers)
PXE_E53: No boot filename received
PXE_M0F: Exiting Intel Boot Agent
No bootable device --insert boot disk and press any key

I put in my live cd and my grub menu came up and Booted into MY OS!
Can someone tell me what is going on before I call Ghostbusters?

---

### Post by 67GTA on 2007-03-19
My computer will not boot without using the live cd. The Intel boot agent is a network booter. I do not know how that got on my PC. I have ran Avast-rkhunter-chkrootkit, with no results. What is controlling my boot?

---

### Post by 67GTA on 2007-03-19
I looked in my bios settings, and there is an option to boot from the ethernet device. That is where the Intel boot agent was coming from. The order is cd-hard drive-floppy-ethernet. Why is it not booting from the hard drive? It seems to be skipping the hard drive and going to ethernet. When I put the live cd in it boots from it when I choose "boot from first hard drive", so is this hardware related, or is there something I need to look for in my system? Could I have screwed up the partition when I edited it so that the PC is not recognizing the boot sector? I only shrank the Ubuntu partition. I did not delete any of it.

---

### Post by alienexplorers on 2007-03-19
Did you try reseting grub via the liveCD.  Boot the live CD and enter:

find /boot/grub/stage1
root (hd0,0) <------this should be the info given in the find command
setup (hd0)
reboot

---

### Post by 67GTA on 2007-03-19
Unfortunatly yes, I originally thought that grub was the problem, but it is something happening before grub starts. Grub menu comes up when I use the live cd and boot from the hard drive, so it is installed and working. I am starting to think it is hardware or hard drive related.

---

### Post by alienexplorers on 2007-03-19
Sorry I could not help.  Not sure what could be causing that problem your having.

---

### Post by 67GTA on 2007-03-20
The Intel boot agent is the network booter from Intel. I looked in my bios settings and have network boot enabled. It was skipping the hard drive and using my daughter's  computer to boot. We are connected by router/ethernet connection. I am splitting my connection and creating a new IP for her.  It was booting her hard drive to my PC. I couldn't figure out why Edubuntu was trying to boot on my PC and the wallpaper suddenly changed(she changed it). I did not know this was even possible. I installed Lilo to try to replace the MBR, and everything is booting fine now. I am still not sure what happened.

---

### Post by alienexplorers on 2007-03-20
Maybe it was possessed.  Time for a computer exorcism.  I have strange things happening on mine with the login page.  Cuts off the section for options. Yet if I do a cold boot everything straightens out until I reboot.

---

