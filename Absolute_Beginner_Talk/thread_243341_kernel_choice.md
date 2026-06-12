---
title: "kernel choice"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by vilto on 2006-08-24
I just installed ubuntu dapper in friends comp.......
his is amd athlon 64 x2 3800+ processor ......
how do i get dual core support?????
i have read in this forums that smp kernel would do fine...how do i install it........
i currently installed 32 bit version of ubuntu.....when i install this new kernel can i still install i386 packages??
i think there are two smp kernel
1)686 and
2)k7
which one to install and how?

IM NEW TO LINUX..... SO PLZZZ TELL STEP BY STEP:frown:

---

### Post by vilto on 2006-08-25
i want to use 32 bit only as i have heard there are some applications problem in 64 bit version/......

---

### Post by nudnik on 2006-08-25
I've been using a 686 kernel for some time without problems, so the Intel version at least seems to be stable.

I would reccomend the K7 version for your machine.

Access the Synaptic Pacakge Manager using the System tab in the upper left hand corner of your screen. Select "Administration" when the dialogue box appears. A variety of options will materialize, one of which will be the synaptic package manager, choose it; you will be prompted for your password. Enter your password and then scroll down to "linux" section. You will find a variety of kernels available. Choose the following: Linux kernel image for version 2.6.15 on AMD K7 SMP/UP listed as "linux-image-2.6.15-26-k7" version 2.6.15-26.46. 

Right click on the above and mark for installation. Then click on the "Apply" tab at the top of the window. The system might ask for the install CD, if so, just insert it in the drive and click "ok". The system should then download and install the kernel, after which you will need to reboot. Be sure to remove the install CD before rebooting.

---

### Post by vilto on 2006-08-25
thanx........but can i run i386 packages after installing k7-smp kernel

---

### Post by nudnik on 2006-08-25
Yes, usually anything you install from the Ubuntu repositories will work well . Software from other sources might not always be as compatible however.

---

### Post by vilto on 2006-08-25
thanx:D

---

