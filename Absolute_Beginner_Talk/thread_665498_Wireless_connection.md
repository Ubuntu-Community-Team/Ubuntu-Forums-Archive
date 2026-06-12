---
title: "Wireless connection"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by ohioiom on 2008-01-12
I have just installed Ubuntu Linux 7.04 onto my laptop as a dual boot  system with WinXP Pro.SP2.
I have a wireless card BT Voyager 1065 PC card connected which works fine with Win XP, but doesn't appear to be connected in the Ubuntu prog. I am currently using an ethernet cable to connect. I thought perhaps the PC card needed installing into the Ubuntu prog.,but when I try to install from the CD I get the message.
_ERROR:NO SUITABLE APPLICATION _
"CANNOT OPEN /MEDIA/CDROM0/SETUP.EXE: NO APPLICATION SUITABLE FOR AUTOMATIC INSTALLATION IS AVAILABLE FOR HANDLING THIS KIND OF FILE"
Would someone please explain to me in 'Stupid people language' what the answer is.
Many thanks:confused:

---

### Post by fraser_m on 2008-01-12
The reason Ubuntu isn't installing the drivers is that is can't run .exe (Windows program) files.

Try opening up a terminal: Applications>Accessories>Terminal and type:

```
lspci
```

Then press Enter/Return.

Copy the output from that here and I'll try to help.

---

### Post by ohioiom on 2008-01-14
Fist of all I would like to apologise,  This being my first post I hadn't realised just how quickly I would get a reply. I had to log off due to a superior power, namely Petticoat Govnmt. I will now do as you instructed..:-
peter@peter-laptop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0b.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 02)
peter@peter-laptop:~$ 

Hope this helps

---

### Post by fraser_m on 2008-01-14
Aha!

Download [this file]("http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133") and double click it on your PC that needs the drivers. Then click Install, and then when it's finished, reboot. It should pick up the wireless signal.

Hope it helps, if it doesn't, tell us.

---

### Post by ohioiom on 2008-01-16
I downloaded the file and installed it, it found my PC card straight away, with both lights on I thought we were in business, but unfortunately I still wasn't connected and it told me restricted drivers were available, which turned out to be what I had just installed, but when I clicked ENABLE it told me it couldn't connect.
I then found an old Belkin dongle which I connected to a usb and I was on line straight away!! I would prefer to use a PC card, as they are less protrusive and therefore less vulnerable to knocks.I have ordered a copy of Ubuntu for Dummies so I can learn about it.

I have since tried to upgrade to Gutsy 7.10, via the update manager, but unfortunately it stopped part way through and I seem to have a bit of both!!, Perhaps that is why your fix couldn't connect! I would like to start again, but of course don't know how. I suppose like a lot of people I have been trying to run before I can walk and then  flounder around.

Thank you most sincerely for all your help and advice, it was appreciated.

---

