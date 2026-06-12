---
title: "Lan card not detected  (RTL 8139D)"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Aerin on 2007-08-04
Hello, 

I am a new user and this is my first time at linux, I've installed Ubuntu Feisty Fawn just a week ago. My ethernet card is a RTL-8139D and works fine on Windows XP, but its not detected in Ubuntu. I've googled extensively and found a lot of people have the same problem. The card is supposed to be a fake btw according to some sites. Most of them have replaced the card, and only one or two have managed to get it to run in Ubuntu. My vendor would not replace it as it has been running in Windows prior to installing Ubuntu. 

I came upon this thread : [http://ubuntuforums.org/showthread.php?t=461330&page=5&highlight=romihim+RTL8139](http://ubuntuforums.org/showthread.php?t=461330&page=5&highlight=romihim+RTL8139) where another user had a similar problem and has managed to fix it. So I know that atleast there's a hope of getting it to work somehow although its a fake. 

My outputs are identical to people with the same problem. 

ifconfig:
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

```

lspci:
```

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 02)
01:07.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)[B]
01:09.0 Ethernet controller: Hangzhou Silan Microelectronics Co., Ltd. RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor (rev 01)[/B]
01:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
01:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

```

dmesg|tail```

[   82.333048] usb 1-1: device not accepting address 8, error -71
[   82.444983] usb 1-1: new full speed USB device using uhci_hcd and address 9
[   82.852746] usb 1-1: device not accepting address 9, error -71
[   82.894418] Bluetooth: RFCOMM socket layer initialized
[   82.894454] Bluetooth: RFCOMM TTY layer initialized
[   82.894460] Bluetooth: RFCOMM ver 1.8
[  102.307070] NET: Registered protocol family 10
[  102.307348] lo: Disabled Privacy Extensions[B]
[  296.186413] 8139too Fast Ethernet driver 0.9.28
[  323.044229] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)[/B]
```

lsmod:
```

Module                  Size  Used by
... 
8139cp                 25088  0 
8139too                27648  0 
mii                     6528  2 8139cp,8139too
...

```

pppoeconf says that there is no working ethernet card, and modconf is not working. 

They have supplied a cd with a folder called LINUX with a a sc90231.c and a makefile. However the readme with it says only kernel 2.4 and 2.5 are supported. So I've downloaded the files for the 2.6 kernel from [http://gurukumara.googlepages.com/](http://gurukumara.googlepages.com/) as said in the previous thread. Now I'm guessing I'll have to compile the driver/kernel module to get it to work as romihim probably did. 

I've no idea how to go about doing it. Does anyone have any other ideas to get my card to work? How do I install the driver? Could anyone help me with this? Thanks for your help.

---

### Post by GMachine_24 on 2007-08-04
hi:

you could have a network card that uses a realtek chip but is made by another manufacturer. that doesn't necessarily mean your network card is fake.

try this command and post the results:

<code>

user@computer:~$sudo lshw

</code>

it seems as if your card is working and that it is recognized by linux/ubuntu or it would not show up on your pci scan (lspci)

gm

---

### Post by GMachine_24 on 2007-08-04
Hello again:

It seems your problem might be related to having two drivers for your lan card. [This I gauged from reading numerous Internet posts about similar problems.

This seems to be the driver you want (and it is the one installed on the Compaq Presario R3000 laptop I am using with a Realtek 8139x chip).

This driver:   296.186413] 8139too Fast Ethernet driver 0.9.28

(8139too instead of 8139cp)

I'm not familiar with installing or removing either driver - but you might try a Net search and see what comes up. Two drivers for one device often makes the device inoperable.

I also recommend [http://wicd.sourceforge.net](http://wicd.sourceforge.net) to help configure your network (if you have installed the gnome network manager you must remove it).

Don't give up - I banged my head against the wall for awhile before I got my wireless to work. Now it works all the time.

gm

---

### Post by Aerin on 2007-08-05
Thanks for your reply. Output of lshw: 

 ```
         
......
             *-network UNCLAIMED
                description: Ethernet controller
                product: RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor
                vendor: Hangzhou Silan Microelectronics Co., Ltd.
                physical id: 9
                bus info: pci@01:09.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64 maxlatency=40 mingnt=20
                resources: iomemory:fc9ff800-fc9ff8ff ioport:d800-d8ff irq:11
......

```

From googling a lot, I think rmmod is used to remove a driver. I havent tried it yet. And when I type sudo modprobe 8139too, nothing happens, but when I type sudo modprobe 8139cp, some error pops up and it says permission denied or something. And in lib/.../kernel/drivers/net,  8139cp.ko and 8139too.ko both are present. 

In the driver cd, sc92031.c and a makefile is there with a readme saying thats the driver for linux. Will I have to compile this and how do I do it? Would I have to rebuild the kernel for adding this driver /module? I think thats the only way I can fix it.

Thanks again for replying.

---

### Post by Aerin on 2007-08-05
I found another thread detailing this problem: 
[http://broadbandforum.in/bsnl-dataone-broadband/3712-dataone-intex-lan-card-linux/](http://broadbandforum.in/bsnl-dataone-broadband/3712-dataone-intex-lan-card-linux/)

Anyway, I managed to compile the driver for the 2.6 kernel, and then insmod-ed the generated .ko file. Then I saw that lsmod shows that this module is running, but has a 0 value in the 'used' field, and nothing happens... ifconfig still shows only lo, and pppoeconf says there is no working ethernet card. I'm lost here. :(

---

