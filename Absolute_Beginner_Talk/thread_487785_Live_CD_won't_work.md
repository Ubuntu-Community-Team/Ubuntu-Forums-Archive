---
title: "Live CD won't work"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by mikeypc2006 on 2007-06-29
I've tried to run both the 32 bit and 64 bit editions of Ubuntu 7.04 Live CD on my desktop.

When I run the 32 bit version, I get the error message: - 

[32.368560] ..MP-BIOS bug:  8254 timer not connected to IO-APIC
[32.547402]  Kernel panic - not syncing: IO-APIC + timer doesn't work!  Boot with apic=debug and send a report.  Then try booting with the 'nopic' option
[32.547438]

When I run the 64 bit version, I get the error message: - 

Kernel alive
Kernel direct mapping tables up to 100000000 @ 8000-d000

Both these instances are running booting the Live CD after selecting the first option from the menu.

What is the problem?

My computer spec is: - 

AMD Athlon™ 64 X2 4200+ - Socket AM2
Microsoft® Windows® XP Professional Edition
Midi-Tower ATX Case +550W PSU -Black/Silver
ASUS M2N32-SLI Deluxe ,AM2 ,nForce 590 SLI, PCIe, WiFi-AP Solo - ATX Mainboard
Realtek RTL8187 Wireless 802.11g 54Mbps
1024MB DDR2 533MHz Memory - (2x512MB)
250GB Serial ATA Hard Drive with 16MB Buffer
Super Format SONY 18x Dual Layer DVD Writer +R/-R/RW/RAM
256MB nVIDIA GeForce 7600 GS - DVI,HDTV & TV-Out - PCI-Express
19" Widescreen LCD TFT Display with Multi Media, DVI-D, 8ms - TS902W
Creative Labs Sound Blaster Audigy 4 Sound Card
Creative Labs T6060 - 5.1 Speakers with Subwoofer
Logitech Desktop Keyboard & Optical Mouse
10x USB 2.0 Ports (onboard)
Firewire PCI Card - adds IEEE1394 Connectivity to your PC
1x Gigabit LAN (onboard)

---

### Post by Rocket2DMn on 2007-06-29
It's possible you got a bad burn on the CD.
Before you burn an iso to a cd you should check the md5sum to make sure it downloaded ok
[HowTo]("https://help.ubuntu.com/community/HowToMD5SUM")
[Hashes]("https://help.ubuntu.com/community/UbuntuHashes") to check against
Then you should burn at a slow speed (like 4x) on good quality media.

If you think your CD is OK, you can try the alternate install cd which you can download from the Ubuntu website, you just have to check the Alternate checkbox when proceeding to the download page.  This typically solves problems people have with the live cd.

---

### Post by Seisen on 2007-06-29
It sounds like your cd's are messed up, what download speed did you burn them it?

---

### Post by mikeypc2006 on 2007-06-29
Sabayon 3.3 didn't work either.  I haven't been able to run any Linux edition as a Live CD on my desktop.  I know the CDs are fine because I have been able to install Linux with them on other computers.

I'd rather not use the 'alternative Install CD' as I don't particularly want to wipe/make changes to my hard disk at this point in time :)

---

### Post by mikeypc2006 on 2007-06-29
Any other ideas guys?  I'd really like to be able to run Ubuntu on my desktop! :D

---

### Post by mikeypc2006 on 2007-06-30
The alternative install CD doesn't work either and gives the same error message :(

---

### Post by DREMA on 2007-07-01
Hello! You need to update your motherboard bios in order to get linux working, I got that problem too and fixed that way, hope it helps you.

---

### Post by sgudibanda on 2007-07-03
HI,

I got my new AMD 64 x2 3800+ machine with Asus M2n-VMX motherboard. I am facing similar problem.
It bails out with kernel panic - Not syncing IO-APIC + TIMER doesnt work.
Has anyone found solution to this? 

Regards,
sandeep

---

### Post by Rocket2DMn on 2007-07-03
Kernel panic means that the kernel (base OS code) hit an error and was unable to continue.  The Not Syncing part is good - it means it's not writing back to your HD which can screw stuff up.  Perhaps you should check your physical connections, as something may have come loose during shipment.
After that, if you have the option of booting with another kernel, that would be best.  There is a way to pass an "noapic" option into the kernel before boot, but I'm not sure how.

---

### Post by kryptik on 2007-07-04
I have the same errors, and I know the CDs work becuase I used them on another PC.  :(

---

### Post by family on 2007-07-04
Dude, i HAD THE EXACT SAME PROBLEM, i FIXED IT TODAY!!!! 
Try booting your PC with the Live CD inside, and you get to the Ubuntu screen right? (If not, reboot, goto the boot menu, and select your CD Drive). Now, hit Esc, and say OK. Type exactly this: live acpi=off. OK? Hit enter... If everything fails, don't blame me, I'm a noob, I did this only today. If not, Ubuntu should run from the disk, and then you can install/partition any way you like!

---

### Post by iver2435 on 2007-07-07
I followed the above instructions and it worked perfectly....I now have Ubuntu installed on my main machine and am doing great!

One thing though...on my screen the kernel option spilled over to a new line so just to be sure everyone else out there can benefit, what you type at the "boot:" prompt is "live noapic" (without the quotes)

that should do it!

---

