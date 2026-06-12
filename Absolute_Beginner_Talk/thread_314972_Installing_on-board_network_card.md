---
title: "Installing on-board network card"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by littlefair on 2006-12-08
I have recently installed ubuntu 6.10 but it didn't recognise my ethernet card, it's an onboard 10/100 on the gigabyte GA-M61VME-S2 motherboard. I am a complete newbie to linux. I don't know much at all!! forcedeth is mentioned alot on the web but no idea how to install anything! 

thanks.

---

### Post by taurus on 2006-12-08
You can't connect to the net even with the LiveCD!  What are the outputs of these two commands from a terminal, Applications -> Accessories -> Terminal?

```
lspci
ifconfig
```

---

### Post by littlefair on 2006-12-08
j@j-linux:~$ lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 03ea (rev a1)
00:01.0 ISA bridge: nVidia Corporation Unknown device 03e0 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 03eb (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 03f5 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 03f1 (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 03f2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation Unknown device 03f3 (rev a1)
00:06.0 IDE interface: nVidia Corporation Unknown device 03ec (rev a2)
00:07.0 Bridge: nVidia Corporation Unknown device 03ef (rev a2)
00:08.0 IDE interface: nVidia Corporation Unknown device 03f6 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 03e9 (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 03e9 (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation Unknown device 03d2 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
01:06.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 04)
01:06.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
j@j-linux:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5220 (5.0 KiB)  TX bytes:5220 (5.0 KiB)

---

### Post by linuchsan on 2006-12-08
Can you check if your onboard network is enabled in the bios?

---

### Post by littlefair on 2006-12-08
It works in windows (it's what I'm using now!) !

---

### Post by linuchsan on 2006-12-08
Try the sis190 module

---

### Post by littlefair on 2006-12-08
how do you do that :oops: ?

thanks :)

---

### Post by linuchsan on 2006-12-08
sudo modprobe sis190

---

### Post by littlefair on 2006-12-08
unfortunately that didn't work. assuming you don't have to do anything else other than type the above! 

Both lspci and ifconfig show the same results as before!

---

### Post by linuchsan on 2006-12-08
oops..sorry...i think you have the Realtek 8201 phy chip installed

---

### Post by linuchsan on 2006-12-08
try modprobe forcedeth, and restart your network.

---

### Post by linuchsan on 2006-12-08
Try sudo modprobe forcedeth, and restart your network

---

### Post by littlefair on 2006-12-08
I don't think this is going to work! 

should rpm <whatever> work? it says command not found? 

kernel-devel is also not installed, should it be? it's not on my cd?!

---

### Post by linuchsan on 2006-12-08
Have you tried the forcedeth module!?
rpm is more for an other distro
What source did you find for the nic?

---

### Post by littlefair on 2006-12-08
I may have done the forcedeth module :) I am a complete newbie to linux, 2 days and counting :)

I got some nvidia thing! nv_mcp55_linux..... to do with nforce!

sorry if this makes no sense!

---

### Post by linuchsan on 2006-12-08
so...after sudo modprobe forcedeth, and /etc/init.d/networking restart ,what happend? what does ifconfig say?

---

### Post by littlefair on 2006-12-08
when i did the restart it said no such device (eth01 -wlan) and then ifconfig was exactly the same!

---

### Post by linuchsan on 2006-12-08
No..do not restart. first see if it works.
sudo modprobe forcedeth, and /etc/init.d/networking restart

---

### Post by mr.v. on 2006-12-08
I'm new to linux too but I seem to have found others with a solution). According to your manufacturer you have a Realtek RTL8201 phy network card. And according to this page there can be a problem with these:
[http://www.brownhat.org/sis900.html](http://www.brownhat.org/sis900.html)
but first things first...type the following in the terminal window exactly:
**cat /var/log/dmesg | eth0**
and post the output...let's see if this problem is happening to you.

P.S. (**cat** basically just spits out the /var/log/dmesg file word-for-word which are all the boot messages and other things stored into a file so you can peruse at your convenience. we then "pipe" that output using the | character (above the backslash) into a program called **grep**. **grep** is cool, it basically just lets you search all those files for a line of text that contains "eth0" or your default ethernet controller and spits that out instead.

---

### Post by littlefair on 2006-12-08
> **linuchsan said:**
> No..do not restart. first see if it works.
sudo modprobe forcedeth, and /etc/init.d/networking restart

Nothing changes in the ifconfig!

Mr.V,

It says eth0 command not found when typing the 'cat /var...' out

---

### Post by mr.v. on 2006-12-08
>It says eth0 command not found when typing the 'cat /var...' out

it says that because I'm an idiot...
type:
cat /var/log/dmesg | grep eth0
I forgot the grep!

---

### Post by kaito on 2006-12-09
I might be having the same problem. I just installed Ubuntu Dapper drake server and everything else went smoothly but ethernet card was not found. I'm also a newbie here so I have no idea how to fix this.

The ethernet on board is Realtek 8201CL

And BTW:
cat /var/log/dmesg | grep eth0
didn't print a line...

Does anybody know how to fix this?

---

### Post by mr.v. on 2006-12-09
how about trying
**[FONT="Courier New"]modprobe sis900[/FONT]**
instead of sis190?

another thread somewhere in the abyss said that may work. Ultimately, this SHOULD be covered by the nvidia drivers. This page lets you download the drivers...
[http://www.nvidia.com/object/linux_nforce_1.11.html](http://www.nvidia.com/object/linux_nforce_1.11.html)
but none are precompiled for ubuntu. It includes the source code for forcedeth called forcedeth.c

maybe the driver included with ubuntu is a bit older than this one.

I wonder if perhaps you could compile the forcedeth.c file from teh 1.11 file and then use that module when you run modprobe forcedeth or just use one of the precompiled modules from a distribution that uses the same linux kernel. We'll need someone more advanced than I am to comment on this though

---

### Post by kaito on 2006-12-10
This same problem with my ethernet-card (RealTek 8201CL) has been noticed a long time ago [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/5820]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/5820")
with Kernel 2.6.15. Is Dapper still using the same Kernel and is this fixed in newer Kernels? How do I know?

---

### Post by mr.v. on 2006-12-10
you can see what kernel version you are using by opening up a terminal window and typing:
**uname -r**

did **modprobe sis900** not work?

---

### Post by mr.v. on 2006-12-10
If there really is a problem with this hardware and it doesn't look like it's getting fixed...you may have to shell out $30 for an intel or 3com adapter. It may be worth the $30 to save your hair =) (i know it's a cop out answer...I hope someone else more knowledgeable can help you better on this...but if not you may want to consider a more "linux compatible" network card).

---

