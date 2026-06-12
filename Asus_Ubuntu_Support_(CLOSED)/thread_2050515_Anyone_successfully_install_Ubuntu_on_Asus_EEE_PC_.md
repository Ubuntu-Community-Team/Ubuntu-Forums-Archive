---
title: "Anyone successfully install Ubuntu on Asus EEE PC 1025c netbook?"
date: 2012-08-31
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Pendita on 2012-08-31
[http://www.asus.com/Eee/Eee_PC/Eee_PC_1025C/](http://www.asus.com/Eee/Eee_PC/Eee_PC_1025C/)

> Specifications
Operating System	Genuine Windows® 7 Home Premium, 32bit
Genuine Windows® 7 Starter, 32bit
Express Gate
Display	10.1" LED Backlight WSVGA (1024x600) Screen
CPU	Intel® Atom™ N2600 (Dual Core; 1.6GHz) Processor
Memory	DDR3, 1 x SO-DIMM, 1GB ( Maximum 2GB ) *5
Storage	320GB/500GB HDD 
3GB ASUS Web Storage*1
Wireless Data Network	WLAN 802.11 b/g/n@2.4GHz*2
Bluetooth V3.0*2
Audio	Hi-Definition Audio CODEC 
High Quality Speaker
High Quality Mic
Interface	1 x VGA Connector
2 x USB 2.0 *3
1 x USB 3.0 *3
1 x LAN RJ-45 
1 x HDMI
1 x Audio Jack (Headphone/Mic-In)
1 x Card Reader : SD/ SDHC/ MMC
Battery	USB 2.0:
6cells Li-ion Battery Pack, battery life 12 hrs (6cells, 5200mAh, 56W/h)*4
3cells Li-ion Battery Pack, battery life 6 hrs (3cells, 2600mAh, 28W/h)*4
USB 3.0:
6cells Li-ion Battery Pack, battery life 11 hrs 0 (6cells, 5200mAh, 56W/h)*4
Dimensions	262 x 178 x 20.7 ~34.4 mm (WxDxH)
Weight	1.25 Kgs (w/ 6cell battery)
1.1 Kgs (w/ 3cell battery)
Color	Texture : Blue, Pink, Purple
Note	*1: Subject to system configuration and usage.
*2: Availability may vary by SKU and country.
*3: 1 x USB 3.0 + 2 x USB 2.0 (optional) or 3 x USB 2.0
*4: Subject to system configuration and usage.
*5 : The memory is fixed on the motherboard and there is no SO-DIMM on the motherboard. The On Board Memory is unable to be removed or replaced for extending.

Anyone?

How's the battery life?

I did a wubi install but the graphics didn't render properly

it Windows 7 starter preinstall really lacks and sloppy

---

### Post by Festina_Lente on 2012-09-01
I'm newish to Linux and got this computer thinking it would run given the 1st eeepcs were on Linux 

It doesn't work well since the graphics card uses closed source drivers. There are some drivers now available: [http://blog.uninstall.it/2012/06/05/kubuntu-12-04-on-asus-eeepc-1025c/](http://blog.uninstall.it/2012/06/05/kubuntu-12-04-on-asus-eeepc-1025c/) 

The computer already comes with four partitions on the drive also, one of which must be erased (can't remember which) before a full install. What can be tricky is that the Ubuntu doesn't recognize Windows and one must partition the drive manually.

Battery life is good with if you reduce screen brightness one way 
sudo set pci -s 00:02.0 F4.B=(a value for brightness 0-99)

So no, it's not the ideal computer for Ubuntu.

---

### Post by Riccardoc on 2012-09-04
Hi,
I managed to make Lubuntu 12.04 work quite well (hardware video decoding with 1080p at <10% CPU, everything working ok excluded 3D) with the 1025c and I wrote a guide; it's not smooth and easy but it should work on any Ubuntu derivate. Feel free to contact me in case you have problems.

[http://linuxeeepc.blogspot.com/2012/08/lubuntu-on-eeepc-1025c-with-correct.html](http://linuxeeepc.blogspot.com/2012/08/lubuntu-on-eeepc-1025c-with-correct.html)

---

### Post by eudemonis on 2012-09-23
check out this blog for an easy and effective fix for of the issue with processor support
[http://blog.uninstall.it/2012/06/05/kubuntu-12-04-on-asus-eeepc-1025c/](http://blog.uninstall.it/2012/06/05/kubuntu-12-04-on-asus-eeepc-1025c/)
worked for me like a charm... been looking for a solution for a while there is a lot of garbage out there on this

---

### Post by silent_shade on 2012-10-13
Hello!
I am not quite sure if this is the right place to post, or if anyone should need this information but I had a real trouble figuring it out and wish to share the results. EEE 1025 comes with a cruel BIOS. One cannot change the boot order, indeed there is no boot order, just internal HDD and booting via network. So, whatever installation media you are using (CD, USB) you need to plug it in, turn laptop on and hit Esc key when you would regularly hit F2. This opens boot menu and with it - a chance to boot/install from CD or whatever.

---

### Post by munkee on 2012-11-10
Anyone had any joy getting Ubuntu 12.10 on an EEEPC 1025C & CE?   

It seems to install without any problems, but falls over on the first boot.  I'm thinking it is down to those pesky Cedarview drivers.  I have re-installed 12.04.1 LTS and pulled the Cedarview drivers via apt and it is working just fine with the 1024 x 600 resolution.

---

### Post by Light-kun on 2012-12-13
Guys, I have this notebook and LinuxMint13 on it.
Problems I have:
1) microphone didn't work with pulseaudio at all and  I removed pulseaudio. Now it works but quality is terribly low. And if I connect ext microphone the wuality remains the samse, so I think it's a driver issue.
2) another big problem is hotkeys work. brightness hotkeys show indicator bar, but don't affect real screen brightness. Turne screen off doesn't work too. Though volume keys work good.
WHen I tried to fix it I added "acpi_osi=Linux" to my boot params and first few minutes all worked good and brightness hotkeys too, but after a minute or two after boot all system was deeply frozen (no REISUB even, only hard power off) I tried to boot gain and again. All three times I got to deep freeze and no useful logs in syslog  after reboot. So I switched back this option and asking you - what can I do to fix these problems?

Any help would be appreciated.

---

### Post by Rob Sayer on 2012-12-15
Haven't tried the asus but I have had recent experience with an Acer D270, which also uses the infamous (in linux circles) cedarview/3600 architecture.

With xubuntu 32 bit 12.04 the screen resolution was correct but the only way to turn down the brightness from maximum was with the terminal.  And then if it came out of suspend it'd be at full brightness again.

When I tried the cedarview packages in the repos the video did not work on reboot.  Very frustrating.

I installed Mint 13 Xfce ... which is based upon ubuntu 12.04 lts, except it comes with xfce 4.10, which doesn't work with ubuntu lts ... and installed all 3 cedarview packages through synaptic.  The brightness controls work perfectly now.  *Much* more impressed.

Haven't fully tested it out yet ... it's a netbook, I didn't get it to play video on ... but I'm happy as is.

OK, tried billardgl this morning.  Which does use 3d rendering.

And it works.  Not outrageously fast, but useable.

---

### Post by chuckleberry on 2013-04-02
I just spent the better part of the day installing Ubuntu 10.04 &  10.01 Netbook Editions, Linux Mint 13, Ubuntu 11.01, 11.10 & 12.04,  and 4 Puppy Distros - all of them stuck at 800x600. Anything I could  find on the web seemd to indicate I was stuck too. I don't have any  blank DVDs to try the Kubuntu kernel trick from Uninstall it! , so I  decided to go with Mint as it had the friendliest 800x600 screen. Did  all the updates & re-read the forums while they downloaded. The one  person who "pulled the Cedarview drivers using apt" seemed the only  hope, but I have no idea what he's talking about since I'm a bit of a  newbie as far as opening the hood goes. So, with the updates completed  & the required reboot I used Synaptic to check out the Cedarview  situation - figuring maybe I could "pull the drivers". Turns out there  are 3 Cedarview options to install, which I did, rebooted & bingo !  1024x600 upon the reboot. Display options give me the choice between  1024x600 & 800x600. Its perfectly usable now. I don't know if this  applies to Linux Mint 13 only, or if the repossitories have the proper  drivers now.

---

### Post by elhijodelpeje on 2013-04-17
Last year I installed Ubuntu 10.04.4 LTS Lucid Network in my eeepc 900, and everything is working smooth, to do it, I created a Multisystem USB flash drive
from other linux in another PC, [http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)  ,  you can use Yumi Multiboot from windows too
[http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)   .Boot from USB in your eeepc to load Multisystem, and select your Ubuntu distro to run 
a live session from which you can install to your hard or ssd drive. Actually I am not able to see my windows network in my EEEPC, although I can see my 
ubuntu shares in my windows 7 pc, but I am working on it, any help...???
Hope this help. Regards...Roberto

---

### Post by Melodie on 2013-08-09
Hi,

I have finished successfully the install of Ubuntu Openbox Remix (codename Bento Village built with Ubuntu Builder on a minimalist Ubuntu Mini Remix) on a eeepc Asus 1025c thanks to this tutorial [http://linuxeeepc.blogspot.com/2012/...h-correct.html](http://linuxeeepc.blogspot.com/2012/08/lubuntu-on-eeepc-1025c-with-correct.html) and I thank the author very much.

Strangely after install and reboot all went fine, until after update and reboot : then things started to become quite complicated as the boot started but was not ending. After reading the above page, and having added the small xorg.conf with the fbdev driver mentioned all went fine.

In the meanwhile I had removed a pair of things such as laptop-mode-tools, which I don't know if is necessary or not, and rfkill for the boot was stalling after one and other related message. However I'll try to reinstall them one by one tomorrow, and anyhow thanks a lot for this thread and for this article at the blogspot page!

---

### Post by TenPlus1 on 2013-08-10
Installing Ubuntu through wubi is definitely a lot slower than running it natively on it's own partition...  Also, their are many ways to conserve battery life including a little utility called jupiter which can be installed:  [https://launchpad.net/~webupd8team/+archive/jupiter](https://launchpad.net/~webupd8team/+archive/jupiter)

---

### Post by KitsuneAkki on 2014-04-20
Hi Everyone, I own an **Asus Eee PC 1011PX** Successfully running Ubuntu.

I have done several updates and hardware upgrades with little to no hassle at all! Even updated the bios, installed SSD, upgraded the WiFi card to a 300 mbps + BT 4.0 card.

I have had issues with the **fn keys**, but after furiously fighting with acpi and grub, i found out that most laptops with any debian install will have issues with acpi events and **fn keys** if the **SATA** Hard Drive options in the **BIOS** are set to **AHCI** instead of **IDE**.

Setting it as **IDE** will resolve many **ACPI** issues as well as the **fn** + **F1** - **F12** keys not functioning correctly.
( I have seen so many forums and blogs flooded with questions and solutions that are workarounds as best! )

*Admins please could you post a STICKY for this solution, as this will frustrate, Asus, ThinkPad, Toshiba, Dell etc users to the brink of madness!*

---

### Post by rbscycle on 2014-04-22
I installed 14.04 32bit on Eee PC 1005HA, no problem!  It was a clean install, not an upgrade.

---

### Post by temporos on 2014-04-25
Lubuntu 14.04 runs great on my Asus Eeepc 1005HA. A few odd kinks here and there, but that's to be expected.

---

