---
title: "Built in ethernet not recognized, new install."
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by justaboutnormal on 2007-03-29
I just installed Ubuntu on my desktop but the built in Ethernet device isn't recognized.  I opened the Networking tool and only the modem was present.  

The motherboard I have is a PCChips P23G Socket 775
I installed Ubuntu 6.10

---

### Post by overdrank on 2007-03-29
> **justaboutnormal said:**
> I just installed Ubuntu on my desktop but the built in Ethernet device isn't recognized.  I opened the Networking tool and only the modem was present.  

The motherboard I have is a PCChips P23G Socket 775
I installed Ubuntu 6.10

Hi can you post the output of the command lspci in the terminal. This should tell you the  type of nic card you have!

---

### Post by justaboutnormal on 2007-03-29
lspci output

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
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

---

### Post by overdrank on 2007-03-29
Your mb specs say you have a rj-45 lan port but it is not showing up. Are you sure it is enabled in bios?

---

### Post by justaboutnormal on 2007-03-29
I don't know, how do I do find out?

---

### Post by overdrank on 2007-03-29
> **justaboutnormal said:**
> I don't know, how do I do find out?

You have to enter the bios on the system. If you have the manual for you computer it will explain how this is done. Let me ask this question first, did you have a operating system on this computer that had a working lan before the installation of ubuntu?

---

### Post by justaboutnormal on 2007-03-29
No, I didn't this is a brand new computer that hasn't had any OS on it before.

---

### Post by Maestro23 on 2007-03-29
> **justaboutnormal said:**
> No, I didn't this is a brand new computer that hasn't had any OS on it before.

Here's the website and manual for your mobo. Should tell you how to enter your BIOS.

[http://www.pcchips.com.tw/PCCWeb/Products/ProductsDetail.aspx?MenuID=16&LanID=2&DetailID=370&DetailName=Manual](http://www.pcchips.com.tw/PCCWeb/Products/ProductsDetail.aspx?MenuID=16&LanID=2&DetailID=370&DetailName=Manual)

---

### Post by overdrank on 2007-03-29
> **justaboutnormal said:**
> No, I didn't this is a brand new computer that hasn't had any OS on it before.

Ok if you have the manual it will explain how to enter your bios for the motherboard and then you can navigate to enable the lan. If you dont have a manual you can download one from the PC site. Good luck!

---

### Post by justaboutnormal on 2007-03-30
The Ethernet LAN isn't listed, there is an updated BIOS from the website, but I don't know how to install it.  It's downloaded, do I just put the ROM file on a cd and boot to it?

---

### Post by justaboutnormal on 2007-03-30
Also, someone else with this motherboard had the same problem and fixed it by upgrading the BIOS.

---

### Post by michwill on 2007-04-05
There's not really an option to "enable" LAN, in this BIOS per se.  However, to the extent possible it's enabled in the BIOS on mine.  I still have the issue. A fresh 6.10 install and the onboard ethernet is not installed.  I have no floppy drive so the option to upgrade the bios in that fashion is out (which is pretty retarded btw).

Any ideas?

---

### Post by michwill on 2007-04-05
Personally, I had to install Windoze, flash the bios, then reinstall ubuntu.  It would then recognize the ethernet.

It irks me to no end that companies force users to use Windows to perform operations that should be OS indifferent.

. . .anywho, this seems to work.

---

