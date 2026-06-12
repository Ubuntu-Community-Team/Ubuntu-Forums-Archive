---
title: "No front end attached to usb tv device"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Shane11 on 2007-08-22
Feisty 0704 user.

I've been trying to get an A800 DVB device from Avermedia to work for about 5 days now! 
At first dmesg reported that the device was in a cold state. Changed the name of the driver and now
it reported as being in 'a warm state' but there is 'no front end attached to' it.
Also there is no directory called dev/dvb - i'm sure this is probably related but not sure how.
This is part of my dmesg:

 [   41.924529] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-01.fw'
[   41.986777] dib0700: firmware started successfully.
[   42.393612] codec_read: codec 0 is not valid [0x107e5370]
[   42.399813] codec_read: codec 0 is not valid [0x107e5370]
[   42.406068] codec_read: codec 0 is not valid [0x107e5370]
[   42.412266] codec_read: codec 0 is not valid [0x107e5370]
[   42.491067] dvb-usb: found a 'AVerMedia AVerTV DVB-T Volar' in warm state.
[   42.690900] saa7115 1-0025: saa7113 found (1f7113d0e100000) @ 0x4a (em28xx #0)
[   44.322091] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   44.322489] DVB: registering new adapter (AVerMedia AVerTV DVB-T Volar).
[   44.516231] dvb-usb: no frontend was attached by 'AVerMedia AVerTV DVB-T Volar'
[   44.516241] dvb-usb: AVerMedia AVerTV DVB-T Volar successfully initialized and connected.
[   44.516265] usbcore: registered new interface driver dvb_usb_dib0700
[   44.516438] usbcore: registered new interface driver rt2570
[   44.541422] RT25usb  Driver version 1.0.0


If someone could point me to the obvious i'd be grateful

Shane11

---

### Post by schorsch on 2007-08-22
What happens if you start e.g. kaffeine or any other video application after your adapter has been registered? Is there any hint to your DVB adapter as a new button ore something else?

---

### Post by Shane11 on 2007-08-22
I tried installing Kaffine earlier, it reported that there were no dvb devices attached and so would not display that button.
Thanks for taking the trouble to reply by the way.
(I've also tried Myth tv and Xine with no luck).

I would like to know how the 'front end' is attached in a working setup. I probably installed something in the wrong order thus creating my problem. And what is placed in dev/dvb by the applications (dev/dvb has not been created on my system).

I managed to get the hardware to work on an old Toshiba A10 laptop so pretty sure it isn't a hardware issue.

---

### Post by schorsch on 2007-08-22
I just started up kaffeine in a terminal session with verbose output and it gave me the following lines:
```
/dev/dvb/adapter0/frontend0 : opened ( Zarlink ZL10353 DVB-T )
/dev/dvb/adapter0/frontend1 : : No such file or directory
/dev/dvb/adapter1/frontend0 : : No such file or directory
```
So as long as you will not have anything under /dev/dvb there will be no chance to get it running I guess. What about your udev rules, is there something weird? Sorry, I do not have the same adapter as you so I can just guess ....

---

### Post by schorsch on 2007-08-22
Perhaps you should try to download an updated firmware file. Just found this [link]("http://ubuntuforums.org/showpost.php?p=2420108&postcount=20") on the forum ....

---

### Post by Hugolp on 2007-08-23
I have the same isue with the AverMedia dvb-t usb Volar. If you compile v4l-dvb and put the firmware in place it works for me in kernel 2.6.20-16 but no in 2.6.20-15. The problem is that both my webcams only work in -15 kernel and not with -16.

I wish v4l wasnt such a mess.

Hugo

---

### Post by Shane11 on 2007-08-23
Hugolp thanks for the reply.
I'm in a real mess with this one! I think I've loaded all the DVB-T players but of course I think it may be to do with the driver. I downloaded dvb-usb-avertv-a800-02.fw because when I looked up the 'card' that was the recommended driver but when I installed it and did dmesg it reported that dvb-usb-dib0700-01.fw was not present.

So I down loaded that and installed it. Now dmesg is happier and shows A800 as in a 'warm state'.
But there is nothing attached to the front end...

I installed both drivers in both -15 and -16 kernels. 
It doesn't work any way. I'll keep plugging away. May even do a complete clean install and start again - it's good fun but a little frustrating.

---

### Post by Hugolp on 2007-08-23
> **Shane11 said:**
> Hugolp thanks for the reply.
I'm in a real mess with this one! I think I've loaded all the DVB-T players but of course I think it may be to do with the driver. I downloaded dvb-usb-avertv-a800-02.fw because when I looked up the 'card' that was the recommended driver but when I installed it and did dmesg it reported that dvb-usb-dib0700-01.fw was not present.

So I down loaded that and installed it. Now dmesg is happier and shows A800 as in a 'warm state'.
But there is nothing attached to the front end...

I installed both drivers in both -15 and -16 kernels. 
It doesn't work any way. I'll keep plugging away. May even do a complete clean install and start again - it's good fun but a little frustrating.

Hi

Try following this how to: [http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)

Its not for your card but its the same driver so it works. The only part you dont have to follow is when it tells you to edit a file to force the amplifier on, cause the Volar alredy does it automatically. Although if you edit the file, theres no problem neither.

The driver you downloaded is old an in the how to youll get the newest driver. Its got a diferent name so I recomend deleting the driver you got first.

IMPORTANT: I am not linux guru, I just learn by trying and solving errors, but I did that how to on -16 kernel and it worked. I did that how to on -15 kernel (cause some webcams dont work in kernel -16) and it didnt work, probably due to using the lastest v4l source. Also it made that when I load with kernel -16 the X wouldnt work. So it may not happen to you, but my advice is to do that how to only in kernel -16, NOT in -15.

I just did on kernel -16 3 minutes ago and its working fine. Guess Ill have to be withouth webcams in this computer for a while.

As I said, I wish v4l wasnt such a mess.

---

