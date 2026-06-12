---
title: "BusID"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by sotonin on 2006-05-29
Where to find this?

I have a few questions. First of all i just reinstalled dapper from scratch i noticed my xorg.conf has a BusID entry on device. ... after installing nvidia drivers and running nvidia-xconfig it removed that line!!

Here's the deal though, i had to remove one SLI card to get dapper to even install. Now i'm gonna add it back in since i installed nvidia drivers. do i need 2 device sections in my xorg one for each card? and how can i find the BusID for each card since it's already been overwritten and i dont know how to find it out.

thanks

---

### Post by bluevoodoo1 on 2006-05-29
```
lspci
```

Will show your pci devices, after adding it back in, look for the line that is relevant to your video card.

---

### Post by dutler on 2006-05-30
lspci and KinfoCenter report my Imagine#9 card as being on 2:0a:0. SuSE (Sax) said it was at 2:10:0. 
My dual display does not work with the #9 , but when i substitute a defernt device for the second screen in xorg.conf the display works fine. I am confident that it is not my xorg.conf (file attached) messing me up. 
2:10:0 does not work (black screen) and when i use 2:0a:0 for the BusID x wont start. 
Any ideas? thanks, dutler 

computer > x86_32
Fresh Kubuntu Breezy install with current updates. 

lspci > 0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 03) 
0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (rev 03) 
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 12) 0000:00:1f.0 ISA bridge: Intel Corp. 82801BA ISA Bridge (LPC) (rev 12) 
0000:00:1f.1 IDE interface: Intel Corp. 82801BA IDE U100 (rev 12) 
0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 12) 
0000:00:1f.4 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #2) (rev 12) 
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801BA/BAM AC'97 Audio (rev 12) 
0000:01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G400 AGP (rev 04) 
0000:02:08.0 Ethernet controller: Intel Corp. 82801BA/BAM/CA/CAM Ethernet Controller (rev 03) 
0000:02:0a.0 VGA compatible controller: Number 9 Computer Company Imagine 128-II (rev 02)  

startx error using 2:0a:0 > Fatal Server error:
Catching 11. Server Aborting

xi0: fatal io error 104 (contion resent by peer) on x server ":0.0" after 0 request... 

x log attached - i would attach, but it exceeds the forums size limits. if someone atually wants to read it, ill post it.
xorg.conf attached

---

### Post by dutler on 2006-05-30
i just realized this is in the beginer talk.... how do i move or "cancel" my post?
-dutler

---

