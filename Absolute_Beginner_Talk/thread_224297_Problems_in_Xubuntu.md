---
title: "Problems in Xubuntu"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by Yosefrajwulf on 2006-07-27
Hi!

I don't know if this is the right place to post this, but since I'm new to Linux (this is my first installation) I thought this was the forum to do so.

Recently I just installed Xubuntu in a very old machine (Celeron 500 Mhz, 128 RAM), it works relatively fine apart form a few problems:
a) No sound (I think the card is detected but the drivers are not loaded, see the output of lspci and the end of the post)

b)I think I'm having trouble with my language configuration since some parts of the system are in Spanish and some in English.

c)I haven't figured out how to make the system recogize my usb flash drive and my digital camera.

d)The graphical interface to administer users (Aplications->System->Users and Groups) is not working properly. Each time I open it I get an error message with something like this:
There was an error while executing the script in the backend


As mentioned before, here is the ouput of the lspci command.

0000:00:00.0 Host bridge: Intel Corporation 82810 GMCH [Graphics Memory Controller Hub] (rev 02)
0000:00:01.0 VGA compatible controller: Intel Corporation 82810 CGC [Chipset Graphics Controller] (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 01)
0000:00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 01)
0000:00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 01)
0000:01:08.0 Multimedia audio controller: Rockwell International Riptide PCI Audio Controller
0000:01:08.1 Communication controller: Rockwell International Riptide HCF 56k PCI Modem
0000:01:08.2 Input device controller: Rockwell International Riptide PCI Game Controller
0000:01:09.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)

Thanks for your help.

P.S. Forgot to mention that if i run Applications->Terminal, this opnes and instantly close the terminal window. However, if I open it via Applications->System->Terminal it works just fine. Really weird!

---

### Post by molly_001 on 2006-07-27
When I have installed Xubuntu on to a very old machine (PIII 433MHz, 96MB RAM) my experience was the same on almost every point.  I want to mention before I forget that some of the issues you describe can likely be fixed by using the Alternate Install CD for Xubuntu installer instead of Live-CD installer.

a) The sound card you have was exactly the same as mine: Rockwell Riptide combined modem and sound PCI card.  After many days of experimentation and forum queries I learned that getting this card to work on X/Ubuntu just wasn't going to happen.  You'll need to put a more updated PCI sound card in there.

c) same with support for USB.  However, when I used the Alternate Install CD, I was then thereafter able to use USB 1.1. 

d) overall your install sounds slightly corrupted.

---

### Post by dolby on 2006-07-27
b) its probably because not all of xfce has been translated to spanish. 

the xfce forums might be able to help u more at least at the time being with problems regarding their desktop..

---

### Post by Yosefrajwulf on 2006-07-27
>>"When I have installed Xubuntu on to a very old machine (PIII 433MHz, 96MB RAM) my experience was the same on almost every point. I want to mention before I forget that some of the issues you describe can likely be fixed by using the Alternate Install CD for Xubuntu installer instead of Live-CD installer."

Actually, I installed Xubuntu using the alternate cd. I couldn't do it with the Live CD (it got stuck at some point, and the CD was not faulty since I checked this before)


>>"a) The sound card you have was exactly the same as mine: Rockwell Riptide combined modem and sound PCI card. After many days of experimentation and forum queries I learned that getting this card to work on X/Ubuntu just wasn't going to happen. You'll need to put a more updated PCI sound card in there."

I had hoped that this could be solved since I in [http://kmuto.jp/debian/hcl/](http://kmuto.jp/debian/hcl/) I saw that the sound part of the  had a driver and it was reported as working under linux. However it seems not to be the case under Xubuntu (from your experience).

>>"c) same with support for USB. However, when I used the Alternate Install CD, I was then thereafter able to use USB 1.1.
d) overall your install sounds slightly corrupted."

Sounds strange, but if you consider so, then should I reinstall? (or is there a shorter way to fix this? I think the alternate installation disc has an option for this)
Actually, the strange thing is that I have apart from the cd-rom unit of the pc, an external (via usb) cd-rw unit that seems to be working just fine.

---

### Post by molly_001 on 2006-07-28
Yosefra --
 
Whether you choose to re-install is certainly your choice.  One thing I can tell you after installing and re-installing X/Ubuntu on 3 machines during the last 30 days: Reinstallation is very easy if you follow the separate /home partition.  You can reinstall Xubuntu as many times as you like, and not lose any of your data, if you choose to put /home in a separate directory.  There are tutorials for this, but let me know if you want me to point the way to some.

---

### Post by Yosefrajwulf on 2006-07-28
Great Molly_001!
I would be very thankful for it.

---

### Post by viper on 2006-07-29
That would be a gr8 tutorial to came you please also pint me in the right direction. Thanx....

---

