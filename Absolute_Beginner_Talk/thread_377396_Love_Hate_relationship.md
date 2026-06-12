---
title: "Love Hate relationship"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by soundsystem00 on 2007-03-06
I have been fighting with Linux for about 2 weeks now. My friend refered it to me and it wiped out my windows completely and here I am. I have realized I really love the way ubuntu works, but I have encountered a few problems..

I cannot listen to the internet radio I use to.. Its a struggle to play mp3s..

My sound did not work, my friend fixed it, but now it all of a sudden does not work.

SD card reader does not read..

If anyone experienced can help me, I will thank you so much.

Laptop is a Gateway MX3230

---

### Post by Kateikyoushi on 2007-03-06
Installing codecs will be easier from feisty. To make your sound work take a look here, most likely you have to unmute it in alsamixer. [LINK]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")

---

### Post by taurus on 2007-03-06
For mp3:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

What kind of soundcard do you have on your machine?

```
lspci
```

For SD card, plug it in and post the output of this command from a terminal, Applications -> Accessories -> Terminal, here.

```
sudo fdisk -l
```

---

### Post by soundsystem00 on 2007-03-06
Thanks. Here is what it said after I typed lspci

soundsystem00@lump:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0c.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:00:0c.2 Mass storage controller: Texas Instruments: Unknown device 803b
0000:00:0c.3 0805: Texas Instruments: Unknown device 803c
0000:00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd.: Unknown devic e 8185 (rev 20)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/ K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 60)
0000:00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Contro ller (rev 80)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc.: Unknown device 3 344 (rev 01)
soundsystem00@lump:~$

---

### Post by old_geekster on 2007-03-06
It can be a struggle depending on ones hardware.

Here are some links that have helped me:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

[http://www.ubuntuforums.org/showthread.php?t=336412&highlight=install+latest+nvidia+drivers](http://www.ubuntuforums.org/showthread.php?t=336412&highlight=install+latest+nvidia+drivers)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

Hope these help you!

---

