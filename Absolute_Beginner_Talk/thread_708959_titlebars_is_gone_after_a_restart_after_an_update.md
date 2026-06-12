---
title: "titlebars is gone after a restart after an update"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by jvh100 on 2008-02-26
So my titlebars and window frames disappeared when I rebooted after an auto update. I just installed gutsy and the effects were working fine, but then .. no titlebars. If I take the effects off, I get them back. I also installed the compiz extras after this to try and correct the problem (I tried to see if there was anything with window decorators checked off) 

I also looked at other posts about nvidia cards and ran that code in terminal but it wasnt registered? maybe i dont have an nvidia card.. 

anyways any help would be great thanks

---

### Post by Presto123 on 2008-02-27
Well...let's see what kind of card you have. Please post the output of the following command in code tags (# sign when replying):

```
lspci
```

---

### Post by jvh100 on 2008-02-27
```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
```

---

### Post by Presto123 on 2008-02-27
No problem.

No you do not have the Nvidia graphics, it is the onboard graphics as shown here:

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
```

I have only handled Nvidia troubleshooting, but I will try to search around.

---

### Post by jvh100 on 2008-02-27
alright so I think I may have solved the problem.. I dont have compiz-gnome isntalled which generates the window decorator. It wont let me download it though - 

"compiz-gnome:
  Depends: libpango1.0-0 (>=1.18.3) but 1.18.2-0ubuntu1 is to be installed

I tried looking to get these but I can't.. how can I enable the installation of compiz-gnome?

---

### Post by Presto123 on 2008-02-27
Go back into Terminal and type in this command (Careful, because you will be editing video settings):

```
gksudo gedit /etc/X11/xorg.conf

```

Look for a line that begins "Default Depth". That line should say "24" directly afterwards.

If you decide to edit it and your screen sends you to a prompt only, type in this to get your video back (Just in case, write this down):

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Written, that would be sudo(space)dpkg-reconfigure(space)-phigh(space)xserver-org

---

### Post by Presto123 on 2008-02-27
> **jvh100 said:**
> alright so I think I may have solved the problem.. I dont have compiz-gnome isntalled which generates the window decorator. It wont let me download it though - 

"compiz-gnome:
  Depends: libpango1.0-0 (>=1.18.3) but 1.18.2-0ubuntu1 is to be installed

I tried looking to get these but I can't.. how can I enable the installation of compiz-gnome?

That's a different matter...where did you find this out? Take a look in System/Administration/Synaptic Package Manager. Search for "Compiz".

I will be heading off to bed here. Someone will have to take this over.

---

### Post by jvh100 on 2008-02-27
yeh it does say 24

---

### Post by jvh100 on 2008-02-27
yeh i did go to synaptic and thats where I got the message

---

### Post by Presto123 on 2008-02-27
Have you tried to install that missing library in Synaptic yet? Search "libpango". I have here on both of my machines (One with Nvidia, one with Intel drivers) "libpango1.0-0" and "libpango1.0-common".

---

### Post by jvh100 on 2008-02-27
compiz wont download in synaptic bc it wont let me download compiz gnome just says "it wont be downloaded now"

---

### Post by jvh100 on 2008-02-27
hm yeh i ried searching for that but I thhnk I typed it in incorrectly 
thanks for your help

---

