---
title: "Ubuntu wont load on macbook"
date: 2010-03-27
forum: Apple Hardware Users
---

### Post by Ryoukii on 2010-03-27
Today i went ahead and installed ubuntu on my windows desktop pc. I tryed the live cd and tested it out and everything was fine i then installed it using wubi. I then wanted to install it to my macbook ( bought in june 2009 ) and i booted the live cd and chose try ubuntu without any change to your computer. It booted a black screen with a white _ at the top then the screen went white and did nothing. I tryed it several times and nothing happend. I then said ok il maybe just try install it through wubi on my bootcamp partition and it all went fine until i got to the windows bootloader and chose ubuntu, it camp up finishing linux installation and where its meant to change and show the ubuntu symbol after ( i know because i've installed ubuntu on the pc) the screen went white. Nothing. Any help anyone?

---

### Post by linuxopjemac on 2010-03-27
what kind of macbook?

It's good to start here:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by Ryoukii on 2010-03-27
White Macbook

Model Name:	MacBook
  Model Identifier:	MacBook5,2
  Processor Name:	Intel Core 2 Duo
  Processor Speed:	2.13 GHz
  Number Of Processors:	1
  Total Number Of Cores:	2
  L2 Cache:	3 MB
  Memory:	2 GB

---

### Post by linuxopjemac on 2010-03-27
> Basic Installation Instructions

Booting the kernel from the (Live)CD has to be changed. Or else you get a black screen and does nothing at all after 2 seconds of kernel boot. Hit F6 to change the boot options after you selected the language. Then disable acpi enter  acpi=off  in the boot line. I also added,  noapic nolapic irqpoll vga=771 . If you don't want to loose acpi functions you can add this other option  maxcpus=1 . 

[https://help.ubuntu.com/community/MacBook5-2/Karmic](https://help.ubuntu.com/community/MacBook5-2/Karmic)

---

### Post by Ryoukii on 2010-03-27
Ok i did that now it boots but the track pad wont work ?

---

### Post by linuxopjemac on 2010-03-27
[https://help.ubuntu.com/community/MacBook5-2/Karmic#Trackpad](https://help.ubuntu.com/community/MacBook5-2/Karmic#Trackpad)

---

### Post by Ryoukii on 2010-03-27
Ok il try that later eventhough the trackpad wouldnt work at all when i tryed it so i dont know how il be able to get to system settings or whatever lol

---

### Post by linuxopjemac on 2010-03-27
I think you already should have appletouch loaded, just to be sure:

```
sudo modprobe appletouch
```

---

### Post by Ryoukii on 2010-03-27
Okay im posting off ubuntu on my macbook now using a mouse but hey its a start. I installed a few drivers and got my wireless working. The trackpad wont work at all no matter how i change the settingss ?

---

### Post by linuxopjemac on 2010-03-27
do you have appletouch loaded ?

---

### Post by Ryoukii on 2010-03-27
I have bigger problem now. After getting ubuntu to load i deleted my windows 7 bootcamp partition in gparted and installed ubuntu on it. When i go to my 'Windows' Partition grub loads and i can choose ubuntu when i do i get a black screen. Nothing :( Please help what can i do ? Is there any commands i can enter in the command line or something

---

### Post by Ryoukii on 2010-03-27
Update installed refIT and now when i reboot i get choice of Mac OS X ( works fine ) and linux. When i choose linux the tux loads then grub loads then when i choose ubuntu it gives me a black screen with a white _ at the top and then shows a white screen. Ugh this is very annoying

---

### Post by linuxopjemac on 2010-03-27
I am off for my bed. I think you need to update grub. Boot from a CD, chroot into the system and update grub

chroot into system:
[http://mac.linux.be/content/chroot-system-livecd](http://mac.linux.be/content/chroot-system-livecd)

then update grub:
```
sudo grub-install /dev/sda
``` (if /dev/sda is your device, check this)

reboot, and hopefully it works

---

### Post by Ryoukii on 2010-03-28
emm i think i did it wrong i installed grub to the wrong partition or something. Now in reFIT there is Mac os x on HD , linux on HD ( doesnt work ) and linux on partition 4 ( doesnt work ).


But the problem must not be grub. If i need to use apc=off or something to even get ubuntu to load then when i install it that setting will be gone. So ubuntu can never install on my macbook :S this is very confusing and i dont think it will ever work

---

### Post by linuxopjemac on 2010-03-28
sync the partitions within refit using the partition tool

---

### Post by linuxopjemac on 2010-03-28
maybe you should follow a manual that worked for other people, like here:

[http://mac.linux.be/content/intel-installation-reports-ubuntu](http://mac.linux.be/content/intel-installation-reports-ubuntu)

---

### Post by Ryoukii on 2010-03-28
I did. It doesnt do anything.


But like To load ubuntu from a live cd i have to go into f6 modes and choose 3 of them. If i dont ubuntu wont load. So when i install ubuntu how is it meant to work if i cant choose them modes in grub ?

Btw i have deleted the partitions. It still says boot linux from HD in reFIT which is weird and in Mac OS X there is only 1 partition now which is mac.

I want to start over and get ubuntu to work but i dont how its going to work after install if i need certain f6 modes to get it to load

---

### Post by linuxopjemac on 2010-03-28
from withing liveCD use gparted and delete everything Linux (leave it empty). Install MacOSX from CD and start again. I would recommend to make a partitoon with BootCamp and install Windows/Ubuntu in that partition.

---

### Post by Ryoukii on 2010-03-28
In that guide it has everything i did but it has one main rule.

11) At the GRUB menu that starts after rEFIT, press E. This brings up a command list. Add acpi=off at the end of line that has your kernel version.


Thats what i need :) Hopefully this will work. Im not going to install mac os x again but all of linux is deleted and the only operating system is a mac. 

Il post back with how i got on. Thanks for the help its appriciated

EDIT : That guide is way too hard for me ive used linux for one day on my pc desktop so that wont help me.
I guess im just left with mac os x. Oh well pity its so hard to install ubuntu on a mac :/

---

