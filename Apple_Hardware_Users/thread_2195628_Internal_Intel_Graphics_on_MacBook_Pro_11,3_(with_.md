---
title: "Internal Intel Graphics on MacBook Pro 11,3 (with Nvidia 750M)"
date: 2013-12-25
forum: Apple Hardware Users
---

### Post by kjano on 2013-12-25
Hi,

I would like to give it a last try. Was anybody able to get the Intel graphics card working on a Haswell MacBook Pro (11,3) that is also equipped with the Nvidia 750M? I am not even looking for a dual solution, just want to see if I can get the Intel graphics working at all. I tried various options but without any success.

Thanks,
Kjano

---

### Post by andreas.heider on 2014-01-01
Hi, see [http://lists.gnu.org/archive/html/grub-devel/2013-12/msg00442.html](http://lists.gnu.org/archive/html/grub-devel/2013-12/msg00442.html) and [http://forums.macrumors.com/showthread.php?p=18576213#post18576213](http://forums.macrumors.com/showthread.php?p=18576213#post18576213).

This enables the Intel GPU, but I haven't gotten the old outb commands in grub to switch the gmux to work yet, so you'll have to use GfxCardStatus in OS X to switch to the Intel card.

---

### Post by kjano on 2014-01-04
Great! Thanks. This made my day; I will give it a try.

---

### Post by mörgæs on 2014-01-04
If it solved your problem please mark the thread so.

---

### Post by peer_gynt on 2014-02-11
I can switch to the Intel GPU -- but only see a black screen, no matter what.  Any advise?  Thanks!

```

cameo ~ # uname -a
Linux cameo 3.14.0-031400rc2-lowlatency #201402092235 SMP PREEMPT Mon Feb 10 03:45:33 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

cameo ~ # lspci
00:00.0 Host bridge: Intel Corporation Crystal Well DRAM Controller (rev 08)
00:01.0 PCI bridge: Intel Corporation Crystal Well PCI Express x16 Controller (rev 08)
00:01.1 PCI bridge: Intel Corporation Crystal Well PCI Express x8 Controller (rev 08)
00:02.0 VGA compatible controller: Intel Corporation Crystal Well Integrated Graphics Controller (rev 08)
00:03.0 Audio device: Intel Corporation Crystal Well HD Audio Controller (rev 08)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d5)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0fe9 (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK107 HDMI Audio Controller (rev a1)
03:00.0 Network controller: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter (rev 03)
04:00.0 Multimedia controller: Broadcom Corporation Device 1570
05:00.0 SATA controller: Samsung Electronics Co Ltd Device 1600 (rev 01)

cameo ~ # cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD: :Off:0000:00:02.0
1:DIS:+:Pwr:0000:01:00.0

```

(this obviously is running on the Nvidia right now)

---

