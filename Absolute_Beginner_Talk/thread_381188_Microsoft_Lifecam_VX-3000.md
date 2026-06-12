---
title: "Microsoft Lifecam VX-3000"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by inthepit on 2007-03-10
i have been researching on google, and the forums but to no avail...  anyone have a clue or can point me in the right direction in installing this webcam?  at least give me a definitive answer to whether or not it works with ubuntu so i don't stress over it any more.

thanks,

pit

---

### Post by teaker1s on 2007-03-10
terminal and 
```
lsusb
```
see if we can see chipset and then look for driver-post output

---

### Post by inthepit on 2007-03-10
```
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:00f5 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 06a3:040b Saitek PLC 
Bus 001 Device 001: ID 0000:0000 
```

---

### Post by teaker1s on 2007-03-10
> **inthepit said:**
> ```
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 003 Device 001: ID 0000:0000  
[COLOR="Red"]Bus 002 Device 002: ID 045e:00f5 Microsoft Corp. [/COLOR]
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 06a3:040b Saitek PLC 
Bus 001 Device 001: ID 0000:0000 
```

IT'S A MICROSOFT CHIPSET=LITTLE OR 0% SUPPORT 
have googled for you and only found xp driver, no mac or linux
maybe it would work with wine-but you'd have to ask the wine team

---

### Post by inthepit on 2007-03-10
yeah i figured as much... doesn't hurt to try... now if only there was something like ndiswrapper for any peripheral...

---

### Post by figueiravasco on 2007-04-30
There's an update at [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) and there's also explicit reference to this webcam. I don't know if it works, but I think it worths a try...

---

### Post by dregin on 2007-05-01
Has anyone had any success with this yet? I found a French forum mentioning it here:

[http://forum.ubuntu-fr.org/viewtopic.php?pid=882125](http://forum.ubuntu-fr.org/viewtopic.php?pid=882125)

I think this is a screenshot of it working in feisty... 
[http://piknick.free.fr/diff%c3%a9rences-webcam.png](http://piknick.free.fr/diff%c3%a9rences-webcam.png)

Here's the google translation of the post that linked it:
> 
Being concerned with this webcam, my VX3000 functions partly under Ubuntu Feisty 7.04. When I says partly, it is that the image is not clear under aMSN, or another software using the webcam, since the resolution is not 640x480: [http://piknick.free.fr/diff%c3%a9rences-webcam.png](http://piknick.free.fr/diff%c3%a9rences-webcam.png) Still another thing, I fell on top, without anything to be able to draw some: [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html), however, it will seem that is the suitable pilot&#8230;


---

### Post by jespdj on 2007-05-02
I also have a Microsoft LifeCam VX-3000. I downloaded the driver from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

Unfortunately there seems to be very little documentation on what to do after downloading this, so I figured it out myself. First I had to unpack it and compile it - that was easy. Just "tar xvfz gspcav1-20070426.tar.gz" to unpack it, then cd to the directory and type make.

This leaves me with a kernel module: gspca.ko

I made a directory "/lib/modules/2.6.20-15-generic/kernel/webcam" and copied the module there, then did "sudo depmod" and "sudo modprobe -v gspca".

This all worked OK and the module was loaded.

I then used camorama to see if it works, and camorama sees the camera but it does not work properly. I get a garbled image, I can more or less see myself but the image is full of red and blue distorted blocks... :(

Also it seems to interfere with my Microsoft wireless USB mouse; the computer does not react to mouse buttons anymore when the webcam is active. Very annoying... :(

Using 64-bit Feisty Fawn.

---

### Post by jespdj on 2007-05-03
An update...: I discovered in Windows XP in the Device Manager that my mouse and webcam were on the same USB main hub. My computer has 6 USB ports; four on the back of the machine, two on the front. The webcam and mouse were in connected to two ports next to each other in the back. Apparently that means that they are on the same USB main hub.

I now plugged my webcam into another port and now it doesn't interfere with the mouse anymore.

The image in camorama now looks different, but still completely wrong. I can now see myself, but the image is very dark and the colors are wrong; my face is blue and my shirt is red (which is blue in reality...).

I guess the driver is still buggy... :(

---

### Post by dregin on 2007-05-07
If you check the settings in camorama there's something like "colour correction" that gets rid of that blueness. I think I've found a problem in the source code... recompiling the driver now to see if I've fixed it or am just completely wrong :P

[edit]
Ok. Three things:

1 - Recompiled the driver and now it'mounting the device to /dev/video0.
2 - I just realised that I actually have a VX-6000.
3 - I am retarded :)

---

### Post by ralphz on 2007-05-14
Hi

I downloaded the kernel module, compiled and
# depmod
# modprobe -v gspca
# lsmod | grep gspca
gspca                 607824  0 
videodev               28160  1 gspca
usbcore               134280  11 gspca,usb_storage,libusual,snd_usb_audio,snd_usb_lib,xpad,usblp,usbhid,ehci_hcd,ohci_hcd

everything seems to be ok but when i start camorama i get "Could not connect to video device (/dev/video0). Please check connection"

Please help.

Ralph

---

### Post by moonblink on 2007-05-15
I have been having this same issue, trying to compile using "make"  I have a VX3000 as well.

When I type "make" this is what I get...

make -C /lib/modules/`uname -r`/build SUBDIRS=/home/moonblink/gspcav1-20070508 CC=cc modules
make[1]: Entering directory `/lib/modules/2.6.20-15-lowlatency/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.20-15-lowlatency/build'
make: *** [default] Error 2

Then when I try  "sudo ./gspca_build"

I get...

 FATAL you need to install the Kernel Source for your running kernel

when I type "sudo apt-get install linux-headers-`uname -r` build-essential"

I get...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.20-15-lowlatency is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So my headers are up to date and my essentials are installed as well.  I am quite frustrated with this...](*,) 


PS.  I am a semi noob.

Also, here are the results of "lsusb"

Bus 005 Device 003: ID 054c:01d0 Sony Corp. DVD+RW External Drive DRU-700A
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c50b Logitech, Inc. Cordless Desktop Optical
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 413c:5103 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 045e:00f5 Microsoft Corp. 
Bus 004 Device 001: ID 0000:0000  


Thanks in advance.

---

### Post by craigsn on 2007-06-22
Well, I followed your suggestions on how to get this work. Everthing worked ok, I guess, but camorama does not find a /dev/video1 and when I go to the /dev directory, there isn't a video1 listed there.

Anything else I can try?

Thanks
Craig 
PS. I'm on Feisty 64 bit

---

### Post by sjc1963 on 2007-07-21
Well, I just run this in the folder where I had the files in;

sudo apt-get install linux-headers-`uname -r` build-essential

Then run this;

sudo ./gspca_build

and it works just fine with my LifeCam VX-3000, though the colors and quality aren't there, it still has the good frame rate.

p.s.

I'm using Ubuntu 7.04 Feisty Fawn.

---

### Post by iwarp62 on 2007-09-02
Tried sjc1963's method. It works but like he said the quality sucks and the colors are awful. Really It's far from usable.

---

### Post by sutabi on 2007-09-06
> **ralphz said:**
> Hi

I downloaded the kernel module, compiled and
# depmod
# modprobe -v gspca
# lsmod | grep gspca
gspca                 607824  0 
videodev               28160  1 gspca
usbcore               134280  11 gspca,usb_storage,libusual,snd_usb_audio,snd_usb_lib,xpad,usblp,usbhid,ehci_hcd,ohci_hcd

everything seems to be ok but when i start camorama i get "Could not connect to video device (/dev/video0). Please check connection"

Please help.

Ralph

I am had the SAME problem:

```

# sudo modprobe -vr  gspca
# sudo cp /lib/modules/2.6.20-16-generic/kernel/webcam/gspca.ko /lib/modules/2.6.20-16-generic/kernel/ubuntu/media/gspcav1/
# sudo depmod
# sudo modprobe -v gspca

```

Seems to work fine now

---

### Post by Victor.Barna on 2007-09-26
hi, i'm having the same problem (Could not connect to video device(/dev/video0).Please check connection.) with my vx-6000 webcam...also, there is no /dev/video0.
I tried adding my webcam in the gspca drivers but to no avail.

any help?

---

### Post by kpturvey on 2007-10-05
Same issue here.  I've installed the gspca drivers and they seem to load OK, but they don't create the /dev/videox device.  

So I tried creating it with mknod and using that.  I get a device not found error whenever I try to read the character device.  The camorama program dies with the same error.  So does Xawtv.  

Any help on getting this to work would be greatly appreciated.  

Thanks.

---

### Post by headphase on 2007-10-21
Well not only did this not work, but it screwed up my dev/video so my tv tuner card is no longer recognized.

---

### Post by georgefairbanks on 2007-10-24
> **sutabi said:**
> I am had the SAME problem:

```

# sudo modprobe -vr  gspca
# sudo cp /lib/modules/2.6.20-16-generic/kernel/webcam/gspca.ko /lib/modules/2.6.20-16-generic/kernel/ubuntu/media/gspcav1/
# sudo depmod
# sudo modprobe -v gspca

```

Seems to work fine now

I'm running Gutsy and this didn't work for me.  I was still getting the errors about /dev/video1.  However, I was able to get it working by modifying the paths.  (Warning:  I don't know what I'm doing!)

```

# sudo modprobe -vr  gspca
# sudo cp /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/gspca.ko /lib/modules/2.6.22-14-generic/ubuntu/media/gspcav1
# sudo depmod
# sudo modprobe -v gspca

```

The webcam now works with camorama, but as others have said, the image quality is garish because the colors are distorted.  Also, there appear to be stuck/dead pixels -- maybe the Windows driver adjusts for these.

Hope this helps other Gutsy users.

---

### Post by ralphz on 2007-10-24
Hi

Is there a way to use Windows driver for this web cam in Gusty. Something like ndiswrapper for wireless cards?

---

### Post by digitalfiz on 2007-11-05
Anyone find a driver that has better quality? the quality on that gspca is really terrible. I found that the philips driver works really good for the cams it supports but it don't support the Microsoft Lifecam VX-3000 apparently. Maybe more info on a windows driver wrapper?

---

### Post by Tsume on 2007-11-08
So that others do not waste their time trying to get this to work, this is what the image quality is for me:

[img]http://img231.imageshack.us/img231/9199/webcam1194566391lv0.png[/img]

---

### Post by badgaz1 on 2007-11-19
The irony is I can't get it to work at all on my Vista x64 installation so you're doing better than me :D

---

### Post by pusherrr on 2007-11-23
i've followed the method used on the french forum (basically sudo ./gscpa_build and it works, although the quality is not as good it is quite bearable....seeing how it is a microsoft product lol

---

### Post by sharinacornell on 2007-12-26
It's been about a month since the last post.. was wondering if anyone got the color problems worked out?

Edit:
Using aMSN the colors seem to work themselves out, but the frame rate is pretty bad..

---

### Post by alecwh on 2007-12-28
I followed the instructions above, and the quality is the same as everyone has commented on. Here is a screenshot:

[IMG]http://img266.imageshack.us/img266/3158/webcam1198819602ns0.png[/IMG]

Hopefully a fix will be released, this is terrible. I'm going to try with some other software, I'll post back.

---

### Post by Prisma on 2008-01-11
The way i fix it (since I dont want to spend more money on a webcam) is to use my  Microsoft Lifecam VX-3000 under XP guest OS running on virtualbox. Well, not actually a fix but i can use my webcam. So every time i want to do some video conferencing with soemone i fire up virtualbox.

---

### Post by g7kse on 2008-01-18
this may be a stupid question but how do I copy gspca.ko into te webcam dir either in the terminal or with nautilus

help a numpty day! please

---

### Post by g7kse on 2008-01-18
Well I ended up wasting about an hour or so fiddling and googling. I found [this]("http://www.colinbaker.org/unix/microsoftwebcam") which made it easier but I also ended up with this

[ATTACH]56874[/ATTACH]

Pretty unusable too

---

### Post by vivalant on 2008-01-21
Try the Generic V4L1+V4L2 SN9CXXX driver at [http://www.linux-projects.org](http://www.linux-projects.org) . It gives you better quality, do not confuse with the v4l2-only sn9c1xx driver.

---

### Post by g7kse on 2008-01-28
This one seems to give a good picture at first but after a few seconds the quality fades back to the standard seen before. If it stayed as it should then it'll be fine otherwise another dead duck I think

---

### Post by RAdams on 2008-03-28
Anyone having any luck with this, getting some decent quality? VX-6000 here. This isn't a production machine, so I volunteer myself for all those scary "this might bork your system but try this" jobs. :)

---

### Post by enigmaniac23 on 2008-04-08
I don't know if this will help anyone, but I have the Microsoft Lifecam VX-3000 and I installed Skype 2.0 Beta for Linux and the webcam works perfectly.  The color is right on, and the quality is very good.  However, I did try to bring up the camera with Camorama and I also get the "could not connect to video device /dev/video0".  I don't know what Skype is doing differently, but it worked great with no tweaking needed.  This doesn't fix your problem, but hopefully it might point someone knowledgeable in the right direction.  Wish I had a better answer for you.

---

### Post by g7kse on 2008-04-09
No idea why but if it works for you then I'll give it a try

thanks

Alex

---

### Post by lonejack on 2008-04-10
> **enigmaniac23 said:**
> I don't know if this will help anyone, but I have the Microsoft Lifecam VX-3000 and I installed Skype 2.0 Beta for Linux and the webcam works perfectly.  The color is right on, and the quality is very good.  However, I did try to bring up the camera with Camorama and I also get the "could not connect to video device /dev/video0".  I don't know what Skype is doing differently, but it worked great with no tweaking needed.  This doesn't fix your problem, but hopefully it might point someone knowledgeable in the right direction.  Wish I had a better answer for you.

enigmaniac, are you talking about a video that appears where you can see the person you are speaking (it work for everybody) or are you speaking about your camera, that is: you and the person you are calling can see your face?

To me doesn't work,
Claudio

---

### Post by enigmaniac23 on 2008-04-10
With skype, I'm talking about the video that the other person sees of me.  They can see me fine.  If I go into the skype Tools --> Options --> Video settings, then I can see myself in the little "test" window, and the color and picture is fine there as well.  I didn't have to do anything at all, it just worked, even though camorama still doesn't work.  I guess I should consider myself lucky.

---

### Post by lonejack on 2008-04-10
> **enigmaniac23 said:**
> With skype, I'm talking about the video that the other person sees of me.  They can see me fine.  If I go into the skype Tools --> Options --> Video settings, then I can see myself in the little "test" window, and the color and picture is fine there as well.  I didn't have to do anything at all, it just worked, even though camorama still doesn't work.  I guess I should consider myself lucky.

Just out of curiosity, in video settings(devices) what does appear on ***select webcam***?

Thank you

---

### Post by enigmaniac23 on 2008-04-10
It says:
Microsoft LifeCam NX-3000 (/dev/video0)

---

### Post by lonejack on 2008-04-12
enigmaniac23 are you so kind to tell me what happens when you connect your webcam? The procedure is this:
switch off your PC, disconnect the VX-3000 USB, switch on your PC. After the system start up, launch this command: **sudo udevmonitor**, put your password then connect the VX-3000 usb. You should obtain something like this:


claudio@claudio-desktop:~$ sudo udevmonitor 
[sudo] password for claudio:
udevmonitor will print the received events for:
UDEV the event which udev sends out after rule processing
UEVENT the kernel uevent
[I]
UEVENT[1207975650.385728] add      /devices/pci0000:00/0000:00:02.0/usb1/1-4 (usb)
UEVENT[1207975650.385814] add      /class/usb_endpoint/usbdev1.4_ep00 (usb_endpoint)
UEVENT[1207975650.388797] add      /devices/pci0000:00/0000:00:02.0/usb1/1-4/1-4:1.0 (usb)
UEVENT[1207975650.388869] add      /class/usb_endpoint/usbdev1.4_ep81 (usb_endpoint)
UEVENT[1207975650.388921] add      /class/usb_endpoint/usbdev1.4_ep82 (usb_endpoint)
UEVENT[1207975650.388971] add      /class/usb_endpoint/usbdev1.4_ep83 (usb_endpoint)
UEVENT[1207975650.389021] add      /devices/pci0000:00/0000:00:02.0/usb1/1-4/1-4:1.1 (usb)
UEVENT[1207975650.389071] add      /devices/pci0000:00/0000:00:02.0/usb1/1-4/1-4:1.2 (usb)
UEVENT[1207975650.389121] add      /class/usb_device/usbdev1.4 (usb_device)
UDEV  [1207975650.392145] add      /devices/pci0000:00/0000:00:02.0/usb1/1-4 (usb)
UDEV  [1207975650.402081] add      /class/usb_endpoint/usbdev1.4_ep00 (usb_endpoint)
UDEV  [1207975650.503603] add      /devices/pci0000:00/0000:00:02.0/usb1/1-4/1-4:1.2 (usb)
UEVENT[1207975650.512380] add      /module/snd_hwdep (module)
UDEV  [1207975650.514549] add      /module/snd_hwdep (module)
UEVENT[1207975650.530448] add      /module/snd_usb_lib (module)
UDEV  [1207975650.534736] add      /module/snd_usb_lib (module)
UEVENT[1207975650.540542] add      /module/snd_usb_audio (module)
UEVENT[1207975650.541535] add      /bus/usb/drivers/snd-usb-audio (drivers)
UDEV  [1207975650.543701] add      /module/snd_usb_audio (module)
UDEV  [1207975650.546174] add      /bus/usb/drivers/snd-usb-audio (drivers)
UEVENT[1207975650.548639] add      /class/usb_endpoint/usbdev1.4_ep84 (usb_endpoint)
UDEV  [1207975650.551555] add      /class/usb_endpoint/usbdev1.4_ep84 (usb_endpoint)
UEVENT[1207975650.557592] remove   /class/usb_endpoint/usbdev1.4_ep84 (usb_endpoint)
UDEV  [1207975650.559835] remove   /class/usb_endpoint/usbdev1.4_ep84 (usb_endpoint)
UEVENT[1207975650.613261] add      /module/v4l2_common (module)
UDEV  [1207975650.616490] add      /module/v4l2_common (module)
UEVENT[1207975650.616616] add      /module/v4l1_compat (module)
UDEV  [1207975650.619426] add      /module/v4l1_compat (module)
UEVENT[1207975650.621703] add      /module/videodev (module)
UEVENT[1207975650.627698] add      /module/compat_ioctl32 (module)
UDEV  [1207975650.629868] add      /module/videodev (module)
UDEV  [1207975650.631574] add      /module/compat_ioctl32 (module)
UEVENT[1207975650.634598] add      /class/sound/pcmC1D0c (sound)
UEVENT[1207975650.634742] add      /class/sound/dsp1 (sound)
UEVENT[1207975650.634828] add      /class/sound/audio1 (sound)
UEVENT[1207975650.634927] add      /class/sound/controlC1 (sound)
UEVENT[1207975650.635023] add      /class/sound/mixer1 (sound)
UDEV  [1207975650.642322] add      /devices/pci0000:00/0000:00:02.0/usb1/1-4/1-4:1.1 (usb)
UDEV  [1207975650.647137] add      /class/sound/pcmC1D0c (sound)
UDEV  [1207975650.649733] add      /class/sound/dsp1 (sound)
UDEV  [1207975650.652287] add      /class/sound/audio1 (sound)
UDEV  [1207975650.657144] add      /class/sound/mixer1 (sound)
UEVENT[1207975650.701756] add      /module/sn9c102 (module)
UDEV  [1207975650.705246] add      /class/sound/controlC1 (sound)
UDEV  [1207975650.706826] add      /module/sn9c102 (module)
UEVENT[1207975650.711563] add      /bus/usb/drivers/sn9c102 (drivers)
UDEV  [1207975650.714543] add      /bus/usb/drivers/sn9c102 (drivers)
UDEV  [1207975651.080147] add      /devices/pci0000:00/0000:00:02.0/usb1/1-4/1-4:1.0 (usb)
UDEV  [1207975651.084453] add      /class/usb_endpoint/usbdev1.4_ep81 (usb_endpoint)
UDEV  [1207975651.086820] add      /class/usb_endpoint/usbdev1.4_ep82 (usb_endpoint)
UDEV  [1207975651.089156] add      /class/usb_endpoint/usbdev1.4_ep83 (usb_endpoint)
UDEV  [1207975651.132347] add      /class/usb_device/usbdev1.4 (usb_device)
[/I]

Thank you,
Claudio

---

### Post by enigmaniac23 on 2008-04-12
Here you go:

UEVENT[1208033301.357831] add      /devices/pci0000:00/0000:00:1d.7/usb7/7-1 (usb)
UEVENT[1208033301.357918] add      /class/usb_endpoint/usbdev7.3_ep00 (usb_endpoint)
UEVENT[1208033301.358115] add      /devices/pci0000:00/0000:00:1d.7/usb7/7-1/7-1:1.0 (usb)
UEVENT[1208033301.358473] add      /class/usb_endpoint/usbdev7.3_ep83 (usb_endpoint)
UEVENT[1208033301.358538] add      /devices/pci0000:00/0000:00:1d.7/usb7/7-1/7-1:1.1 (usb)
UEVENT[1208033301.358601] add      /devices/pci0000:00/0000:00:1d.7/usb7/7-1/7-1:1.2 (usb)
UEVENT[1208033301.358624] add      /devices/pci0000:00/0000:00:1d.7/usb7/7-1/7-1:1.3 (usb)
UEVENT[1208033301.358684] add      /class/usb_device/usbdev7.3 (usb_device)
UDEV  [1208033301.367587] add      /devices/pci0000:00/0000:00:1d.7/usb7/7-1 (usb)
UDEV  [1208033301.367625] add      /class/usb_endpoint/usbdev7.3_ep00 (usb_endpoint)
UDEV  [1208033301.493602] add      /devices/pci0000:00/0000:00:1d.7/usb7/7-1/7-1:1.3 (usb)
UEVENT[1208033301.495475] add      /module/snd_hwdep (module)
UDEV  [1208033301.496081] add      /module/snd_hwdep (module)
UDEV  [1208033301.504572] add      /devices/pci0000:00/0000:00:1d.7/usb7/7-1/7-1:1.1 (usb)
UEVENT[1208033301.552161] add      /module/snd_usb_lib (module)
UDEV  [1208033301.554137] add      /module/snd_usb_lib (module)
UEVENT[1208033301.566086] add      /module/v4l2_common (module)
UEVENT[1208033301.567617] add      /module/v4l1_compat (module)
UDEV  [1208033301.568638] add      /module/v4l2_common (module)
UDEV  [1208033301.569982] add      /module/v4l1_compat (module)
UEVENT[1208033301.571652] add      /module/videodev (module)
UDEV  [1208033301.573228] add      /module/videodev (module)
UEVENT[1208033301.585398] add      /module/compat_ioctl32 (module)
UDEV  [1208033301.592889] add      /module/compat_ioctl32 (module)
UEVENT[1208033301.643319] add      /module/snd_usb_audio (module)
UEVENT[1208033301.644292] add      /bus/usb/drivers/snd-usb-audio (drivers)
UDEV  [1208033301.645733] add      /module/snd_usb_audio (module)
UDEV  [1208033301.647004] add      /bus/usb/drivers/snd-usb-audio (drivers)
UEVENT[1208033301.648408] add      /class/usb_endpoint/usbdev7.3_ep84 (usb_endpoint)
UDEV  [1208033301.653103] add      /class/usb_endpoint/usbdev7.3_ep84 (usb_endpoint)
UEVENT[1208033301.660644] add      /module/uvcvideo (module)
UEVENT[1208033301.661015] add      /bus/usb/drivers/uvcvideo (drivers)
UDEV  [1208033301.663530] add      /module/uvcvideo (module)
UDEV  [1208033301.664815] add      /bus/usb/drivers/uvcvideo (drivers)
UEVENT[1208033302.098064] remove   /class/usb_endpoint/usbdev7.3_ep84 (usb_endpoint)
UDEV  [1208033302.100412] remove   /class/usb_endpoint/usbdev7.3_ep84 (usb_endpoint)
UEVENT[1208033302.104651] add      /class/sound/pcmC1D0c (sound)
UEVENT[1208033302.104698] add      /class/sound/dsp1 (sound)
UEVENT[1208033302.104717] add      /class/sound/audio1 (sound)
UEVENT[1208033302.104820] add      /class/sound/controlC1 (sound)
UEVENT[1208033302.104846] add      /class/sound/mixer1 (sound)
UDEV  [1208033302.112400] add      /devices/pci0000:00/0000:00:1d.7/usb7/7-1/7-1:1.2 (usb)
UDEV  [1208033302.112437] add      /class/sound/pcmC1D0c (sound)
UDEV  [1208033302.120468] add      /class/sound/dsp1 (sound)
UDEV  [1208033302.120502] add      /class/sound/audio1 (sound)
UDEV  [1208033302.120523] add      /class/sound/mixer1 (sound)
UEVENT[1208033302.122149] add      /class/video4linux/video0 (video4linux)
UDEV  [1208033302.122846] add      /devices/pci0000:00/0000:00:1d.7/usb7/7-1/7-1:1.0 (usb)
UDEV  [1208033302.126358] add      /class/usb_endpoint/usbdev7.3_ep83 (usb_endpoint)
UDEV  [1208033302.128865] add      /class/video4linux/video0 (video4linux)
UDEV  [1208033302.244525] add      /class/sound/controlC1 (sound)
UDEV  [1208033302.266723] add      /class/usb_device/usbdev7.3 (usb_device)

---

### Post by lonejack on 2008-04-13
enigmaniac23, thank you. Now, it seems the behavior is not completely, but substantially different. In particular at the end of your trace the device is created correctly: 'video0'. Can you tell us what motherboard and configuration and ubuntu version are you using? 
Furthermore can you launch this command:

  **lsusb**

Thank you for your help,
lonejack

---

### Post by enigmaniac23 on 2008-04-13
I have a Dell Latitude D630 - Intel motherboard.
Ubuntu 7.10


~$ lsusb
Bus 007 Device 006: ID 045e:0721 Microsoft Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 0f62:1001 Acrox Technologies Co., Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 0b97:7761 O2 Micro, Inc. 
Bus 005 Device 005: ID 0b97:7772 O2 Micro, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000

---

### Post by lonejack on 2008-04-14
lsusb:
Bus 002 Device 004: ID 059f:0641 LaCie, Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID **045e:00f5** Microsoft Corp. 
Bus 001 Device 002: ID 056a:00b0 Wacom Co., Ltd 
Bus 001 Device 001: ID 0000:0000 
are you sure your webcam is a VX-3000?
Can somebody on this thread check his id?
Thank you,
lonejack

---

### Post by enigmaniac23 on 2008-04-14
AAARGGGGHH....

My wife has the VX-3000.

MINE is the NX-3000
This is mine in dmesg
[  487.232000] usb 7-2: new high speed USB device using ehci_hcd and address 4
[  487.368000] usb 7-2: configuration #1 chosen from 1 choice
[  487.556000] Linux video capture interface: v2.00
[  488.040000] usbcore: registered new interface driver snd-usb-audio
[  488.040000] uvcvideo: Found UVC 1.00 device Microsoft LifeCam NX-3000 (045e:0721)



This is her VX-3000 in dmesg
[  992.128000] usb 3-2: new full speed USB device using uhci_hcd and address 6
[  992.284000] usb 3-2: configuration #1 chosen from 1 choice
[  992.292000] usb 3-2: SN9C105 PC Camera Controller detected (vid:pid 0x045E:0x00F5)
[  992.392000] usb 3-2: No supported image sensor detected for this bridge


SO....MY NX-3000 is the one that is working.  I tried my wife's VX-3000 and it does NOT work.

---

### Post by g7kse on 2008-04-18
I can confirm that my set up has had a dramatic change in video quality in skype but the camorama view is still as bad as before.

i have not changed anything personally, in fact the vx-3000 has been unplugged for a couple of months because the picture quality was so poor. if I can help by posting any outputs then please let me know and I'll do it 

Alex

---

### Post by lonejack on 2008-04-23
hi guys, there are news:

[https://bugs.launchpad.net/ubuntu/+bug/216669](https://bugs.launchpad.net/ubuntu/+bug/216669)

On hardy it seems it'll work!!!
(I hope)

---

### Post by g7kse on 2008-04-23
Hopefully this will close out this problem, it seemed to be a bit hit and miss so maybe another update has done something as well

---

### Post by lonejack on 2008-04-25
Hardy Heron 8.04LTS, it works!!!!!

---

### Post by ralphz on 2008-04-27
What about video quality? Can you post some screen shots?

---

### Post by lonejack on 2008-04-27
Annexed two screenshots: windows and ubuntu. Video quality differs but to me is good enough.
Bye,
Claudio

---

### Post by ralphz on 2008-04-28
I would say there is a big difference if the light conditions were the same for both captures.

But at least I can see something :P

Thanks.

RalphZ

---

### Post by Cooler1989 on 2008-04-29
On my new Hardy Heron it's still don't work or work in this way:

[http://picasaweb.google.pl/pyszkomeister/Publiczne/photo#5194679981143327554]("http://picasaweb.google.pl/pyszkomeister/Publiczne/photo#5194679981143327554")

If you have solution on hardy heron, please let me know... :/

---

### Post by Prefix100 on 2008-04-29
> **Cooler1989 said:**
> On my new Hardy Heron it's still don't work or work in this way:

[http://picasaweb.google.pl/pyszkomeister/Publiczne/photo#5194679981143327554]("http://picasaweb.google.pl/pyszkomeister/Publiczne/photo#5194679981143327554")

If you have solution on hardy heron, please let me know... :/

+1,

In hardy mine is perfect qulaity in cheese, and skype - for a short time, then the quality quickly degrades, dots spread down the screen like a disease.

---

### Post by JunCTionS on 2008-04-29
Mine works plug&play with Hardy Heron and skype (at least the video).
thing is (and I believe this is the common problem with the color everyone is experiencing) is that the auto-brightness is set too high.
To see what I mean, place a white sheet of paper in front of half of the field of view and see how everything else (except the white paper) looks better.
The paper on the other hand shows all the bugs in an overexposed electronic.

So, anyone have an idea on where one might be able to lower the brightness?

Also, I'm just starting to test it, but the microphone (essential for me) doesn't seem to work so plug&play, made the test call with skype and I get nothing, I tested it with both options that appear in the "Sound In" scroll menu after plugging the camera:
USB camera (hw:camera,0)
USB camera (plughw:camera,0)

I'll try to google it a bit now, hope this post helps with the thought on the brightness.

---

### Post by JunCTionS on 2008-04-29
Is the issue in the different programs? or in the compatibility with these
Attached you may find images taken with Camorama, Cheese and Kopete being Cheese's the best image.

My skype image is not as bad as camorama's but it's bad. (can't screenshoot it, I just get a black square with KSnapshot, must be some sort of overlay)

Kopete also has a bad-ish image  but you can sort of adjust the image, for those of you that get a dark sort of inverted images, I also saw that you can accomplish this by setting Kopete's contrast to 0.

I tried fixing camorama's settings but it only gets worse, Cheese doesn't allow much settings, but it's great as you can see, so my suggestion is: try different software.

I also attached the output of the "sudo lsusb -V" for reference purpose, and to see if anyone might find some pointers there on how to get the microphone working (there's an explicit reference to it there).

Good luck :)

---

### Post by jreikes on 2008-05-01
Hey, just want to add in that mine does the same thing as you guys are seeing - messed up colors, etc.

I've only tested it in Ekiga. I'm using Hardy 64-bit, so I didn't know I could use Skype. Can I?

---

### Post by g7kse on 2008-05-02
perhaps it would be a good idea to try a actual test between those of us who seem to have acceptable pictures and those who dont. A quick call between two people might be able to give a comparison and an opportunity to test both video and audo quality as well as set ups

Just a thought

---

### Post by JunCTionS on 2008-05-02
yeah, you can use it with Skype in Hardy (at least the i386 version) at least the video is plug&play. Has anyone gotten audio in skype or any other software? how?

---

### Post by superdif on 2008-05-07
Hi,
I has been able to use the Microsoft Lifecam VX-3000 on Gusty thank to this thread, but I am having problems with Hardy. In specific I'm using Kubuntu (the one with KDE 3.5.9) 64 bits; I'm using the kernel 2.6.25.2 that I have manually downloaded and compiled (I don't know if it may be the cause).

I have downloaded gspcav1-20071224.tar.gz from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html), unpacked it, and run *gspca_build* without error.

I first noticed problems during the system boot where I get this messages:
```
hub 2-0:1.0: unable to enumerate USB device on port 2
hub 2-0:1.0: unable to enumerate USB device on port 4
```
on port 4 there is an AVerTV USB 2.0 Plus (I have never been able to get that working).

Later on (still during boot) I get:
```
[   10.970977] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.47pre49
[   10.972710] usb 1-2: SN9C105 PC Camera Controller detected (vid:pid 0x045E:0x00F5)
```
that make me think that the camera has been detected, but then I get:
```
[   11.338290] usb 1-2: No supported image sensor detected for this bridge
[   10.306445] /usr/src/gspcav1-20071224/gspca_core.c: USB GSPCA camera found. SONIX JPEG (sn9c1xx)
[   11.338290] usbcore: registered new interface driver sn9c102
[   10.306445] /usr/src/gspcav1-20071224/gspca_core.c: [spca5xx_probe:4275] Camera type JPEG
[   11.340582] /usr/src/gspcav1-20071224/gspca_core.c: [spca5xx_getcapability:1249] maxw 640 maxh 480 minw 160 minh 120
[   11.340668] usbcore: registered new interface driver gspca
[   11.340672] /usr/src/gspcav1-20071224/gspca_core.c: gspca driver 01.00.20 registered
[   11.420277] usbcore: registered new interface driver snd-usb-audio
```
and
```
[   14.428926] /usr/src/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 8
...
[   21.799708] /usr/src/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 8
```

If I try to run *camorama* I get an error message that say *"Unable to capture image"*.

In Skype (2.0.0.68 ) under *"Options - Video Devices - Select webcam:"* the field is already set (automatically) to *"MicroSoft VX3000 (/dev/video1)"*, but if I try to do the test Skype crash (totaly close itself) and I get the following error (in the console):
```
Skype V4L: Failed to query capabilities: Invalid argument
Starting the process...
Skype Xv: Xv ports available: 32
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 280
Skype Xv: No suitable overlay format found Aborted
```

*dmesg* gives the following info:
```
[   75.599637] vivi: open called (minor=0)
[  607.635778] vivi: open called (minor=0)
[  624.686693] vivi: open called (minor=0)
[  624.686702] ioctl32(skype:11251): Unknown cmd fd(15) cmd(80685600){t:'V';sz:104} arg(f6205ff4) on /dev/video0
[  624.686706] ioctl32(skype:11251): Unknown cmd fd(15) cmd(803c7601){t:'v';sz:60} arg(f620605c) on /dev/video0
[  624.709564] /usr/src/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 8
[  731.477995] vivi: open called (minor=0)
[  731.478009] ioctl32(skype:11251): Unknown cmd fd(35) cmd(80685600){t:'V';sz:104} arg(f6205e98) on /dev/video0
[  731.478015] ioctl32(skype:11251): Unknown cmd fd(35) cmd(803c7601){t:'v';sz:60} arg(f6205e34) on /dev/video0
[  731.740561] BUG: scheduling while atomic: skype/11281/0x00000002
[  731.740578] Pid: 11281, comm: skype Tainted: P         2.6.25.2-20080507 #1
[  731.740580]
[  731.740581] Call Trace:
[  731.740656]  [<ffffffff80426400>] schedule+0xc2/0x5a6
[  731.740666]  [<ffffffff80426b6e>] schedule_timeout+0x1e/0xad
[  731.740673]  [<ffffffff802253ae>] enqueue_task+0x13/0x1e
[  731.740676]  [<ffffffff80426240>] wait_for_common+0xf6/0x16b
[  731.740679]  [<ffffffff80229d6a>] default_wake_function+0x0/0xe
[  731.740683]  [<ffffffff802869e8>] map_vm_area+0x1a3/0x28e
[  731.740688]  [<ffffffff80243b34>] kthread_create+0xa3/0x108
[  731.740691]  [<ffffffff80389737>] vivi_thread+0x0/0x7b3
[  731.740700]  [<ffffffff80428264>] _write_unlock+0x15/0x2f
[  731.740704]  [<ffffffff8023a40c>] lock_timer_base+0x26/0x4c
[  731.740707]  [<ffffffff804282bb>] _spin_unlock_irqrestore+0x12/0x2c
[  731.740709]  [<ffffffff8023a5ae>] __mod_timer+0xcf/0xdf
[  731.740714]  [<ffffffff803896c2>] vivi_start_thread+0x5a/0xcf
[  731.740719]  [<ffffffff80387fca>] __videobuf_read_start+0xfd/0x129
[  731.740723]  [<ffffffff80388045>] videobuf_poll_stream+0x4f/0xf7
[  731.740728]  [<ffffffff802a62e5>] do_select+0x291/0x454
[  731.740735]  [<ffffffff802a6939>] __pollwait+0x0/0xe1
[  731.740764]  [<ffffffff802c3e14>] compat_core_sys_select+0x196/0x233
[  731.740783]  [<ffffffff802c5171>] compat_sys_select+0x9f/0x13a
[  731.740790]  [<ffffffff80222a62>] sysenter_do_call+0x1b/0x66
[  731.740797]
[  730.336774] vivi/0: [ffff81007bd78900/1] timeout
[  730.336780] vivi/0: [ffff81007bd78800/2] timeout
[  730.336783] vivi/0: [ffff81007bd78e00/3] timeout
[  730.336786] vivi/0: [ffff81007bd78a00/4] timeout
[  730.336789] vivi/0: [ffff81007bd78200/5] timeout
[  730.336791] vivi/0: [ffff81007bd78d00/6] timeout
[  730.336793] vivi/0: [ffff81007b5c0000/7] timeout
[  730.336795] vivi/0: [ffff81007b5c0c00/8] timeout
[  730.336798] vivi/0: [ffff81007b5c0d00/9] timeout
[  730.336801] vivi/0: [ffff81007b5c0300/10] timeout
[  730.336805] vivi/0: [ffff81007b5c0400/11] timeout
[  730.336808] vivi/0: [ffff81007b807800/12] timeout
[  730.336811] vivi/0: [ffff81007b807200/13] timeout
[  730.336815] vivi/0: [ffff81007b807d00/14] timeout
[  730.336818] vivi/0: [ffff81007b807100/15] timeout
[  730.336821] vivi/0: [ffff81007b807f00/16] timeout
[  730.336824] vivi/0: [ffff81007b807400/17] timeout
[  730.336827] vivi/0: [ffff810037885e00/18] timeout
[  730.336831] vivi/0: [ffff810037885400/19] timeout
[  730.336834] vivi/0: [ffff810037885300/20] timeout
[  730.336837] vivi/0: [ffff810037885b00/21] timeout
[  730.336840] vivi/0: [ffff810037885600/22] timeout
[  730.336844] vivi/0: [ffff810037885d00/23] timeout
[  730.336847] vivi/0: [ffff810037885f00/24] timeout
[  730.336850] vivi/0: [ffff810037885700/25] timeout
[  730.336853] vivi/0: [ffff810037885200/26] timeout
```

The strange thing is that it refers to */dev/video0* while *Skype* was (automatically) pointing to */dev/video1*

Any idea?

---

### Post by JunCTionS on 2008-05-14
that's odd, I compiled the gspcav1-20071224 on Gutsy before and ended up basically in the same place as I am in Hardy now (no need to compile).
Why not upgrade to Hardy? I'm a Kubuntu user and I can tell you that for the first time in kubuntu versions I have been able to just go to the Adept Manager, "Fetch Updates" and then do "Distribution Upgrade" without any problems on 4 different computers.

---

### Post by ggenius on 2008-05-21
I think I may have found a solution, if you're comfortable with having no built in audio and maybe having to get an external microphone:

NOTE: This has been tested on my openSUSE system. I'm not sure if it works under Ubuntu. I'll test it out later.

1. Install:
   * Gspcav1 driver
   * Ov51x driver
   * Spca5xx driver
   * Stk11xx driver
   * Uvcvideo driver
   I'm not sure which one worked for me, so I selected to install all of the above.
   * Gqcam
   Gqcam worked best for me.

2. Since this was tested on openSUSE 10.2, make sure you're using kernel 2.6.18 or above, but unsure how it reacts with other kernels.

3. Reboot
4. Log in and launch Gqcam
5. I'm sure you'll end up with a messed up image.
6. Go to the menu > File > Preferences > Filters
7. Check RGB -> BGR conversion
8. Apply and click OK
9. Set the other options if required
10. You should have a nice, clean image.

EDIT: Gspcav1 is the module my kernel loads, so use Gspcav1.

---

### Post by chmavr on 2008-06-14
does the update for hardy works for the vx 6000 model also????has anyoone make this work??

---

### Post by mikebai1990 on 2008-06-24
Can anybody confirm ggenius's method on ubuntu?

---

