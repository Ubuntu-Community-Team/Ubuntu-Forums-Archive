---
title: "Ubuntu and my Gateway laptop's display problems."
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by perrylearns on 2007-12-21
Hey guys,

I have a gateway MX3225 and I am having problems like the ones in [[COLOR="Blue"]this post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=267653&highlight=MX3225").  My display only comes up in 640x480 or 800x600.

I tried the steps outlined in the post, but when I reboot I end up with the following message:

> There already appears to be an X server running on display :0. Should another display number by [sic] tried? Answering no will cause GDM to attempt starting the server on :0 again. (You can change consoles by pressing Ctrl-Alt plus a function key, such as Ctrl-Alt-F7 to go to console 7. X servers usually run on consoles 7 and higher.)  

If I answer "Yes", the same message happens again, with ":1" in place of ":0". Answering "Yes" again yields the same response, this time with ":2" in place of the former. This variable cycles again back to ":1"...

Anyway, I just wondered if you had anyone could help me understand how to get the display drivers to work. I just installed Xubuntu 7.1 "Gutsy Gibbon", and I suspect (Though I may be wrong) that differences in the versions might translate to differences in the process.

My computer's a Gateway MX3225, and the system specifications (from Gateway.com) are as follows:

[INDENT]MX3225 Notebook Specifications
Part Number: 1008829Gateway MX3225 Notebook


Feature Description 
Processor Intel® Celeron® M Processor 370
1 MB L2 Cache | 1.5 GHz | 400 MHz FSB  
Display Screen 14-inch Widescreen Ultrabright WXGA TFT  
Chipset Via VN800  
Memory 256 MB DDR2 (1 × 256 MB) SODIMM 533 MHz 
Expandable to 1 GB  
Video S3 UniChrome™ Pro integrated graphics processor
Up to 64 MB shared video memory  
Audio AC '97 2.3 Compliant audio  
Hard Drive 60-GB 4200 RPM hard drive 
Optical Drive CD-RW / DVD Combo 
Write maximum: 24X CD-R/RW
Reads maximum: 24X CD-ROM, 8X DVD-ROM  
Media Reader 4-in-1 Digital Media Manager
Secure Digital, Memory Stick, Memory Stick-Pro, and MMC 
Modem  56K ITU V.92 ready Fax/Modem (RJ-11 port)  
Network  10/100 Mbps built-in Ethernet
802.11g integrated Wireless (up to 54 Mbps) SecureEasySetup™  
Interfaces 2 - USB 2.0 Ports 
1 - VGA External Connector 
1 - RJ11 (Modem) 
1 - RJ45 (Ethernet LAN) 
Microphone In 
Headphone / Audio Out 
 
Pointing Device Touchpad with Vertical Scroll Zone 
PCMCIA  1 - Type I or Type II; Card Bus 
Battery 6-cell Lithium-ion 
Dimensions 1.1 to 1.24-inches (H) × 13-inches (W) × 9.7-inches (D)
28 to 32 mm (H) × 330 mm (W) × 246 mm (D)  
Weight  5.01 pounds
2.27 kilograms [/INDENT]


Any help is much appreciated.  Thanks in advance.

---

### Post by overdrank on 2007-12-21
Hi and welcome,  there has been some issues with the unichrome graphics. You can try and boot to recovery mode which is usually the second choice when booting the grub and it will be a command line.  enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and the use the command ```
startx
``` or use command to reboot ```
sudo reboot
```
If it is the only OS on the system and you see grub loading then you can start pressing the esp key and this will allow you to choose to boot in recovery mode. Hope this helps and good luck!

---

### Post by macogw on 2007-12-21
Recovery mode doesn't require logging in.  It goes straight to a root login.

---

### Post by overdrank on 2007-12-21
You are correct forgot to edit that out. :oops:

---

