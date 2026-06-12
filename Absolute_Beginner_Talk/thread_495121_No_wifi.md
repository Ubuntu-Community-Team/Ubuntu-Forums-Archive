---
title: "No wifi?"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by ~~Tito~~ on 2007-07-07
It worked  before i installed with the live cd but now it wont work?

HP Pavilion zv5000
ATI Mobility Raedion IGP 9000 64 mb
Pentium 4 3.00ghz, 3.0ghz
1.12gb ram

---

### Post by corney91 on 2007-07-07
Do you have a wireless button? When I switched to Ubuntu I thought that the button was not enabled because the light did not turn on but accidently pressing it may turn off your wireless without knowing. It may seem trivial but it stumped me.:)

---

### Post by ~~Tito~~ on 2007-07-07
Thats what i thought to but it wont turn on when i push it.

---

### Post by originald on 2007-07-07
Is your network card activated ?

If you go to System > Administration > Network you can check if it is activated from there.

OriginalD

---

### Post by ~~Tito~~ on 2007-07-07
Roaming mode?

---

### Post by corney91 on 2007-07-07
Not sure then, but you should check the configuration on your router. This seems simple but can also be the sources of problems, for example yesterday my router changed the wireless name and passphrase on it's own (well, it probably was something my dad did:p)

Also, you should check the Restricted Drivers Manager.

---

### Post by corney91 on 2007-07-07
> **~~Tito~~ said:**
> Roaming mode?

That should be ok

---

### Post by macogw on 2007-07-07
What kind of wireless card is it?&#12288;The specs you listed have nothing at all to do with wireless.  Your graphics card, processor, and RAM aren't going to affect wifi.

---

### Post by ~~Tito~~ on 2007-07-07
i think realtech or something
8011 or something i forgot

---

### Post by Vague on 2007-07-07
> **corney91 said:**
> Also, you should check the Restricted Drivers Manager.

+1

That was my guess.

---

### Post by originald on 2007-07-07
This link may help you, it is what I used to get my network going when I was having problems with WPA

[http://ubuntuforums.org/showthread.php?t=318539]("http://ubuntuforums.org/showthread.php?t=318539")

---

### Post by macogw on 2007-07-07
> **~~Tito~~ said:**
> i think realtech or something
8011 or something i forgot

that's probably 802.11 since that's the thing on all wireless stuff.  might be a protocol name or something, i dont know.  it's the wireless number to me :p

Type "lspci" (that's a little L not a big i at the beginning) in the Applications > Accessories > Terminal and post the output here

---

### Post by ~~Tito~~ on 2007-07-07
00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 16)
00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:07.0 USB Controller: NEC Corporation USB (rev 43)
02:07.1 USB Controller: NEC Corporation USB (rev 43)
02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)


That?

---

### Post by macogw on 2007-07-07
Yep!  This is the important line:
> 02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
The drivers are already installed, but Ubuntu's not allowed to install the firmware by default because Broadcom is a bunch of meanies.  To get the firmware:
> sudo apt-get install bcm43xx-fwcutter

---

### Post by ~~Tito~~ on 2007-07-07
ok thanks it installing now.
Do i need to install anything else?

---

### Post by ~~Tito~~ on 2007-07-07
Yes im connected and for somereason wine came back!!!!! YAY!!!!!

---

