---
title: "Need help with webcam!!"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Stabilityonitsown on 2008-04-08
Hi guys I need help with my webcam. I have searched google and done TONS of tutorials but NONE worked. My webcam is a Micro Innovations webcam. Here is the specs.

## Cat proc/bus/usb/devices ## brings up
***********************************************
T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=ff(vend.) Sub=ff Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=04fc ProdID=0561 Rev= 0.00
S:  Manufacturer=Sunplus Technology Co., Ltd.
S:  Product=Generic Digital camera
***********************************************
## lsusb ## brings up
***********************************************
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 413c:2003 Dell Computer Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 04fc:0561 Sunplus Technology Co., Ltd Flexcam 100
Bus 001 Device 003: ID 413c:3200 Dell Computer Corp.
Bus 001 Device 001: ID 0000:0000
***********************************************
## lsmod ## brings up
***********************************************
Module                  Size  Used by
ibmcam                 43980  0
usbvideo               24388  1 ibmcam
compat_ioctl32          1472  1 usbvideo
videodev               21120  1 usbvideo
v4l1_compat            12036  1 videodev
v4l2_common            20448  1 videodev
i915                   17728  2
drm                    61332  3 i915
ppdev                   8676  0
lp                     11012  0
button                  6672  0
ac                      5188  0
battery                 9636  0
ipv6                  226272  8
dm_snapshot            15552  0
dm_mirror              19152  0
dm_mod                 50232  2 dm_snapshot,dm_mirror
loop                   15048  0
snd_intel8x0           30332  1
snd_ac97_codec         83104  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            38368  0
snd_mixer_oss          15200  1 snd_pcm_oss
parport_pc             32132  1
parport                33256  3 ppdev,lp,parport_pc
rtc                    12372  0
floppy                 53156  0
psmouse                35016  0
serio_raw               6660  0
snd_pcm                68676  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              20996  1 snd_pcm
tsdev                   7520  0
evdev                   9088  1
pcspkr                  3072  0
i2c_i801                7468  0
snd                    47012  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9248  1 snd
i2c_core               19680  1 i2c_i801
snd_page_alloc         10184  2 snd_intel8x0,snd_pcm
shpchp                 33024  0
pci_hotplug            28704  1 shpchp
usbhid                 37248  0
intel_agp              22204  1
agpgart                29896  3 drm,intel_agp
ext3                  119240  1
jbd                    52456  1 ext3
mbcache                 8356  1 ext3
ide_cd                 36064  0
cdrom                  32544  1 ide_cd
ide_disk               14848  3
generic                 4868  0 [permanent]
e100                   32232  0
mii                     5344  1 e100
ehci_hcd               28136  0
uhci_hcd               21164  0
piix                    9444  0 [permanent]
ide_core              110504  4 ide_cd,ide_disk,generic,piix
usbcore               112644  6 ibmcam,usbvideo,usbhid,ehci_hcd,uhci_hcd
thermal                13608  0
processor              28840  1 thermal
fan                     4804  0
***********************************************
## find /lib/modules -name ibmcam.ko ## brings up
***********************************************


I have tried installing gspca and executing the followng commands
sudo modprobe gspca usbgrabber=1 - Didn't work
modprobe -v ibmcam - Didn't work

When I run #xawtv I get the following error message:
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available


When I run #camorama I get the following error message:
"Could not connect to video source(/dev/video0).
Please check connection."

Someone please help!:(

---

### Post by mick8985 on 2008-04-08
Have tried your webcam with cheese?

---

### Post by tompickles on 2008-04-08
jsut more information on cheese - its a new app available with the new version of GNOME (2.2) which is in Ubuntu 8.04.

---

### Post by philinux on 2008-04-08
Or with 

Kopete

Seems to do a good job with webcams.

---

### Post by Stabilityonitsown on 2008-04-08
> **tompickles said:**
> jsut more information on cheese - its a new app available with the new version of GNOME (2.2) **which is in Ubuntu 8.04**.Sorry Ubuntu is not my thang I go with Debian...

---

### Post by Tomatz on 2008-04-08
I had the same problem and went round and round in circles for hours.

The problem was that i connected the webcam through a usb hub. Connecting it directly into the usb port on the back of my computer with gspca installed fixed the problem.

That might be your problem?

---

### Post by chunchengch on 2008-04-08
run these and post the output

$ sudo modprobe gspca
$ dmesg |tail

---

### Post by Stabilityonitsown on 2008-04-08
FATAL: Module gspca not found.:( I am starting to lose my hair:(:(:(

---

### Post by kolisikepu on 2008-04-08
As already suggested, install Cheese from Add/Remove Programs.  If you're having video issues, then Cheese will open and then shut down.

I had a similar problem a few weeks back with my integrated webcam on my Acer.  Check to see if your media files can plan properly.  If it doesn't, then use this command as it fixed my problem.

```
sudo aptitude install xserver-xgl compizconfig-settings-manager
```

---

### Post by philinux on 2008-04-08
Have you tried this generic driver. your cam is supported.

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

---

### Post by Tomatz on 2008-04-08
> **kolisikepu said:**
> As already suggested, install Cheese from Add/Remove Programs.  If you're having video issues, then Cheese will open and then shut down.

I had a similar problem a few weeks back with my integrated webcam on my Acer.  Check to see if your media files can plan properly.  If it doesn't, then use this command as it fixed my problem.

```
sudo aptitude install xserver-xgl compizconfig-settings-manager
```

Why would you want xgl just to use a webcam???

---

### Post by kolisikepu on 2008-04-08
> **Tomatz said:**
> Why would you want xgl just to use a webcam???

Trust me... after many days trying to sort out my webcam problems, doing that just resolved EVERYTHING!

I had problems trying to get my webcam working, my mp3, video files working and just running xgl solved it all.... did I mention I spent days trying to fix this problem?? :lolflag:

---

### Post by Tomatz on 2008-04-08
> **kolisikepu said:**
> Trust me... after many days trying to sort out my webcam problems, doing that just resolved EVERYTHING!

I had problems trying to get my webcam working, my mp3, video files working and just running xgl solved it all.... did I mention I spent days trying to fix this problem?? :lolflag:

Then the problem wasn't the webcam/drivers (as is here). It was the fact you couldn't see the video ;)

---

### Post by kolisikepu on 2008-04-08
It's not mentioned it's a driver issue.

I too was getting this message when trying to run Camo

When I run #camorama I get the following error message:
"Could not connect to video source(/dev/video0).
Please check connection."

Just running XGL fixed it all... that's all I'm saying.  Looking at his Output, the webcam is there.

---

### Post by Tomatz on 2008-04-08
> **kolisikepu said:**
> It's not mentioned it's a driver issue.

I too was getting this message when trying to run Camo

When I run #camorama I get the following error message:
"Could not connect to video source(/dev/video0).
Please check connection."

Just running XGL fixed it all... that's all I'm saying.  Looking at his Output, the webcam is there.

Yeah strange.

Probably worth he gives it a go. Though i am doubtful i'm certainly not infallible ;) 

:lolflag:

---

### Post by mick8985 on 2008-04-08
> **Stabilityonitsown said:**
> Sorry Ubuntu is not my thang I go with Debian...
I don't understand why that means you can't use cheese?

---

