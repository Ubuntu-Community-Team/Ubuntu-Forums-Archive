---
title: "Wireless problems!!"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by MikeJ112 on 2007-06-13
Hi, I have just installed a wireless card into the computer. Booted up fine, but Ubuntu doesnt recgonise the card. lspci gives;

```
lspmike@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 02)
01:09.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
01:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:0b.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
mike@ubuntu:~$ 
mike@ubuntu:~$ 
```

Any help MUCH appreciated, am trying to get this PC set up for my brother!!

---

### Post by MikeJ112 on 2007-06-13
BTW, i am using this pc online wired!

---

### Post by matthewboh on 2007-06-13
Apparently the Marvell's are not supported with Linux drivers, so you're going to have to install ndiswrapper (which I have used and works).  Here's the how to [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

and the Marvell driver site [http://www.marvell.com/drivers/search.do]("http://www.marvell.com/drivers/search.do")

---

