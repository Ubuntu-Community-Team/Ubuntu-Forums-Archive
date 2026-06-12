---
title: "no sound with new kernel update"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by mistergq on 2007-06-08
I was on vacation since Sunday.  Today I turned on my laptop saw updates, and installed.  I have had a restart since then and now I have no sound.  Anyone else with this problem?

---

### Post by tahuya_rat on 2007-06-08
No clues yet, please list your hardware, then you would want various outputs, but so far,  I can't help ya!:(

---

### Post by mistergq on 2007-06-08
Laptop: Gateway MX6447: here is a cut and paste from Gateway's website.
Processor 	AMD Turion™ 64 Mobile Technology MK-36
Operates at 2.0 GHz | 512 KB L2 Cache
HyperTransport™ technology at up to 1600 MHz
LCD Screen 	15.4-inch Ultrabright™ WXGA TFT (1280 × 800)
Chipset 	ATI RS485M
Memory 	1024 MB 533 MHz DDR2 (2 × 512)
Expandable to 2 GB
Total Slots: 2 DDR2 Slots | Available Slots: 0 DDR2 Slots
Video 	ATI Radeon® Xpress 1150 Graphics with up to 128 MB of Shared Video Memory
Audio 	High Definition 2 Channel Audio
Hard Drive 	120 GB 4200 RPM PATA hard drive
Optical Drive 	DVD+/-RW Multi-Format Double Layer (up to 8.5 GB)

Write maximum: 8X DVD +/-R, 6X DVD-RW, 8X DVD+RW, 2X DVD-R DL, 2.4X DVD+R DL, 24X CD-R and 16X CD-RW
Read maximum: 24X CD-R/RW/ROM, 8X DVD-R/RW/ROM, 4X DVD+/-R DL, RAM
Media Reader 	4-in-1 Digital Media Manager
Secure Digital (SD), Memory Stick, Memory Stick-Pro, and Multimedia card (MMC)
Modem 	56K ITU V.92 ready Fax/Modem
Network 	Integrated 802.11g Wireless LAN
Integrated 10/100 Ethernet
Interfaces 	

    * 4 - USB 2.0 Ports
    * 1 - VGA External Connector
    * 1 - S-Video Connector
    * 1 - IEEE 1394 port
    * 1 - RJ11
    * 1 - RJ45
    * Microphone In
    * Headphone / Audio Out
    * 1 - Kensington Lock Slot
    * 1 - AC Adapter Connector 

Pointing Device 	Integrated Synaptics Touchpad with Vertical Scroll Zone
PCMCIA 	1 - Type I or Type II; Card Bus
Battery 	6-cell Lithium-ion
Dimensions 	1.31 to 1.40-inches H × 14.09-inches W × 10.39-inches D
Weight 	6.32 pounds

---

### Post by Bohlio on 2007-06-08
I had this too, Go to System, preferances, sound, and make sure the playback device is set for the one you use. Mine was all set for autodetect and that wouldnt work. After that, I couldnt get the little noises from the login to work because it was using my onboard audio (I have a PCI Audio). All I did to get that working was disable the onboard audio from the BIOS.

---

### Post by mistergq on 2007-06-08
> **Bohlio said:**
> I had this too, Go to System, preferances, sound, and make sure the playback device is set for the one you use. Mine was all set for autodetect and that wouldnt work. After that, I couldnt get the little noises from the login to work because it was using my onboard audio (I have a PCI Audio). All I did to get that working was disable the onboard audio from the BIOS.problem is I don't know what to set it to other than autodetect.

---

### Post by Bohlio on 2007-06-08
try your different options, there is a test button so you will be able to quicky go through your choices.

---

### Post by mistergq on 2007-06-09
> **Bohlio said:**
> try your different options, there is a test button so you will be able to quicky go through your choices. sorry i didn't make that clear, I did, none of them worked.

---

### Post by abn91c on 2007-06-09
go to kmixer the slide the PCM bar all the way up, it will help to have an audio cd playing to monitor for sound. Also all the radio buttons should be on Green

---

### Post by mistergq on 2007-06-09
> **abn91c said:**
> go to kmixer the slide the PCM bar all the way up, it will help to have an audio cd playing to monitor for sound. Also all the radio buttons should be on Green well this is interesting, in the 16 kernel, I go into Kmix and only have master and igain or something like that.  Also, the only tab I have is Output, no input or switches.  In 15, I have Master, PCM, Front, Surron, and Capture Mix.  The tabs I have are output, input, and switches.

I have a feeling there is something wrong with the kernel.

---

