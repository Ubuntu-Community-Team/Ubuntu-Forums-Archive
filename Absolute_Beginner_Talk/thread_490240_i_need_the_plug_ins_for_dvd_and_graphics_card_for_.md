---
title: "i need the plug ins for dvd and graphics card for tremulous can you pleace help"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by EnGorDiaz on 2007-07-02
i dont know the name of the graphics card but i think its a geforce ive had to install the system 3 times due to ompletely recking the graphics and plus my dvd player wont work can someone help my dvd player is an lg when ever i try to play sumthing it says i need plug ins what plug ins please please just give me the plug ins for the dvd player atleast ive been pulling my hair out practicaly ive been working my *** off trying to get it up but everything seems to just come up with errors

---

### Post by overdrank on 2007-07-02
> **EnGorDiaz said:**
> i dont know the name of the graphics card but i think its a geforce ive had to install the system 3 times due to ompletely recking the graphics and plus my dvd player wont work can someone help my dvd player is an lg when ever i try to play sumthing it says i need plug ins what plug ins please please just give me the plug ins for the dvd player atleast ive been pulling my hair out practicaly ive been working my *** off trying to get it up but everything seems to just come up with errors

Hi to find out what you video card is, use the command [HTML]lspci[/HTML] in the terminal (located under applications, accessories,terminal)
As for the dvd try these link
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)
Good luck! :D

---

### Post by seshomaru samma on 2007-07-02
to find out what card you have put this in a terminal:
```
lspci | grep VGA
```
and press enter...

to play DVD you need some codecs you can get them by putting this line in a terminal:
```
sudo apt-get install libdvdcss2
```
before that you need add extra repositories 
read all about it [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

more about DVD codecs [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability")

---

### Post by EnGorDiaz on 2007-07-02
james@james-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

unichrome not compatible damn it

---

### Post by overdrank on 2007-07-02
> **EnGorDiaz said:**
> james@james-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

unichrome not compatible XXXX it

Sorry for the incompatibility issue but remember there are adolescents here! So whatch what you are typing!:(

---

### Post by ubuntu27 on 2007-08-24
Somebody needs help here
Almost similar to my friends problem which I am trying to help.

[http://ubuntuforums.org/showthread.php?p=3246538](http://ubuntuforums.org/showthread.php?p=3246538)

**BUMP**

---

