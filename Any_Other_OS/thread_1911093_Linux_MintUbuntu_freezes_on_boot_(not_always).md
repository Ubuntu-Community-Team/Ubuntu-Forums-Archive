---
title: "Linux Mint/Ubuntu freezes on boot (not always)"
date: 2012-01-18
forum: Any Other OS
---

### Post by lex_man on 2012-01-18
Hello. I have a computer with following configuration: 

Case: CoolerMaster Elite 334, black 
PSU: CORSAIR 550W, VX Series CMPSU-550VXEU 
MBO: Gigabyte MA790XT-UD4P, AMD 790X+SB750, S. AM3, 8xSATA RAID, DDR3 
Memory: 2 x DDR3 4GB (2x2GB) Corsair, 1600MHz, 9-9-9-24, COR-TW3X4G1600C9DHX 
CPU: AMD Phenom II X4 955 Black Edition, socket AM3, BOX 
Cooler: Scythe Katana 3 
HDD: WD 1TB, 1001FALS, SATA II, 32Mb Cache, WD Caviar Black 
HDD: WD 1.5TB, 15EARS, WD Caviar Green 
DVD: DVD/RW Pioneer DVR-117FBK, 22x, ATA 
GPU: MSI HD 6850 OC Cyclone, 1GB,DVI,HDMI,DX11 
Additional: Controller TRANSCEND PDU3 USB3.0, PCI Express x1 2ch 

My system is dual boot - Linux Mint & Windows 7 (used rarely for  Steam). Until approx. 10 days ago I used older version of Mint (Helena  or Isadora, not sure) and everything worked fine. However, I recently  tried to reinstall my system, and that didn't finis very well. First I  tried to install latest version of Linux Mint - version 12, Lisa.  Booting from DVD (which is not faulty) worked fine every time I tried  it. Also, booting from any other CD/DVD with any Linux distro worked  without problem. Installing also went well but once installed on my PC -  I could not boot system, no mather what I tried. I even reinstalled  Mint once again, with some minor changes on my partition setup, but  result was the same. just for confirmation I installed Ubuntu 11.10 x64  and whole scenario happened again - OS installed without problems, but  couldn't boot. I tried to disable various options in BIOS but result was  the same. I suspected it could be related to new kernel (although I  don't know how or why) and decided to try installing older version of  Mint (version 11, Katya). Once again, installation went well, and after  that my system booted just fine. Although I didn't get what I wanted,  which is latest version of Mint, I was somehow happy with that outcome  and left things like that. However, when I tried to boot my PC the day  after - system couldn't boot. Grub 2 shows, and after I pick my option  (default one) and press Enter - boot process starts and after a few  seconds computer freezes. Rebooting few times more didn't make any  changes - my PC freezes, sometimes right after I choose option in Grub 2  (options disappears but screen is still in colour of Grub 2  background), and sometimes a few seconds later (fully black screen  either with or without blinking cursor in upper left corner). After some  time and few reboots later - computer finally boots and works fine rest  of the day. And after that - every day when starting computer it's a  new "struggle"; on some days computer boots without problem on first  attempt, and on some days it boots after a series of rebooting. Few days  ago that series of reboots lasted much longer than half an hour. On the  other hand, Windows boots fine all the time. 

For information to be complete, I have to say few more things:  recently I upgraded BIOS and changed few SATA channels on my MBO from  IDE to AHCI mode (channels 0-3 are in AHCI mode, and channels 4-5 are in  IDE mode). My boot disk is connected to SATA channel 4. Up until  recently, all my SATA channels were in IDE mode, but since I plan to buy  SSD, I changed some channels to SATA just to see how it works. BIOS  upgrade is connected to that - it seems that latest BIOS for my MBO  supports AHCI mode much better (whatever it means) so I decided to make  that upgrade (on suggestion from GigaByte support crew). However, after  making that changes I still used my old Mint for a week or two and it  worked just fine, I mentioned it just because it is a "major change". Of  course I tried to change all SATA channeles back to IDE mode just to  see if my PC will boot without problems but with no luck - it acted  pretty much the same so I changed those SATA channels mode back to AHCI. 

If someone finds it useful, compressed file with dmesg, lshw and lspci dumps can be downloaded from [here.]("http://www.invita.hr/downloads/dumps.zip") 

Sorry for my rather long message. Hope someone will read it and will be able to help me with my problem. 

Thanks in advance, 
JM

---

