---
title: "No Sound"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by lunamystry on 2007-07-20
I installed kubuntu desktop on my pc today just to try it out and now Icant get sound out of my system. Does anybody know how I can solve tis? I was trying to play movies, DVD movies that I didnt really exract from the discs I just copied to the PC and tried to play usin VLC and they started nicely and when whenItried to play a different movie it just froze. I will try to get my system log if i can... i dont know how.

---

### Post by alienexplorers on 2007-07-20
Can you go into terminal and type lspci to see if your sound card is being detected.  Please post the results here.

---

### Post by lunamystry on 2007-07-20
> **alienexplorers said:**
> Can you go into terminal and type lspci to see if your sound card is being detected.  Please post the results here.

Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 05)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 05)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 05)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 05)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 05)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 05)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 05)
01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
lunamystry@pardus:~$

---

### Post by lunamystry on 2007-07-21
this is what I did:

I went to synaptic and i searched for KDE ten i just removed everything that had KDE, amarok kaffeine games everything. I know this was probably no t the best way to go about things but i was desperate and when i tried to google sfafely remove kubuntu package i didnt the links I got were broken or my internet connecting was misbehaving because they didnt open. 

>  sudo dpkg- reconfigure gdm 

which works to change the display manager.

---

### Post by wak_maximus on 2007-07-22
i also facing same problem..
my sound card is almost the same,but in (ICH7 family)
try to go to volume manager..at right of your screen..
double click..
go to edit>preferences
make sure PCM , PCM-2 and Master box is check..

i don't know if it will work for you..
but it work for me..

---

