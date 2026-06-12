---
title: "help with Q6600 on nVidia i680 board"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by miniq_q on 2007-09-05
Hello,
I'm about to join the ubuntu family. however, I have a slight problem. I can not get v7.04 (feisty) live dvd to boot to start the install.

here is my setup:

Intel Q6600
evga i680 MB
MSI 8600GTS Video card
Crucial 2x1GB DDR2 800MHz 
Audigy 2 ZS sound card.
Samsung 500GB x 2 in RAID 0 mode.

I already try the txt mode install (with NOAPIC option), VGA mode with NOAPIC.

I search within google with no answer. Can anyone help me please?

thank you:popcorn:

---

### Post by eph1973 on 2007-09-05
Did you download your distro of Ubuntu, and if so, did you burn it to the CD as an image, or as a file?  Or are you able to get to the splash screen, it just won't start the installation process?

---

### Post by miniq_q on 2007-09-05
I download the iso image and burned it onto a dvd, it is bootable on my Dell Inspiron 8600 Laptop fine.
I have 3 bootable DVD so far:

Ubunto v7.04
Kbuntu v7.04
Edubuntu V7.04

all can not boot (GUI or text, with NOAPIC option)

Thanks for all the help :confused:

---

### Post by eph1973 on 2007-09-05
have you tried without the NOAPIC option?  I know on my laptop, NOAPIC makes my screen just sit there blank.  Have you tried reading this page? [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
Since you have a RAID 0 setup, you might need to follow the instructions on that page to install.

If neither of those are your problem, I don't really know.  Hopefully either one of those things work, or perhaps someone else will know more about your problem.

---

### Post by miniq_q on 2007-09-06
Hello,

Thanks for your help.

I downloaded the alternate-cd.iso and was able to install feisty. However, it freeze at random when I try to config my nVidia video card.

still searching for answers. :guitar:

great way to learn I must say. :lolflag:

---

### Post by eph1973 on 2007-09-06
Great job!
Remember to use search tools like google, which can greatly decrease the time it takes to figure the particulars out.  Also, if you are having a lot of crash problems, you might want to try to boot into either recovery mode or using the CD to change your settings.  Just remember, if you boot using the CD, that your actual hard drive partition is somewhere like /media/hda1, or whatever the number of the partition for the drive that your installed your root directory is). 
You may need the driver from here: [http://www.nvidia.com/object/linux_display_ia32_100.14.09.html](http://www.nvidia.com/object/linux_display_ia32_100.14.09.html)
and this has some guidance:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nVidia_drivers_in_7.04](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nVidia_drivers_in_7.04) but basically, you'll have to use your restricted devices manager to ensure you are using the right driver, and follow the instructions.  If you have further questions on the details, you should be able to find fairly easy here on the forums or through [www.google.com](www.google.com)
Good luck :-)

---

