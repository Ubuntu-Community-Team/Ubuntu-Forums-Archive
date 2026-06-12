---
title: "looking for my video card info"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by rdsii64 on 2007-10-06
bellow is what I just cut and pasted from my terminal window. What I was looking for was the information about my video card. Specifically how large my frame buffer is. All I can see is what I already knew ( that it is an nvida card)  can someone guide me as to where and how I can find what I am looking for. 
I have another card that is a decent 3d card but its an ATI card. I would rather use the nvida card that came in this machine if I can. I want to install beryl on this machine but I need to know if my card has the 3D chops to make it work.

any help appreciated.

ps
I am  a linux noobe 
rdsii64@rdsii64-Ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 02)
**01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15**)
02:0a.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
02:0b.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
rdsii64@rdsii64-Ubuntu:~$

---

### Post by Pumalite on 2007-10-06
Try at the Terminal:
nvidia-settings

---

### Post by rdsii64 on 2007-10-06
tried that and this is what I got.
did I do it wrong or was there something I left off


The program 'nvidia-settings' can be found in the following packages:
 * nvidia-glx
 * nvidia-settings
Try: sudo apt-get install <selected package>
Make sure you have the 'restricted' component enabled
bash: nvidia-settings: command not found
rdsii64@rdsii64-Ubuntu:~$

---

### Post by MrFSL on 2007-10-06
This might give you an answer.

This user says "No" to Beryl on this card.

[http://ubuntuforums.org/showpost.php?p=3156042&postcount=7](http://ubuntuforums.org/showpost.php?p=3156042&postcount=7)

---

