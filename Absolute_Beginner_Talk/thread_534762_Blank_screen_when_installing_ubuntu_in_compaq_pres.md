---
title: "Blank screen when installing ubuntu in compaq presario F572"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Satpam on 2007-08-25
Hi guys,

I am trying to install ubuntu 7.0.4(downloaded one) on compaq presario F572 and it displays blank screen after I select start and install ubuntu and a couple of initializations. Anyone know how to solve this problem :confused:? Also while searching in forum, I across some ppl mentioning command prompt, but I dont see any command prompt option in installation menu, is it the F6? 

My spec is AMD athlon 64 x2, 1 GB of memory, Nvidia Geforce Go 6100, Synaptics PS/2 touchpad, Broadcom 802.11b.g WLAN.

It passes the disk-defect check and I also tried starting from safe graphic mode and the initializing stops somewhere and so I restart my laptop.

Thank you.

---

### Post by oilchangeguy on 2007-08-25
the first problem is your video card. and if you get it installed, the second problem will be your wireless card.

---

### Post by pgar23 on 2007-08-25
> **Satpam said:**
> Hi guys,

I am trying to install ubuntu 7.0.4(downloaded one) on compaq presario F572 and it displays blank screen after I select start and install ubuntu and a couple of initializations. Anyone know how to solve this problem :confused:? Also while searching in forum, I across some ppl mentioning command prompt, but I dont see any command prompt option in installation menu, is it the F6? 

My spec is AMD athlon 64 x2, 1 GB of memory, Nvidia Geforce Go 6100, Synaptics PS/2 touchpad, Broadcom 802.11b.g WLAN.

It passes the disk-defect check and I also tried starting from safe graphic mode and the initializing stops somewhere and so I restart my laptop.

Thank you.

Yes. the command prompt is accessible when you go to your installation option that you want and then press F6...when you press F6, delete the "quite splash" part of it...this will allow you to see where the installation is going wrong/stalling.
When you find where it is going worng/stalling, report back to the forums with output...and search the forums for threads of similar problems/solutions...If not post a new thread and someone will HELP. I will check bak later.

Good Luck.

---

### Post by Satpam on 2007-08-25
> **oilchangeguy said:**
> the first problem is your video card. and if you get it installed, the second problem will be your wireless card.

How do I able to install the video card driver from ubuntu install menu? I can't access internet from it.

---

### Post by oilchangeguy on 2007-08-25
> **Satpam said:**
> How do I able to install the video card driver from ubuntu install menu? I can't access internet from it.

you may have to use the alt. cd to perform the install.

---

### Post by Satpam on 2007-08-25
> **oilchangeguy said:**
> you may have to use the alt. cd to perform the install.

 I finish burning ubuntu 7.0.4 alternate cd, can anyone guide me on installing the video card driver?

---

### Post by Satpam on 2007-08-31
Anyone :confused:?

---

### Post by Marat Galiev on 2007-08-31
I have installed Ubuntu?

---

### Post by Satpam on 2007-09-02
> **oilchangeguy said:**
> you may have to use the alt. cd to perform the install.

I tried the alt. cd, select the option it gave as best as i could and install it, but when I boot the ubuntu, it stops loading and thats it...so in the end I delete the ubuntu. I think the problem might come from the nvidia graphic card like most ppl said, but I don't know how to install it while I am installing ubuntu. Anyone know how to fix this ? Thanks.

---

### Post by fastpakr on 2007-09-04
Have you read any of the threads discussing getting Ubuntu working on the F572?  Try adding noapic as a boot parameter (press F6 when GRUB starts and add it to the kernel line).

---

### Post by mootpoint on 2007-09-04
1) Boot the Live CD.
2) Double click on the "install" icon on the desktop.
3) Hit F6 to edit the boot line.
4) Add "noapic acpi=off irqpoll" (no quotes) to the end of the kernel line.
5) Proceed with the install.
6) After Ubuntu is installed, you'll want to use the restricted drivers manager to install the Nvidia video drivers. You'll then want to remove the "acpi=off" and perhaps "irqpoll." 

As another poster noted, searching ubuntuforums.org for f572us will take you to several threads where others have worked out these issues.

m00t

---

