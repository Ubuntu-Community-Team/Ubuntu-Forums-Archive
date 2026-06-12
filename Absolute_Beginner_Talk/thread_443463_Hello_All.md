---
title: "Hello All"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by warpedreality on 2007-05-14
Hello Everyone!

Awesome forum.. I love the ppl here. I'm still a lurker and haven't posted anything yet. They just gave me a brand new Thinkpad T60p at work and I knew what had to be done :). Everyone's like "oh linux is so hard.. you'll never find all the drivers.." .. I'm stumbling my way around.. tried some stuff around the forums.. screwed something up.. reinstalled Ubuntu all over again :)

Couple of things I might need help with ..

1. Info on how to get my ATI Mobility FireGL v5200 card to work properly and Beryl..(read somewhere around how to disable restricted drivers.. didn't quite make it work..)

2. IBM uses Cisco-LEAP for wireless networking security.. I found this WICD that supports LEAP for Ubuntu.. haven't tried it out yet.. might need help if it doesn't work. I have a Intel WLAN card..(

Here's the **lspci** from my config
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M56GL [ATI Mobility FireGL V5200]
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
```

Would appreciate if someone could give me a headsup on any potential issues I might face..

Who knows.. I might post a step-step Ubuntu 7.04 desktop on a Thinkpad t60p soon.. :)

---

### Post by starcraft.man on 2007-05-14
For your first question... you can go here for a [guide to set up Beryl with ATI]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29"). 

To install your drivers go to [Envy.]("http://albertomilone.com/nvidia_scripts1.html") Download the 0.9.3 debian, double click, install, and then go Applications > System Tools > Envy. Then answer yes to any prompts from Envy. Then reboot and done (if everything goes well, ATI is a headache)

If you already installed drivers, go right to beryl guide. Have fun with it, I love beryl :)

I don't have the answer to your wireless question, I keep my desktop on a line, its just easier and I can't get dropped/interfered with.

---

### Post by warpedreality on 2007-05-14
thx!! will try that out.. 

Oh..I forgot to mention Bluetooth.. I have a Nokia N70 and a Nokia N95(coming in tomorrow). I sync,copy,transfer files from my N70 with my other thinkpad T41p('dos XP Pro) via Bluetooth and the Nokia PC Suite Connect application.

It's fine if I'm not able to use any specific 'application' with Ubuntu, but I just need to be able to switch on the Bluetooth on my T60p and like push files from my phone into the laptop.. and push files back from the laptop into the phone..

PS: When my N95 comes in tomorrow.. I'l try connecting the USB cable and see if anything works.. I lost the N70 connection cable 8-|

---

### Post by stchman on 2007-05-14
> **warpedreality said:**
> Hello Everyone!

Awesome forum.. I love the ppl here. I'm still a lurker and haven't posted anything yet. They just gave me a brand new Thinkpad T60p at work and I knew what had to be done :). Everyone's like "oh linux is so hard.. you'll never find all the drivers.." .. I'm stumbling my way around.. tried some stuff around the forums.. screwed something up.. reinstalled Ubuntu all over again :)

Couple of things I might need help with ..

1. Info on how to get my ATI Mobility FireGL v5200 card to work properly and Beryl..(read somewhere around how to disable restricted drivers.. didn't quite make it work..)

2. IBM uses Cisco-LEAP for wireless networking security.. I found this WICD that supports LEAP for Ubuntu.. haven't tried it out yet.. might need help if it doesn't work. I have a Intel WLAN card..(

Here's the **lspci** from my config
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M56GL [ATI Mobility FireGL V5200]
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
```

Would appreciate if someone could give me a headsup on any potential issues I might face..

Who knows.. I might post a step-step Ubuntu 7.04 desktop on a Thinkpad t60p soon.. :)

1.  Use Envy to install ATI drivers.

2.  Follow my procedure to install madwifi in Ubuntu.  [http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

Hope this helps.

---

### Post by warpedreality on 2007-05-14
I see only WPE, WPA and WPA2 listed on your site.. what about LEAP protocol? would I be able to use madwifi to configure LEAP?

---

### Post by stchman on 2007-05-14
> **warpedreality said:**
> I see only WPE, WPA and WPA2 listed on your site.. what about LEAP protocol? would I be able to use madwifi to configure LEAP?

I don't know much about LEAP so I cannot help you with that.  WPA and WPA2 should be way more security than you need for home use.  From what I have read LEAP is more vulnerable than WPA since it uses WEP style keys.

---

