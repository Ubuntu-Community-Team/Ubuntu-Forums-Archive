---
title: "Skype"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by jadda on 2007-04-14
Hey.
Have anybody made skype work under ubuntu 6.10?  When I talk in skype I can hear who I am talking to, but they cant hear me. Big problem. I can hear myself in the speakers, and it works flawlessy under windows.

---

### Post by Gorthus on 2007-04-14
Did you install the Debian version off their site?

---

### Post by jadda on 2007-04-14
I installed it through automatix

---

### Post by Gorthus on 2007-04-14
Hm... As I have no knowledge on this problem, and mine worked fine from startup (didnt even have to go into the settings at all), I would suggest uninstalling it, and then getting the debian version from skype.com

---

### Post by Maestro23 on 2007-04-14
> **Gorthus said:**
> Hm... As I have no knowledge on this problem, and mine worked fine from startup (didnt even have to go into the settings at all), I would suggest uninstalling it, and then getting the debian version from skype.com

I use the version from their site as well. No problems either.

---

### Post by jadda on 2007-04-14
no difference...I got my mic set on 100%, capture on 100% and input source on mic. I have fiddeled a lot with this, and nothing has worked. Any suggestions on what else I could do?

---

### Post by jjalocha on 2007-04-14
Many people are experiencing problems with their microphone jack inputs, specially with Skype.  Try googling for that. [In my case]("http://ubuntuforums.org/showthread.php?t=367898"), the problem was solved:

> 
Sound playback works OK out of the box, but it gets temperamental with the microphone jack input, specially with Skype. You might try to tweak it with 'alsamixer' from the command line, which didn't do it for me. Or you can try the following hack with the command line version:

```

$ amixer set "Input Source" Line
$ amixer set "Input Source" Mic

```

For some reason, switching those in that order solves the problem. If this works for you, then you can add the fix permanently to your /etc/rc.local file. Just add the following lines before exit 0.

```

/usr/bin/amixer set "Input Source" Line
/usr/bin/amixer set "Input Source" Mic

```



---

### Post by jadda on 2007-04-14
Thanks a lot for the feedback!! but unfortunately it did not do the trick for me:(  any other suggestions? 
some additional infortmation. In the system-->preferences-->sound i get a consistent beep on all of the tests exept sound capture, there it is only a short beep. 
Whenever I try to record anything from the sound recorder I get a beep for the whole duration of the record.

---

### Post by jadda on 2007-04-14
please help! 
I have beer trying to resolve this for weeks now, googled and search and at one point I messed up ubuntu so bad I had to reinstall ii working on this issue...am I the only one having problems with this?

---

### Post by jjalocha on 2007-04-14
I don't really understand much about audio hardware, but I'll try to help a little bit. The following two commands will tell you what hardware you have. That's the very first starting point. Please post the output of:

```

$ lspci

```

```

$ aplay -l

```

I think, you should also have a look at the [Comprehensive Sound Problems Solutions Guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide").

I also remember that many many people had problems with their mic on the Ubuntu Forums, with many different solutions. Try to search for that.

---

### Post by sailor2001 on 2007-04-14
skype uses a full broadband........ if you have other downloads happening at the same time, you will lose some of the skype.... also 1g ram would help out a lot

---

### Post by sailor2001 on 2007-04-14
edit: are you plugged in to sound outlet in front of box? (mic) that would be mic2 listing under your volume control

---

### Post by nike984 on 2007-04-14
Can you tell us the error message that shows up when you hit
'skype' on the terminal?

I'm also wondering whether you have installed scim-qtimm package.
If it is the case, there is a bug report that scim-qtimm & skype won't 
work together. 
The temporary solution for this case is to go to
System=>Preferences=>Main Menu
and find the skype icon  and change  the command to 

> env QT_IM_MODULE=xim skype

---

### Post by jadda on 2007-04-15
Here is the output you asked for. I have 1 gig of ram, and got a good internet connection, but th problem is that I can not send sound from the mic or record. scim-qtimm is not installed. Thanks again for the replies=) the fact that I can't fix this is driving me mad...

arne@arne-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
arne@arne-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6600] (rev a2)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
06:04.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller

---

### Post by aktiwers on 2007-04-15
Did you check if your Mic works? This has been the only problem for me. There are 2 ways I normally can fix this with.

Double click on your Gnome Sound Applet (where you can turn up and down on sound).
Now go to Edit => Preferences and mark "Mic Select" and MicroPhone Capture. Press close.

Now under Options, I for some reason always have to pick Mic2 instead of Mic1 witch is default.

Maybe this works for you. Else you can also fiddle with your skype settings witch could be the problem.

But try this first, it usually does it for me.

---

### Post by jjalocha on 2007-04-16
jadda, if I'm not misleaden, you have a Realtek ALC260 sound card. Try googling for that specifically. There are many people with slightly different mic problems on the forums. If I understand you correctly, your microphone is working correctly, because you can hear yourself through the speakers, but it's skype that doesn't "see" the microphone. Have you tried with other recording software? Audacity? Ekiga? Is it a built-in microphone that you are trying to get working? Have you tried plugging an external microphone into the jack?
At first sight, there are more people with the same hardware+problem as you. There might be a solution on [this thread]("https://answers.launchpad.net/ubuntu/+ticket/800"), but I'm not sure if I'm understanding everything I read now.
I'm sleepy. It's late. To be continued tomorrow. Sorry.

---

### Post by kvonb on 2007-04-16
Try installing "gnome alsa mixer" from the add/remove thing on your main menu.

It has tons more options than the standard panel mixer.

Have a look for the "capture" slider, and play with that.  Also make sure "rec" is ticked on the "mic" slider.

There are lots of other buttons and stuff like "Mic boost", "Mic select", "PCM" also seems to do strange things!

I had the same problem with Teamspeak, I could hear myself but nobody could hear me.  Once I installed "gnome alsa mixer" I was able to get it working.

It's something to do with the capture source or something.

Regards, Kev :)

---

### Post by chakkaradeep on 2007-04-16
Hi All,

I am behind proxy and squid is not allowing me to configure proxy settings. As per their help, they say first to login to Skype without proxy, then set the proxy settings. This is utter stupidity ! How can one bypass proxy for Skype !

Is there any solution for this ? I really dont know why Skype developers feel so hard to start Skype with proxy configurations! :confused: :confused:

---

### Post by dpoole on 2007-04-28
I installed 7.04 last night, installed skype via Automatix,  I am using usb headset, tried logitec, and Plantronics, Skype wouldn't hold its usb headset settings in skype Options, kept going back to speaker, and mike not working,    I  ,uninstalled skype via Automatix ,  Downloaded Skype from the skype site  Skype> download > Linux > Debian, Ubuntu is listed there. Now works properly. Hope this helps someone.:)

---

### Post by Najand on 2007-04-28
Myabe it is time for you to learn to install deb packages using "apt" or "dpkg", not "automatix" or "easyubuntu",etc.

---

### Post by aikishugyo on 2007-08-23
Also note that htese settings worked for me, whereas before I had no sound at all:

SWITCHES: Mic Capture ON
Mic Boost ON
(Stereo Mic ON)

OPTION: Mic Select MIC1

RECORDING: Capture must be at some non-zero volume

PLAYBACK: Mic OFF
PCM and/or mono and/or other playback should be at some non-zero volume

---

