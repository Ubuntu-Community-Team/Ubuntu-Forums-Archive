---
title: "I need wireless and I cant get it..."
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by GSF1200S on 2007-03-27
Ive managed to adapt to Edgy pretty well- Ive got NTFS3g working, my video card is working, and nearly everything else is working...

The one thing I need the most to break my XP dependency is a functioning wireless card. Ive tried to get this resolved in a former post, but I really didnt solve my problem. Ive tried using Ndiswrapper and windows drivers- nothing. Ive tried using madwifi (Atheros Communications is the Vendor, card made by Gigabyte (W101GT), and while it seems like im close, I still cant get it to work.

To be honest, im not sure I know what im looking for. When I had ndiswrapper and the graphic interface for it running, my drivers were listed as installed, but it said the hardware wasnt present. Trying the other path of madwifi, it seems like it installed through the  terminal fine, but I dont see any wireless card listed in networking, and I dont have a connection. For madwifi, Ive used the following resources:

[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

[http://packages.debian.org/testing/net/madwifi-tools](http://packages.debian.org/testing/net/madwifi-tools)

Ive looked through the forums, but most others could at least detect a network, or were running Fiesty. Im on Edgy 6.10 Ubuntu. I have to have wireless for my job... if anyone could lend a hand I would really appreciate it!

---

### Post by josephus on 2007-03-27
[http://madwifi.org/wiki/Compatibility#GN-WI01GT](http://madwifi.org/wiki/Compatibility#GN-WI01GT)

This guy couldn't get it to work with the version of HAL installed on Edgy Eft.  You might have to wait for Feisty Fawn or compile HAL yourself.

---

### Post by GSF1200S on 2007-03-27
> **josephus said:**
> [http://madwifi.org/wiki/Compatibility#GN-WI01GT](http://madwifi.org/wiki/Compatibility#GN-WI01GT)

This guy couldn't get it to work with the version of HAL installed on Edgy Eft.  You might have to wait for Feisty Fawn or compile HAL yourself.

Thanks... I wont burn a lot of time trying to get madwifi to work. I guess I should focus all my attention on ndiswrapper. In the terminal, it says something about ndiswrapper failing to load and to check the system log. The system log doesnt seem to have anything about the ndiswrapper in it... I dont even know what HAL is, so compiling it for madwifi doesnt sound like a good idea either... Man, this sucks... if I could just get past the hardware crap Id be set!

---

### Post by josephus on 2007-03-27
Are you sure you are using the right drivers?  Here are the drivers off of the company website

[http://www.gigabyte.com.tw/Support/Communication/Driver_Model.aspx?ProductID=2215](http://www.gigabyte.com.tw/Support/Communication/Driver_Model.aspx?ProductID=2215)

While we are at it do you mind posting the output of 
```
lspci
```
I'm just interested in the line that mentions your wireless card.

As well, I'm interested in seeing which modules are loaded.
```

lsmod | grep ath
lsmod | grep ndis
```

The first line is to make sure that none of the madwifi are loaded and interfering with you the ndiswrapper.   

I was just playing around with ndiswrapper on my wireless card (not the same card as yours), and it took a couple of tries before it would load up properly.

---

### Post by GSF1200S on 2007-03-28
> **josephus said:**
> Are you sure you are using the right drivers?  Here are the drivers off of the company website

[http://www.gigabyte.com.tw/Support/Communication/Driver_Model.aspx?ProductID=2215](http://www.gigabyte.com.tw/Support/Communication/Driver_Model.aspx?ProductID=2215)

While we are at it do you mind posting the output of 
```
lspci
```
I'm just interested in the line that mentions your wireless card.

As well, I'm interested in seeing which modules are loaded.
```

lsmod | grep ath
lsmod | grep ndis
```

The first line is to make sure that none of the madwifi are loaded and interfering with you the ndiswrapper.   

I was just playing around with ndiswrapper on my wireless card (not the same card as yours), and it took a couple of tries before it would load up properly.

I apologize for not responding sooner.. Ive been a bit busy... but thanks for throwing in some ideas... Im really new to this-

lspci yielded the following results:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0398 (rev a1)
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
06:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

lsmod | grep ath yielded the following results:
ath_pci                97184  0 
ath_rate_sample        15616  1 ath_pci
wlan                  204764  2 ath_pci,ath_rate_sample
ath_hal               192080  2 ath_pci,ath_rate_sample

lsmod | grep ndis
ndiswrapper           201744  0 
usbcore               130304  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd

Hopefully this helps.. Ive been working on this for DAYS now, and im running out of ideas.. I really appreciate any advice...

---

### Post by josephus on 2007-03-28
did you try out the drivers from the website?

if you are going with the ndiswrapper you need to disable the madwifi drivers.  

```
sudo modprobe -r ath_pci
```

then load up 

```
ndiswrapper -i net5211.inf
ndiswrapper -l
sudo modprobe ndiswrapper
```

Also I noticed on the madwifi website that they have a new version out which includes the newer version of HAL.  It's pretty easy to install, but as long as you are using the right drivers, ndiswrapper should work.

---

### Post by GSF1200S on 2007-03-28
> **josephus said:**
> did you try out the drivers from the website?

if you are going with the ndiswrapper you need to disable the madwifi drivers.  

```
sudo modprobe -r ath_pci
```

then load up 

```
ndiswrapper -i net5211.inf
ndiswrapper -l
sudo modprobe ndiswrapper
```

Also I noticed on the madwifi website that they have a new version out which includes the newer version of HAL.  It's pretty easy to install, but as long as you are using the right drivers, ndiswrapper should work.

hmm this is weird.. check out this procession which makes no sense to me:

poeticrpm@poeticrpm-laptop:~$ ndiswrapper -l
installed drivers:
net5211 invalid driver!
poeticrpm@poeticrpm-laptop:~$ ndiswrapper -e net5211.inf
couldn't delete /etc/ndiswrapper/net5211.inf: No such file or directory

And then, if I attempt to install the drivers included on a disc with my computer, I get this:

poeticrpm@poeticrpm-laptop:~$ ndiswrapper -i w29n51.inf
couldn't create /etc/ndiswrapper/w29n51: Permission denied at /usr/sbin/ndiswrapper-1.9 line 139.

Im installing Fiesty right now, and after I reboot, im going to try the madwifi again. If I cant get that rolling, im going to come back to ndiswrapper.

If you see ANYTHING above that seems odd, let me know- your help is invaluable right now.. If I cant find it in a reply or on a website somewhere, I cant do it in Linux (yet, im learning..) Thanks!

---

### Post by josephus on 2007-03-28
it should be ndiswrapper -e net5211 instead of ndiswrapper -e net5211.inf

a lot of times when you have errors where they can't add or delete something it's because you need to run the command using sudo.

i'm pretty sure running feisty will solve your problems.  i actually tried out the beta today on the live cd,  it has some pretty nice features, including really easy access to the restricted modules which include the madwifi/hal drivers.

---

### Post by GSF1200S on 2007-03-28
YEAAAHHH!!!! I freakin got it!! Awesome!!!

First off, thanks to everyone who helped. The info about HAL was invaluable!! Pertaining to ndiswrapper, im still going to try and get more information about that. I would like to compile what Ive learned and perhaps put it somewhere (maybe a sticky?) so that everyone can try the same things and solve there problems.

By the way, after upgrading to Fiesty, I went to the synaptic package manager and downloaded madwifi and madwifi tools. I then had to restart. With a little tinkering (learning how madwifi had the network setup) I managed to get a connection. 

Thanks to all, and be looking for a wireless information post in a few days (for people who have the same problems I did). If any of you have suggested pages of info you can PM me or simply reply to this post.

---

### Post by stchman on 2007-03-30
> **GSF1200S said:**
> Ive managed to adapt to Edgy pretty well- Ive got NTFS3g working, my video card is working, and nearly everything else is working...

The one thing I need the most to break my XP dependency is a functioning wireless card. Ive tried to get this resolved in a former post, but I really didnt solve my problem. Ive tried using Ndiswrapper and windows drivers- nothing. Ive tried using madwifi (Atheros Communications is the Vendor, card made by Gigabyte (W101GT), and while it seems like im close, I still cant get it to work.

To be honest, im not sure I know what im looking for. When I had ndiswrapper and the graphic interface for it running, my drivers were listed as installed, but it said the hardware wasnt present. Trying the other path of madwifi, it seems like it installed through the  terminal fine, but I dont see any wireless card listed in networking, and I dont have a connection. For madwifi, Ive used the following resources:

[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

[http://packages.debian.org/testing/net/madwifi-tools](http://packages.debian.org/testing/net/madwifi-tools)

Ive looked through the forums, but most others could at least detect a network, or were running Fiesty. Im on Edgy 6.10 Ubuntu. I have to have wireless for my job... if anyone could lend a hand I would really appreciate it!

I know you have your card working, but the best drivers for that card are the madwifi drivers.  I have a procedure on my website laid out to get thta card up and running.  I am going to assume that the wireless card is built in.

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

Take a look at it.

---

### Post by ssc351 on 2007-04-05
Yo, I'm trying to get the same card working here are some problems i am running into:

Can you help?

dell640m@dell640m-laptop:~$ ndiswrapper -l
ar5211.sys : invalid driver!
atheros : invalid driver!
net5211 : invalid driver!

dell640m@dell640m-laptop:~$ ndiswrapper -e net5211
couldn't delete /etc/ndiswrapper/net5211: Inappropriate ioctl for device


lspci:

dell640m@dell640m-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)




dell640m@dell640m-laptop:~$ lsmod | grep ath
multipath               9856  0 
md_mod                 79764  7 raid10,raid456,raid1,raid0,multipath,linear


dell640m@dell640m-laptop:~$ lsmod | grep ndis
ndiswrapper           194608  0 
usbcore               134280  4 ndiswrapper,ehci_hcd,uhci_hcd

---

### Post by josephus on 2007-04-05
First unload the ndiswrapper module

```
sudo modprobe -r ndiswrapper
```

Then remove the invalid drivers from ndiswrapper

```
sudo ndiswrapper -e <driver_name>
```

in this case the invalid drivers are ar5211.sys, net5211, and atheros

After that you need to install the driver.  make sure you've downloaded the proper drivers and unpacked them.  Go into the same directory as that driver and

```
sudo ndiswrapper -i <driver>
```

the driver name is the file with .inf extension.  Upper/lowercase matters.  Checked if it worked with ndiswrapper -l.  If it worked, it'll give you the message: 'driver installed, hardware present'.  

Now load the ndiswrapper back into memory.  

```
sudo modprobe ndiswrapper
```

---

### Post by SlaughteredLamb on 2008-04-03
just wanted to dig this thread up to thank Josephus.  your method successfully got my wireless card on my laptop up and running in Ubuntu 7.10.  Much thanks!

---

