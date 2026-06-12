---
title: "[SOLVED] newbie no sound k8v motherboard"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by mclark0013 on 2007-11-24
First time installing ubuntu 7.1 everything working ok but I can't get any sound. if I go to system and then sound it says my device is via 8237 (alsa mixer). Have no clue where to start first time using anything but windows. Any help will be greatly appreciated don't want to have to go back to windows.

---

### Post by uclalinux on 2007-11-24
Post what type of mother board you have, and model number. etc   It will be easier to help you.

---

### Post by mclark0013 on 2007-11-25
asus k8v deluxe is the motherboard I have using onboard sound.

---

### Post by jcsteele on 2007-11-25
Post the output to an "lspci" command which will be much more useful.

//jcs

---

### Post by mclark0013 on 2007-11-25
here is the lspci output

clark@clark-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0a.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

---

### Post by jcsteele on 2007-11-25
You might want to check out an existing bug that can be found at:

[http://ubuntuforums.org/archive/index.php/t-25980.html](http://ubuntuforums.org/archive/index.php/t-25980.html)

In particular, the posts by cabu and geopandas might be worth a try.

//jcs

---

### Post by mclark0013 on 2007-11-25
tried everything in that post, unfortunately still no sound!! Thanks for all the suggestions

---

### Post by jcsteele on 2007-11-25
Sound can sometimes be a real problem for some people...for others it works like a charm.  I would search the bug reports for your chipset and see what you can come up with...if nothing else, file a bug report and see what happens.

Sorry it didn't work out...

//jcs

---

### Post by mclark0013 on 2007-11-25
where do I do those things at sorry I'm really new??

---

### Post by jcsteele on 2007-11-25
Not a problem...thats why I am here.

You can find out alot of information by visiting [http://www.ubuntu.com/community/reportproblem](http://www.ubuntu.com/community/reportproblem) which will explain alot of things to you that you might/will need to know


Happy ubunt'ing

//jcs

---

### Post by so7777777os on 2007-11-25
That's a pity......i'm newbie too.
I can't provide any useful suggestion,but i think you could try Ubuntu 7.04.

---

### Post by mclark0013 on 2007-11-27
Got this problem taken care of. For some reason I had to move my speaker wire to a different port on my motherboard. Don't know why it worked fine in windows that way. All I know is that now that the sound is fixed I never have to return to the evil land of Microsoft.

---

### Post by uclalinux on 2007-12-03
Mark as solved under thread tools. Thanks

---

