---
title: "[SOLVED] Wireless"
date: 2008-10-09
forum: Apple Hardware Users
---

### Post by xiaoqiangwj on 2008-10-09
Can anyone help me set up the wireless? I just installed ubuntu on my macbook pro. the wireless connection is weird. I can't connect to any network which require password. please help!:-D
It keeps telling me the password is wrong,but im sure I got it right. I am using the BELL Canada router.
Thanks!

---

### Post by joseph2008 on 2008-10-10
Wireless communication is the transfer of information over a distance without the use of electrical conductors or "wires". The distances involved may be short (a few meters as in television remote control) or very long (thousands or even millions of kilometers for radio communications). When the context is clear the term is often simply shortened to "wireless". Wireless communications is generally considered to be a branch of telecommunications.
______________________________________________________________
[LA Flowers](http://www.florist-flowers-roses-delivery.com/california/los_angeles_ca.html) [low rate loans](http://www.cheaponline-loans.co.uk/) [penedes](http://www.vilafrancadelpenedes.com) [ringback tones](http://www.myringtoneshub.com/)

---

### Post by hajk on 2008-10-10
To the OP: what model MBP do you have? If it's the latest 4,1 model, with the Broadcom 4328 (rev 05) wireless chip, then you should consider using the new Broadcom "wl" driver, there is a sticky post in the Networking subforum about how to install it. There's also a recent post about it in this Apple subforum.

---

### Post by xiaoqiangwj on 2008-10-10
Thanks for your reply.:) I'm not sure which one I have, but here is the profile of the wireless apater.

AirPort Card Information:

  Wireless Card Type:	AirPort Extreme  (0x168C, 0x87)
  Wireless Card Firmware Version:	1.4.4
  Current Wireless Network:	BELL578
  Wireless Channel:	3


and the cpu is the 2.4GHz intel Core 2 Duo.

I tried to use the new Ubuntu 8.10 today, it looks like they have the driver included. But if I try to connect to any network, it will stuck when "requesting address". Any ideas? Thanks!

---

### Post by cyberdork33 on 2008-10-10
> **xiaoqiangwj said:**
> Thanks for your reply.I'm not sure which one I have, but here is the profile of the wireless apater.

AirPort Card Information:

  Wireless Card Type:    AirPort Extreme  (0x168C, 0x87)
  Wireless Card Firmware Version:    1.4.4
  Current Wireless Network:    BELL578
  Wireless Channel:    3


and the cpu is the 2.4GHz intel Core 2 Duo.
See the "Before you post" link in my signature to identify your mac version.

The output of the command 'lspci' in ubuntu would be better in helping us determine which wifi card you have, but I think you have an Atheros card.

---

### Post by xiaoqiangwj on 2008-10-10
~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
0b:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)
0c:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
0d:03.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 02)


Thanks!:KS:KS

---

### Post by xiaoqiangwj on 2008-10-10
Problem solved. Try to install the mad dirvers( I reinstalled ubuntu). It works for me. Thanks for everyone!!:KS:KS:KS

---

### Post by cyberdork33 on 2008-10-10
> **xiaoqiangwj said:**
> Problem solved. Try to install the mad dirvers( I reinstalled ubuntu). It works for me. Thanks for everyone!!:KS:KS:KS
Please mark this thread as solved from the thread tools menu at the top of the page.

---

### Post by xiaoqiangwj on 2008-10-11
but it looks like there are still some problems. Its not that stable.It will disconnect automatically every half an hour, and I need to reconnect it by myslef. Any ideas? Thanks

---

### Post by cyberdork33 on 2008-10-11
there is also the ath9k driver that you can try.
[http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097)

---

### Post by xiaoqiangwj on 2008-10-12
> **cyberdork33 said:**
> there is also the ath9k driver that you can try.
[http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097)

That's the one I used before, and I can't connect to any security network, but I dont know why it works well now. Thanks!

---

