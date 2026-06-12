---
title: "cant watch tv--tv card not detected"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by darek214 on 2007-03-04
I just made the switch to ubuntu from windows and everything is great. But i cant get tvtime or other programs to detect my tv card.They detect my webcam instead.I think the card is an ATI Radeon X300 SE PCI-E graphics card but im not sure. How can i fix this? All the help would be greatly appreciated.

---

### Post by newlinux on 2007-03-04
what is the model of you TV tuner card? Only certain ones are supported by linux. You gave us the information on your graphics card (it is a tuner card as well?).

---

### Post by crispy_420 on 2007-03-04
Are you sure that card has a tv tuner? I thought it was just graphics.

---

### Post by darek214 on 2007-03-04
i dont no where to find the tv tuner card info. I think its ATI??? Im not sure.Is there a way to find out? I have a tv tuner card because i watched tv before on windows media center.

---

### Post by darek214 on 2007-03-04
I might have found it. The vendor is Conexant. Thats all it says. Is this card supported?

---

### Post by darek214 on 2007-03-04
can anyone help??? The tv tuner card is either Conexant or ASUS. I dont no where to look for its name. I hope this helps.

---

### Post by crispy_420 on 2007-03-04
Media Center? Maybe it is a Hauppauge card if so you may have a promising future of MythTv in your future.

run lspci from terminal to find the exact chipest

---

### Post by darek214 on 2007-03-04
This is what i got: 

00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
03:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
03:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
03:04.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:04.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
03:05.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)

It looks like Conexant but im not sure.

---

### Post by darek214 on 2007-03-04
is there a program that i can download for ubuntu and has my tv tuner card supported? does anyone know a program like that?

---

### Post by newlinux on 2007-03-04
you might want to check out [http://www.linuxtv.org](http://www.linuxtv.org). I believe that conexant (which is the brand of the chip on the card, not the brand of the card) chip is supported, but I'm not sure. You may need to install some drivers. Do you have a device named /dev/video or /dev/video0? already? if not, then you definitely need drivers (if it is supported) and a good source of information is the link I provided above, unless you can find out the true make and model of the tuner card.

---

### Post by lonce on 2007-03-04
It should be supported.  Thats the same chipset that hauppauge used to use.  So it should be supported.  All you should need to do is install the IVTV drivers.  There is a great how to on the wiki here.  Works very well and only takes a couple minutes.

---

### Post by darek214 on 2007-03-04
Im sorry for all the trouble but would u be willing to find the link to the page for me? I have no idea where to look.

---

### Post by newlinux on 2007-03-04
no problem
[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

Hope that gets you up and running.

---

### Post by darek214 on 2007-03-04
it still doesnt seem to work. even after i finished the directions on the wiki page, my webcam turned on for the test video. It seems to be interfering with me viewing tv. im not 100% sure on that but the webcam is the only option in all the tv apps.

---

### Post by darek214 on 2007-03-04
Ok i got it to work....all i did was unplugged the webcam and pulled the plug from the power outlet and voila. The webcam must have been in the way of detecting the real tv tuner. Im glad it works now. Thanks to all that helped me. I wouldnt have done it without u.

---

### Post by superm1 on 2007-03-05
> **darek214 said:**
> Ok i got it to work....all i did was unplugged the webcam and pulled the plug from the power outlet and voila. The webcam must have been in the way of detecting the real tv tuner. Im glad it works now. Thanks to all that helped me. I wouldnt have done it without u.
Its possible that your webcam was grabbing /dev/video0, and then the ivtv drivers /dev/video1.
You should be able to handle using both of them, the only confusing thing will be which driver loads first on system boot when you have both drivers available.
So with your webcam plugged in, you can see what /dev/video* devices exist:
```
ls -l /dev/video*
```

---

### Post by darek214 on 2007-03-05
Now im having another problem....there is no sound coming from the tv. The video is playing but there is no sound. And the only program that i can use to watch tv is xawtv. all the others crash or there me there is no settings in the config.list or something like that.Thats not my main concern, just the audio. Thx 4 the help again.


Oh and this is the output i got when i typed in the code.
lrwxrwxrwx 1 root root      6 2007-03-05 09:00 /dev/video -> video2
crw-rw---- 1 root video 81, 0 2007-03-05 08:58 /dev/video0
crw-rw---- 1 root video 81, 1 2007-03-05 08:58 /dev/video1
crw-rw---- 1 root video 81, 2 2007-03-05 09:00 /dev/video2

---

