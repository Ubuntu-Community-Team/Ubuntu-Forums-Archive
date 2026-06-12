---
title: "k42j Wireless problem."
date: 2011-05-28
forum: Asus Ubuntu Support (CLOSED)
---

### Post by tamnk on 2011-05-28
i use asus k42j and ubuntu 11.04 but i can't connect wireless although see network? now what must i do? help me!!!!

---

### Post by uRock on 2011-05-28
Hello and welcome to the forums,

Which k42j model is it? There are several models [http://www.asus.com/Search/?SearchKey=k42j](http://www.asus.com/Search/?SearchKey=k42j)

Can you open a terminal, then copy and paste the following command, then post the terminal's response here? ```
lspci
```

PS. I moved your post its own thread.

Regards,
uRock

---

### Post by misterblobby on 2011-06-03
Not a fix but.....

I have had similar issues with ASUS N73J with Windows 7 dual boot.

Mine does connect to the wireless most of the time, but will sometimes continuously search just after startup - this seems to happen more often when windows has been hibernated or if it was the last OS used.

Rebooting seems to get rid of the problem, but I would appreciate a fix too if anyone has one. 

Booting ubuntu twice is still faster than starting up windows once, so no huge problem!

---

### Post by uRock on 2011-06-03
> **misterblobby said:**
> Not a fix but.....

I have had similar issues with ASUS N73J with Windows 7 dual boot.

Mine does connect to the wireless most of the time, but will sometimes continuously search just after startup - this seems to happen more often when windows has been hibernated or if it was the last OS used.

Rebooting seems to get rid of the problem, but I would appreciate a fix too if anyone has one. 

Booting ubuntu twice is still faster than starting up windows once, so no huge problem!Can you post the output of **lspci** in a terminal, so that we can see which chip set the Asus card is using?

---

### Post by misterblobby on 2011-06-03
Hope this helps: (from N73J)

00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df0 (rev a1)
01:00.1 Audio device: nVidia Corporation GF108 High Definition Audio Controller (rev a1)
02:00.0 Multimedia controller: Philips Semiconductors SAA7231 (rev ca)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 USB Controller: Fresco Logic Device 1400 (rev 01)
06:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)

---

### Post by uRock on 2011-06-03
> **misterblobby said:**
> Hope this helps: (from N73J)

Are you using 11.04 or an older version?

---

### Post by misterblobby on 2011-06-03
11.04

---

### Post by uRock on 2011-06-03
If you are using 11.04, then installing the **linux-backports-modules-net-natty-generic** package should do the trick with your chip set. I am getting this info from [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773154"), where one of the last comments claims it fixed the problem. You can install via the Ubuntu Software Center or via the terminal with the following command; ```
sudo apt-get install linux-backports-modules-net-natty-generic
```

As for 10.04 and 10.10 here is the Ubuntu documentation page explaining what to install. [https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285)

---

### Post by misterblobby on 2011-06-03
Thanks a heap uRock,

It's installing now, I'll put up another reply in a week on whether the issue is gone.

---

### Post by uRock on 2011-06-03
> **misterblobby said:**
> Thanks a heap uRock,

It's installing now, I'll put up another reply in a week on whether the issue is gone.

That'll be great. It'll make life easier when someone searches for the same issue and can read that the fix works for others.:)

---

### Post by misterblobby on 2011-06-13
Just a quick update: The above fix worked fine on my N73J.

---

