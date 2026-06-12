---
title: "Broadcom Wireless Card hates me :("
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by xXx 0wn3d xXx on 2006-03-27
Okay Here's my hardware done wih he lspci command. I don' know what the type of he card is...
> 
chris@ubuntu:~$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5950 (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:06.0 PCI bridge: ATI Technologies Inc: Unknown device 5a38
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4374
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4375
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4373
0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4372 (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4376
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 4377
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4371
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc: Unknown device 4370 (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 4378 (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5955
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4351 (rev 10)
0000:08:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
**0000:08:07.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)**
0000:08:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

Since I saw this I'm assuming that I have a Broadcom 4318 card...I tried google for the drivers but I could only find he 64 bit versions and I can't get it to work. Can someone possibly give me the links to the drivers and a good broadcom guide ?

---

### Post by RedKnight on 2006-03-27
Run this command from terminal and reply with your output:

```
iwconfig
```

---

### Post by xXx 0wn3d xXx on 2006-03-27
[QUOTE=RedKnight]Run this command from terminal and reply with your output:

```
iwconfig
```[/QUOTE]
> chris@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

chris@ubuntu:~$


I'm just going to take a guess and say that that's not the best results :) I tried one broadcom guide but I'm lost in the process + I think that the drivers might be causing the problem.

---

### Post by RedKnight on 2006-03-27
I'm just looking into this for you, dosn't look like any wireless drivers are loaded.....
If you've got msn you can add me via the msn icon on my profile.

---

### Post by xXx 0wn3d xXx on 2006-03-27
[QUOTE=RedKnight]I'm just looking into this for you, dosn't look like any wireless drivers are loaded.....
If you've got msn you can add me via the msn icon on my profile.[/QUOTE]
I don't really need that much help, it's just I can't get the drivers.

---

### Post by RedKnight on 2006-03-27
Heres something to research into mate, i've never used it but apparently because the broadcomm does not have linux drivers you need to consider using:

ndiswrapper-1.2

Which will then use the windows drivers.... You will need to get the windows .sys and .inf file for this.

---

### Post by xXx 0wn3d xXx on 2006-03-27
YES ! I got the light to come on...

---

### Post by xXx 0wn3d xXx on 2006-03-27
I got the light to come on and it's activated but I can't get it to connect to my wifi network. I have the Network configured under System>Admin>Newtork. I needed to type in sudo modprobe ndiswrapper to get it working.

---

### Post by harisund on 2006-03-27
So could you connect? Could you post the output of iwconfig if you couldn't connect still?

---

### Post by harisund on 2006-03-27
So could you connect? Could you post the output of iwconfig if you couldn't connect still?

---

### Post by harisund on 2006-03-27
Wow ! how on earth did that happen? I just clicked on "Post Quick Reply" and it posted a hundred repliles? Sorry, really . my sincere apologies ..

---

### Post by xXx 0wn3d xXx on 2006-03-27
Thank you everyone for your help. I got it to work perfectly :) I'm very happy now. I also for my computer to stop looking for eth0 at boot but it will connect when it plugs in. I was thinking about switching back to windows but this has restored my faith in Ubuntu.

---

### Post by RedKnight on 2006-03-28
Glad that worked mate :)
Wasn't too sure how the ndiswrapper worked but looks like thats the answer.

Glad your staying with us mate, You should never had to choose Windows over Ubuntu... I mean you don't get this much support from Microsoft ;)

Stuart.

---

