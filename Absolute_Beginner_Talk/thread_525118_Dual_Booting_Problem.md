---
title: "Dual Booting Problem"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by evilbdboi on 2007-08-13
I have read up on several site on how to dual boot but after i physically do it, it does not seem to work 

Here is what i have done

My system is already installed with Windows XP.

My harddisk is 80GB of which 30GB is allocated to windows and the remaining i leave it as free space

When i am installing ubuntu, at the partitioning area, i selected manual partation. 
1GB is set to SWAP and 15GB is set to ext3. After that i set ext3 to /. The installation is carried on. After the whole process ended, i was prompt to restart and take out the installation cd. 

I was waiting for a screen which i can see a choice of which OS i want to boot into but instead, the windows boot screen was shown and i am back to windows again. I have tried reinstalling several times the same situation occurs. I even download the software and verify that it was downloaded without error before writing it to a CD.

Below is a screenshot of my partitioning please advise

[IMG]http://i203.photobucket.com/albums/aa33/evilbdboi/NewBitmapImage.jpg[/IMG]

---

### Post by Wim Sturkenboom on 2007-08-14
I'm not sure how to fix it as I don't recall all options during the install. The problem is that the bootlaoder (GRUB) is not installed in the right place (it's probably somewhere on the second HD).

Options
1)
You can try to set the bootorder in the BIOS to boot from the second HD. It might solve the issue.
2)
Re-install and check if you get an option where to install Grub. It should be in the MBR.
3)
Search here how to *fix GRUB*. Searching this forum reveals a number of hits. one of them is [http://ubuntuforums.org/showthread.php?t=508300](http://ubuntuforums.org/showthread.php?t=508300) and might help you out.
4)
Boot from live CD; there might be an option to boot from a certain harddisk (this is a temporary solution).

---

