---
title: "Ubuntu 11.04 works only in nomodeset option. How can i get full graphics in 11.04"
date: 2012-03-11
forum: Asus Ubuntu Support (CLOSED)
---

### Post by jijokjose on 2012-03-11
I have an **ASUS N55S** laptop with following configuration.

[B]i7 processor
2 GB NVIDIA graphics card[/B]

I installed ubuntu 10.04 on my laptop then upgrade to 11.04 on yesterday. 
[COLOR="Red"]After upgrading it reboots and works with full graphics but after the next reboot it shows only a blank screen[/COLOR] 
then i try **nomodeset** option in grub so ubuntu 11.04 load with minimum graphics. 
**What can i do for getting full graphics...???**
I get full graphic in the first reboot so i think if some options changed then i will get full graphics...
Plzz help me....
Thanks in advance :)

---

### Post by winh8r on 2012-03-11
Take a look here:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

Hope this helps you.

---

### Post by jijokjose on 2012-03-11
Thanks for the help...
Am going to try that solution... Thanksss :)

---

### Post by jijokjose on 2012-03-11
Thanks for the help but I Do all the steps that your are giving but after installing **startup manager** 
i reboot the system then ubuntu loads the startup screen(pink color screen) in graphics mode 
then display the following error in black screen.

[B]FATAL:Error inserting vesafb (/li/module/2.6.38-13-generic-pae/kenel/drivers/video/vesafb.ko):No such device

  *strting CUPS printing spooler/server                     [ok]

fsck from util-linux-ng 2.17.2

/dev/sda9:clean, 456220/2897424 files, 2889721/11567164 blocks

  *starting network connection manager                      [ok]
  *starting MDNS/DNS-SD daemon                              [ok] [/B] 

[COLOR="DarkRed"]Now i cant load my ubuntu 11.04 either in graphics mode or in nomodeset option.... [/COLOR]

Plzz help me....

---

