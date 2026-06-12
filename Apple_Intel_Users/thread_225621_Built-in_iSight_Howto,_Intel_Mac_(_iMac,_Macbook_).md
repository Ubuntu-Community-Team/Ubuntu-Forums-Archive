---
title: "Built-in iSight Howto, Intel Mac ( iMac, Macbook )"
date: 2006-07-30
forum: Apple Intel Users
---

### Post by rapido on 2006-07-30
This is a quick Howto on getting the Built-in iSight to work on Intel Mac. So far I have installed on a 20" Intel iMac.  I will also be installing on my 15" Macbook Pro ( as soon as it is back from a logic board replacement ). This guide assumes you have access to the iSight firmware, via harddrive partition.  I can really take zero credit on the development work behind this.  I am simply trying to piece together what I have found in a semi-coherent way.

INSTALLATION

Newest Super Quick 2-Step Install ( Updated for Gutsy 7.10 with 640x480 gstreamer support ):
$ wget [http://www.shiftingheat.com/packages/isight/isight_install.sh](http://www.shiftingheat.com/packages/isight/isight_install.sh)
$ sh isight_install.sh

GSTREAMER TEST

$ gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=640,height=480 ! ffmpegcolorspace ! ximagesink

EKIGA TEST

* Install prerequisites
$ sudo apt-get install ekiga libpt-plugins-v4l2

* Launch Ekiga, via menus or 
$ ekiga

* Configuration.  You may have to select the iSight device. 
Edit > Preferences > Devices > Video Devices > 
  - Video plugin: V4L2
  - Input device: Built-in iSight

CHEESE TEST
$ sudo apt-get install cheese
$ cheese



OLDER INSTALLERS AND NOTES
Below are previous installation techniques and notes.  They should not really be needed any longer, but remain for completeness.


Older Quick Install:
* uvcvideo is now prebuilt in Feisty.  Problem is that it doesn't work with iSight.  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105638](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105638)
  Hopefully this will change with a future kernel update and this guide will become mute.  For now, we will disable it and build our own module.
$ sudo modprobe -r uvcvideo
$ sudo mv /lib/modules/$(uname -r)/kernel/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/$(uname -r)/kernel/ubuntu/media/usbvideo/uvcvideo.ko.original

* Install prerequisites, libusb-dev, you might need kernel headers that match your kernel ( I already had them )
$ sudo apt-get install libusb-0.1-4 libusb-dev linux-headers-$(uname -r)

* Download the new all-in-one bundle, with firmware autoloader as provided by Ivan N. Zlatev ( see [http://i-nz.net/projects/linux-kernel/](http://i-nz.net/projects/linux-kernel/) )
$ wget [http://files.i-nz.net/projects/linux-kernel/isight/uvcvideo-isight.tar.gz](http://files.i-nz.net/projects/linux-kernel/isight/uvcvideo-isight.tar.gz)
$ tar -xzvf uvcvideo-isight.tar.gz

* Build and Install the uvcvideo module
$ cd against-revision-*
$ sudo make
$ sudo make install

* Load the module
$ sudo modprobe uvcvideo

Original Installation Instructions:
* Install prerequisites, libusb-dev, you might need kernel headers that match your kernel ( I already had them )
$ sudo apt-get install libusb-0.1-4 libusb-dev linux-headers-$(uname -r)

* Download the patched linux-uvc source, with firmware extraction tool as provided by Ronald S. Bultje ( see [http://blogs.gnome.org/view/rbultje](http://blogs.gnome.org/view/rbultje) )
$ wget [http://people.freedesktop.org/~rbultje/linux-uvc-0.1.0-b.tar.gz](http://people.freedesktop.org/~rbultje/linux-uvc-0.1.0-b.tar.gz)

* Extract the archive
$ tar zxf linux-uvc-0.1.0-b.tar.gz

* Build and Install the uvcvideo module
$ cd linux-uvc-0.1.0-b
$ sudo make
$ sudo make install

* Mount the mac partion, to give access to the iSight firmware
$ sudo mkdir /mnt/mac
$ sudo mount -t hfsplus /dev/sda2 /mnt/mac/

* Load the iSight firmware
$ sudo ./extract /mnt/mac/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport

* Load the module
$ sudo modprobe uvcvideo


NOTES
It seems that we are also getting close to having this installable via .deb packages.  I found the following Debian packages.  This was my initial attempt, before backing out what I had done and following the directions above.

* linux-uvc-source ( 0.1.0-4 ) 
[http://packages.debian.org/unstable/graphics/linux-uvc-source](http://packages.debian.org/unstable/graphics/linux-uvc-source)
This requires module-assistant.  It seemed to build and install fine.  I downloaded and installed with Gdebi.  Then, to build the kernel module:
$ sudo m-a prepare
$ sudo m-a a-i linux-uvc

* linux-uvc-tools ( 0.1.0-4 )
[http://packages.debian.org/unstable/graphics/linux-uvc-tools](http://packages.debian.org/unstable/graphics/linux-uvc-tools)
This includes the tool macbook-isight-firmware-loader ( the equivalent of extract above ).  I couldn't get this toolset to install properly, due to dependencies.  The toughest dependency was the need for libc6(>= 2.3.6-6).

---

### Post by chasisaac on 2006-07-30
I cannot wait to till Sunday afternoon when I can try this. 

Yeah!

---

### Post by leonedo on 2006-07-30
it works great, thanks!!

---

### Post by phico on 2006-07-30
> **leonedo said:**
> it works great, thanks!!

Thank you rapido !  It is working for me also.

(I just had to install :
 sudo apt-get install libusb-0.1-4 libusb-dev
instead of :
 sudo apt-get install libusb libusb-dev)

---

### Post by rapido on 2006-07-30
> **phico said:**
> Thank you rapido !  It is working for me also.

(I just had to install :
 sudo apt-get install libusb-0.1-4 libusb-dev
instead of :
 sudo apt-get install libusb libusb-dev)

Thanks for the correction.  I have updated the original post.

---

### Post by blindspy on 2006-08-07
```
$ sudo modprobe uvcvideo
FATAL: Error inserting uvcvideo (/lib/modules/2.6.15-23-686/usb/media/uvcvideo.ko): Invalid module format
```

any suggestions?

---

### Post by phetre on 2006-08-07
Wow, thank you!  This is very impressive.  Only two little things went wrong on mine:
[LIST=1]
[*]The GStreamer test fails with the message:  "ERROR: pipeline could not be constructed: no element "v4l2src"."
[*]The image displays beautifully in Ekiga, but it seems to be cropped weirdly:  the camera shows only objects to its left, so I have to lean right to get in the picture.
[/LIST]
Any ideas?

---

### Post by rapido on 2006-08-08
> **phetre said:**
> Wow, thank you!  This is very impressive.  Only two little things went wrong on mine:
[LIST=1]
[*]The GStreamer test fails with the message:  "ERROR: pipeline could not be constructed: no element "v4l2src"."
[*]The image displays beautifully in Ekiga, but it seems to be cropped weirdly:  the camera shows only objects to its left, so I have to lean right to get in the picture.
[/LIST]
Any ideas?

As far as the GStreamer test, it looks like you may not have the video4linux2 plugin installed in gstreamer.  Looking at the gstreamer documentation, it seems the plugin ( which provides support for v4l2src ) is part of the gst-plugins-bad. 

I would try first executing the following ( the second requires multiverse enabled ).  These are two plugin packages I have installed that look like good candidates for that plugin.

$ sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse

Then try the GStreamer command again, as shown above.

As far as Ekiga, mine is also displaying roughly one quadrant of the actual camera input.  Not sure why yet.  I found nothing obvious in the preferences.  I will have to dig deeper in documentation.

---

### Post by phetre on 2006-08-08
Thanks, it worked after a reboot.  Maybe the codecs just hadn't settled in yet.
And you're right:  the GStreamer test window shows the camera's entire field.  How strange!

---

### Post by rapido on 2006-08-10
> **phetre said:**
> Wow, thank you!  This is very impressive.  Only two little things went wrong on mine:
[LIST=1]
[*]The GStreamer test fails with the message:  "ERROR: pipeline could not be constructed: no element "v4l2src"."
[*]The image displays beautifully in Ekiga, but it seems to be cropped weirdly:  the camera shows only objects to its left, so I have to lean right to get in the picture.
[/LIST]
Any ideas?

phetre,

I figured out how to configure Ekiga to show the entire video display.  First, open gconf-editor.

$ gconf-editor &

Now, from the left-hand tree, navigate to:
apps > ekiga > devices > video 

Change the value for size from 0 to 1.  This changes the size from Small ( QCIF 176x144 ) to Large ( CIF 352x288 ).

Reopen Ekiga and you should see the full video image.

---

### Post by idn on 2006-08-13
Just to say this is awesome - it works fine. Although the video seems to be flipper horizontally - i wave with my left hand but in the video its with my right. Not a big issue but kind of random :)

---

### Post by rupy on 2006-08-17
Very cool thanks.

For some reason my ekiga doesnt work with my webcam though - just says error opening device?

The cam opens in kopete but its all green?

---

### Post by rupy on 2006-08-20
It seems to be very flakey, I rebooted and now it refuses to work?

I also have to re-run the extract command to get the firmware each time it seems, is this normal?

Here is my dmesg:
> 
[17185375.804000] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8501)
[17185387.784000] usbcore: deregistering driver uvcvideo
[17185397.748000] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8501)
[17185397.748000] usbcore: registered new driver uvcvideo
[17185407.416000] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).
[17185407.564000] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).
[17185407.764000] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).
[17185483.352000] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).
[17185483.356000] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).
[17185483.356000] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).
[17185490.328000] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).
[17185490.560000] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).
[17185496.168000] usbcore: deregistering driver uvcvideo
[17185498.288000] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8501)
[17185498.288000] usbcore: registered new driver uvcvideo
[17185502.720000] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).
[17185502.956000] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).
[17185508.604000] usbcore: deregistering driver uvcvideo
[17185516.096000] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8501)
[17185516.100000] usbcore: registered new driver uvcvideo
[17185520.848000] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).
[17185521.908000] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).
[17185529.476000] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).
[17185529.480000] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).
[17185654.524000] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).
[17185686.392000] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).
[17185686.604000] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).


---

### Post by idn on 2006-08-24
Does anyone know of a application that can capture the images or movies?

---

### Post by goneskiing on 2006-08-24
Will this and the other patches (ie sound, video) be included in Edgy ?

---

### Post by idn on 2006-09-02
I have posted a few things on launchpad about kernel patches and things but havent heard anything, I really want to get the framebuffer working so I can use splashy.

---

### Post by bashee on 2006-09-02
> **idn said:**
> Does anyone know of a application that can capture the images or movies?

ekiga :) call:save current picture or Ctrl+S. Will be saved in your home folder with date and timestamp.

with gconf-editor you can edit the path and the prefix of the stored: apps:ekiga:general:save_prefix.

Or maybe try coriander: sudo aptitude install coriander [http://damien.douxchamps.net](http://damien.douxchamps.net)

---

### Post by anasazi on 2006-09-03
this doesn't work anymore

when you type "sudo make" it just goes:

sudo: make: command not found

---

### Post by border on 2006-09-06
when I try the ./extract command
all I get is this:
Shalsum check on firmware file failed

I tried copying the file to the linux file system (even from osx via usb stick), but I still get the same result.

I even tried continuing, and I can load the module. Every program can see that I have an iSight now, but there not able to use it

Anyone any ideas?

thx

---

### Post by Ender710 on 2006-09-15
I also get "Shalsum check on firmware file failed".  Anybody know the problem?

---

### Post by phenixamd on 2006-09-15
i had the same sha1 issue.. if you remove the line thats returning -1 from the extract.c file and recompile, it appears to load the firmware correctly.

its um, line 174

---

### Post by phenixamd on 2006-09-15
just kidding.

removing that line makes it look like the firmware is loading properly.. dmesg reports 
[17179714.904000] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8501)
after it.   but it needs to be redone upon reboot, and the device doesnt seem to be working for me in ekiga.

---

### Post by tlight on 2006-09-15
I just nuked my OSX install and am writing this from dapper.. hence can't access the firmware, any chance of including it in a package of some form?
Or linking to the firmware elsewhere..

---

### Post by rupy on 2006-09-16
I managed to get mostly everything sorted, thanks all. I just have 2 questions:

1) Does nobody else have to re-run the extract command on every reboot? I added the mac partition to my /etc/fstab so there is no reason it can't re-access the path if it needs to, although it shouldnt anyways right?

2) Does anyone know how to get this to work with kopete?

---

### Post by gavin8or on 2006-10-07
For all the people that are having problems with the Sha1sum checksum error, you have a newer version of the Firmware (newer than firmware 1.55) and the original patch only works with firmware 1.55. 

Download the latest version (with an updated patch) of linux-uvc-0.1.0-d from [Ronald's directory](http://people.freedesktop.org/~rbultje/)and then try the exact same steps again... it will work and everything will be working great!

---

### Post by Jaime E. Villate on 2006-10-10
I get a very nice picture with Ekiga or Gstreamer, for just a second, but the image then freezes and horizontal sections get scrambled. I see the following:

```
[17181784.512000] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).
[17181784.948000] uvcvideo: Failed to resubmit isoc URB (-45).

```

I have a MacBook (not Pro) with kernel 2.6.15-27-686 and installed linux-uvc-0.1.0-d
What could be the problem?

---

### Post by phetre on 2006-10-16
> **gavin8or said:**
> For all the people that are having problems with the Sha1sum checksum error, you have a newer version of the Firmware (newer than firmware 1.55) and the original patch only works with firmware 1.55. 

Download the latest version (with an updated patch) of linux-uvc-0.1.0-d from [Ronald's directory](http://people.freedesktop.org/~rbultje/)and then try the exact same steps again... it will work and everything will be working great!

Hi Gavin9or,

Thanks for the tip.  Unfortunately I'm a n00b and haven't been able to get it to work.  Here's what I've done so far:

[LIST=1]
[*]Downloaded linux-uvc-0.1.0-d and unzipped it to my home directory.  Ran "sudo make" and "sudo make install."
[*]Ran my script "enable_isight.sh" to load the firmware and modprobe uvcvideo.  (It worked before the firmware update, but if you think the problem is there, I can attach the contents).  Got a checksum error, so I figured I needed to apply the patch myself.
[*]I downloaded isight.patch and ran 'patch <isight.patch' in the linux-uvc directory.  9 out of 11 hunks failed (why did the other two work?)...
[*]...but I ran "sudo make" and "sudo make install" anyway.  Still the checksum error.
[/LIST]

Fortunately I don't use the camera for anything besides showing off, but it's still nice to have.  Can you help me, please?

---

### Post by Stu09 on 2006-10-17
> **Jaime E. Villate said:**
> I get a very nice picture with Ekiga or Gstreamer, for just a second, but the image then freezes and horizontal sections get scrambled. I see the following:

```
[17181784.512000] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).
[17181784.948000] uvcvideo: Failed to resubmit isoc URB (-45).

```

I have a MacBook (not Pro) with kernel 2.6.15-27-686 and installed linux-uvc-0.1.0-d
What could be the problem?

Has anyone else tried this on a MacBook (not Pro) ?
How did you go ?

---

### Post by Technoviking on 2006-10-20
On Edgy RC i get the following error loading the firmware.
```
dbasinge@tardis:~/linux-uvc-0.1.0-d$ sudo ./extract /mnt/mac/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport
Loading firmware for iSight...
Invalid firmware data_length 23389, load aborted
Loading firmware for iSight...
Invalid firmware data_length 23389, load aborted
No Apple iSight found!
dbasinge@tardis:~/linux-uvc-0.1.0-d$ test: 1: ==: unexpected operator
```

---

### Post by cdinz on 2006-10-21
> **Mike said:**
> On Edgy RC i get the following error loading the firmware.
```
dbasinge@tardis:~/linux-uvc-0.1.0-d$ sudo ./extract /mnt/mac/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport
Loading firmware for iSight...
Invalid firmware data_length 23389, load aborted
Loading firmware for iSight...
Invalid firmware data_length 23389, load aborted
No Apple iSight found!
dbasinge@tardis:~/linux-uvc-0.1.0-d$ test: 1: ==: unexpected operator
```

I get the same on my MacBook running Edgy RC

---

### Post by benanzo on 2006-10-25
I have the black macbook and get the same error.  I am fully updated on edgy rc.

---

### Post by Technoviking on 2006-10-27
> **Mike said:**
> On Edgy RC i get the following error loading the firmware.
```
dbasinge@tardis:~/linux-uvc-0.1.0-d$ sudo ./extract /mnt/mac/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport
Loading firmware for iSight...
Invalid firmware data_length 23389, load aborted
Loading firmware for iSight...
Invalid firmware data_length 23389, load aborted
No Apple iSight found!
dbasinge@tardis:~/linux-uvc-0.1.0-d$ test: 1: ==: unexpected operator
```

No change in Edgy.

---

### Post by frigaut on 2006-10-30
I'm on edgy, and got the exact same error message as you.
This is solved by doing:

sudo ln -sf bash /bin/sh
extract the firmware
sudo ln -sf dash /bin/sh

don't forget the second ln though!

---

### Post by Technoviking on 2006-10-31
I have to re-extract the firmware everytime I reboot, is that normal.

---

### Post by stevetsai on 2006-10-31
Finally I fixed kopete and I can see the video from kopete normally. If someone want to use kopete with isight, they could download kopete-0.12.2 and modify kopete-0.12.2/kopete/libkopete/avdevice/videodevice.cpp. I attach the file and someone can search "Steve Tsai" to find out the codes I modified.

---

### Post by rupy on 2006-11-02
> **Mike said:**
> I have to re-extract the firmware everytime I reboot, is that normal.
yup I get this too, any ideas?

stevetsai: I love you! Thanks so much for that, gonna try it out now.

---

### Post by rupy on 2006-11-02
> **stevetsai said:**
> Finally I fixed kopete and I can see the video from kopete normally. If someone want to use kopete with isight, they could download kopete-0.12.2 and modify kopete-0.12.2/kopete/libkopete/avdevice/videodevice.cpp. I attach the file and someone can search "Steve Tsai" to find out the codes I modified.
Hi Stevetsai, a few questions if you dont mind: 1) will this only work with 12.2 or 12.3 as well? 2) I assume I have to get the source and compile kopete to do this right?

---

### Post by stevetsai on 2006-11-02
Hi rupy,
I just built kopete 0.12.2 only. How do you get kopete 0.12.3? The last release is kopete 0.12.2. If you could tell me where I can download 0.12.3, I can download it to test.

---

### Post by rupy on 2006-11-05
> **stevetsai said:**
> Hi rupy,
I just built kopete 0.12.2 only. How do you get kopete 0.12.3? The last release is kopete 0.12.2. If you could tell me where I can download 0.12.3, I can download it to test.
Lol, no idea, I just used apt...

---

### Post by rupy on 2006-11-05
> **Mike said:**
> I have to re-extract the firmware everytime I reboot, is that normal.

Will adding the firmware loader command to /etc/init.d/bootmisc.sh fix this, I assume modules are loaded after this so it should right?

eg:
/usr/src/linux-uvc-0.1.0-d/extract /mnt/osx/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport

---

### Post by stevetsai on 2006-11-09
Rupy,
They have the same videodevice.cpp, so you can use the above file. Right now I use edgy with the fixed version 0.12.3 kopete and it works fine.

---

### Post by rupy on 2006-11-09
Cool, well I just downgraded to 12.2 - they appeared to be the same anyways...

Thanks again stevestai!

PS. My previous post on adding that line to your bootmisc.sh did in fact fix the loading firmware each time issue.

---

### Post by pistooli on 2006-12-16
> **stevetsai said:**
> Finally I fixed kopete and I can see the video from kopete normally. If someone want to use kopete with isight, they could download kopete-0.12.2 and modify kopete-0.12.2/kopete/libkopete/avdevice/videodevice.cpp. I attach the file and someone can search "Steve Tsai" to find out the codes I modified.

Excellent job... many thanks. I can confirm that recompiling Kopete with the above mentioned modification makes indeed the iSight work with Kopete... :-)

cheers - pistooli

---

### Post by rootkit on 2007-01-06
i've done all the steps but kopete doesn't see the webcam.
what i'm, wrong? i get an ioctl error:
VIDIOCGCAP: invalid argument

i have V4L2 enabled in the kernel, what else do I need?

---

### Post by rootkit85 on 2007-01-06
ok, found. I didn't have vfl1 compatibility layer, so kopete won't work.
I've recompiled my kernel and now in kopete i can see... a green box

i also have errors in the kernel:
```
Linux video capture interface: v2.00
uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8501)
usbcore: registered new interface driver uvcvideo
USB Video Class driver (v0.1.0-c)
uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).
uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).
uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp: 26).
```

also kopete says:
```
read error 19, No such device
```

btw, i've edited the firmware loader so it can work even with dash as default shell, then
i've modified it into a program that dumps the firmware in a file.
You may say: "why dump it if we can load it from the apple driver?"
the answer is that the apple driver is copyrighted by Apple, so such firmware can't be redistributed.
also the dumped firmware is way smaller (11kb)

i attach the dumper, the dash aware loader and the firmware.

Have fun, my camera still doesn't works (maybe I have to use vfl1 instead of vfl2+compat layer?)

---

### Post by Romu on 2007-01-22
I'm using Edgy as single boot on my MacBook Pro

Can someone send me the file:
System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport

Thanks.

---

### Post by trevelyn on 2007-03-19
> **Romu said:**
> I'm using Edgy as single boot on my MacBook Pro

Can someone send me the file:
System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport

Thanks.

yeah seriously, what the hell? i got rid of OS X because it was a lame llama, anyone know where to find this file I would greatly appreciate it!! thanks - trevelyn :(

---

### Post by trevelyn on 2007-03-19
i see like a few people have asked for the drivers already, i appolagize.

would it be possible to cp the APPLEUSBVIDEOSUPPORT er whatever it's called from the mounted install disk? I'm going to try tonight when i get home.  could you even mount the install disk? Thats too outrageous to have to install mac os x, then partition, then install kubuntu, then extract the driver from a mounted os x partition, then repartition with fdisk and get rid of OS x, and dist-upgrade ubuntu.  Though, all of that is worth it, Kubuntu is a beautiful operating system with great controls, once you get around the damn "sudo."  Speaking of sudo, i also modprobed uvnc-linux er whatever the driver is called for iSight, and (wouldnt you know it) Both of my USB ports turned off.  Then i rebooted, and now only ONE usb port works. I dont know how to turn the other port back on, but i have to reinstall anyways to finally accomplish this iSight problem.

---

### Post by cyberdork33 on 2007-03-19
Does the install disc use hfs+? you will probably need to install the hfsplus filesystem driver before you can mount the OSX cd if that is going to work.

---

### Post by trevelyn on 2007-03-20
yeah it mounted perfectly with   mount -t hfsplus /dev/dvd /mnt/dvd 
I issued a whereis command and locate, both found nothing, then i used Konquerers search option, that files not on either install disk.  Its probably created during the install process.
I sure wish someone could upload it, it would save a HUGE amount of time for all of us.

also, If someone does get it up, I will host the file from my site with a much better up to date how to on installing JUST ubuntu, with *no* other OS.  Most of the texts i have been following have had too many errors, and need updated.

---

### Post by longhorn49 on 2007-03-20
[http://www.mediafire.com/?81xtkqyttjt](http://www.mediafire.com/?81xtkqyttjt)

ok since I helped you guys out, can someone help me figure out why I only get a green screen. Im running a mactel-2.6.20.1 kernel.

---

### Post by trevelyn on 2007-03-21
well thanks but i already installed OSX, got the driver, then reinstalled Kubuntu.  Talk about errors, i really dont think linux belongs on this hardware my friends.  anyways, i follwed al the steps and i guess got a little bit further than before.  heres what my screen reads when i ./extract /iSight/AppleUSBVideoSupport:

Once device 0x5ac 0x8300
Loading firmware for one iSight
Invalid firmware length 23389, load aborted
Loaded firmware for one iSight
Once device 0x13b1 0x20
Once device 0x0 0x0
Once device 0x13b1 0x20
Once device 0x5ac 0x8300
Loading firmware for one iSight
Invalid firmware length 23389, load aborted
Loaded firmware for one iSight
Once device 0x5ac 0x8205
Once device 0x0 0x0
Once device 0x5ac 0x8205
Once device 0x5ac 0x21a
Once device 0x0 0x0
Once device 0x5ac 0x21a
Once device 0x5ac 0x8240
Once device 0x0 0x0
Once device 0x5ac 0x8240
Once device 0x4d9 0x499
Once device 0x0 0x0
Once device 0x4d9 0x499

and neither kopete, nor ekiga find my camera.  nothing in dmesg either.  i have a plain MacBook brand new, with the *newer* wifi card too, which isnt supported by anything. i've tried madwifi drivers, ive tried howtos on installing Windows.INF's with ndiscrapper, nothing.  now the iSight wont work, im anout to give up. thanks - trev

---

### Post by trevelyn on 2007-03-21
> **longhorn49 said:**
> [http://www.mediafire.com/?81xtkqyttjt](http://www.mediafire.com/?81xtkqyttjt)

ok since I helped you guys out, can someone help me figure out why I only get a green screen. Im running a mactel-2.6.20.1 kernel.

oh i almost forgpt, when i tried to play a DVD the screen was green too, maybe the same issue???

---

### Post by trevelyn on 2007-03-23
wow! it's working! i sent the driver froim my temp OS X install somewhere to my solaris server and reinstalled Ubuntu and hey in ekiga the iSight works! well, the question thats a few questions up from me where the guy says his Kopete screen is green, mine is too and i have googled, and found like nothing.  any ideas on this yet?? thanks in advance guys! - trev

---

### Post by thonuz on 2007-03-23
There is iSightDriver.pkg in bootcamp. Just view contents.
Will this driver work or do anything? I am putting both the wirless driver and this on a stick and use also wine.

---

### Post by rei_t_ex on 2007-03-29
Hello, having followed the instructions, my isight firmware managed to load without a single problem (and running ./extract/AppleUSBVideoSupport a second time now returns "Apple iSight with firmware already loaded found").

However, when I try to run the Gstreamer test, I get 
```
WARNING: erroneous pipeline: no property "use-fixed-fps" in element "v4l2src0"
```

And selecting V4L2 in Ekiga gives a "No device found".

Any help would be appreciated.

---

### Post by gmc on 2007-04-22
Hi Folks,

I'm having a little trouble with my "iSight". Can someone verify the md5sum of the AppleUSBVideoSupport file with the value below?

```

./extract AppleUSBVideoSupport
Sha1sum check on firmware file failed
root@macbook:/usr/src/linux-uvc-0.1.0-b# md5sum AppleUSBVideoSupport 
***8b78709d02d3584f40cc041db9eecfe8***  AppleUSBVideoSupport
root@macbook:/usr/src/linux-uvc-0.1.0-b# 

```Thanks
Gord

Edited: Solved, seems I was using an older version of the linux-uvc driver.

---

### Post by SarahDavies on 2007-04-23
I am having the same issue as rei_t_ex.  Please help.  Is the problem that we ran "extract" twice?

Thanks.

---

### Post by ragemaxis on 2007-04-23
im running macbook 2.1 white (i believe its 2.1,  its a core2duo 2ghz w/ 1gb ram) and I was having trouble on end with getting the firmware loader to work,  it was giving me the wrong size error on version "e" and it was giving me the sha1 error on version "b".

**I downloaded the .deb file and used alien to make a .tgz out out of it ... the one posted at the beginning of this thread,  linux-uvc-tools ... then installpkg'd it and used the macbook-isight-firmware-loader to load the firmware.  worked first try.**

now uvcvideo loads fine.   Going to try and test it with kopete, etc. next - I had it working doing the OSX load then slackware load before ... in that I could get a /dev/video0 with incorrect permissions,  and then in kopete a green box.  Ekiga wasn't working at all (gconf error) and gstreamer won't work.

This is the joy of running slackware in a debian-centric world.   nothing works out of the box - every single thing i've attempted to work with for getting the isight working has bitterly failed for one reason or another.   I get tired of jumping through endless hoops to just get simple software working.   I will likely just install the .deb files for gstreamer to try and get that working.  I intend to use this with Kopete so hopefully the .cpp replacement file will work.

---

### Post by trevelyn on 2007-04-28
> **rei_t_ex said:**
> Hello, having followed the instructions, my isight firmware managed to load without a single problem (and running ./extract/AppleUSBVideoSupport a second time now returns "Apple iSight with firmware already loaded found").

However, when I try to run the Gstreamer test, I get 
```
WARNING: erroneous pipeline: no property "use-fixed-fps" in element "v4l2src0"
```

And selecting V4L2 in Ekiga gives a "No device found".

Any help would be appreciated.

yup, i just upgraded to feisty fawn 7.04 and the isight doesnt not work at all.  i googled a lot about this same error that you got, you are the only other person in the world that posted that error.  i like how the volume/backlight/eject buttons all work nicely but could someone please help us on this isight issue?? i have applied the isight.patch in the tutorial from that guys blog and nothing happened still got the same error.. actually when i initially tried to extract the AppleVideoSupport firmware (right after i installed) it said there was already an isight with firmware found!! what???
:confused:

---

### Post by (pr) on 2007-04-28
I have the same error. 

> pieterjan@pieterjan-laptop:~$ WARNING: erroneous pipeline: no property "use-fixed-fps" in element "v4l2src0"

---

### Post by yannoo on 2007-05-09
Same erroneous pipeline here on feisty (7.04) on a MBP.

I have gstreamer0.10-plugins-bad and gstreamer0.10-plugins-bad-multiverse installed, so the problem does not come from there.
In Ekiga, the device cannot be found with either V4L or V4L2 (but maybe having both is bad?).
The uvcvideo drivers loads well. It seems like the problem might be coming from the binding with V4L2...

```
$ lsmod|grep videouvcvideo               42500  0 
videodev               28160  1 uvcvideo
v4l2_common            25216  2 uvcvideo,videodev
v4l1_compat            15236  2 uvcvideo,videodev
video                  16388  0 
usbcore               134280  10 uvcvideo,hci_usb,ndiswrapper,appletouch,xpad,usbhid,appleir,uhci_hcd,ehci_hcd

```

Looking on packages.debian.org, it seems like the only package that has something to do with the string "v4l2src" is in the gstreamer plugins good ([http://packages.debian.org/cgi-bin/search_contents.pl?word=v4l2src&searchmode=searchword&case=insensitive&version=unstable&arch=i386](http://packages.debian.org/cgi-bin/search_contents.pl?word=v4l2src&searchmode=searchword&case=insensitive&version=unstable&arch=i386))

When trying to execute the gst-launch-0.10, I get the following results (note the two variants)(translated from french, so may differ slightly from english):
```

$ gst-launch-0.10 v4l2src use-fixed-fps=false ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=640,height=480 ! ffmpegcolorspace ! ximagesink
WARNING: erroneous pipeline: no property "use-fixed-fps" in element "v4l2src0"

$ gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=640,height=480 ! ffmpegcolorspace ! ximagesink
Putting pipeline in PAUSE...
ERROR: the pipeline refuses to get in pause.
ERROR : of element /pipeline0/v4l2src0 : Cannot identify device '/dev/video0'.
Additional debug information :
v4l2_calls.c(404): gst_v4l2_open (): /pipeline0/v4l2src0:
system error: No file or directory of this type
Assigning pipeline to NULL ...
FREEING pipeline ...

```

More fun stupid testing... I went in /dev and looked at the latest devices created and I found that interesting "ptmx" which I have no idea what it is, so I decided to try something funny and link /dev/video0 (which doesn't exist) to that /dev/ptmx:
```

$ sudo ln -s /dev/ptmx /dev/video0
$ sudo gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=640,height=480 ! ffmpegcolorspace ! ximagesink
Putting pipeline in PAUSE...
ERROR: the pipeline refuses to get in pause.
ERROR : the element /pipeline0/v4l2src0 : Error getting capabilities for device '/dev/video0': It isn't a v4l2 driver. Check if it is a v4l1 driver.
Additional debug information :
v4l2_calls.c(70): gst_v4l2_get_capabilities (): /pipeline0/v4l2src0:
system error: Invalid argument
Assigning pipeline to NULL ...
FREEING pipeline ...

```

Seems like the link is not done between /dev/video0 (which doesn't exist) and the real device anchor on the system. Now I don't know how to check which device is created or used by v4l2...

Anybody?

If anybody is subscribed to v4l2 mailing-list, could they please ask them to have a look at this post?

---

### Post by pacanukeha on 2007-05-12
I too am having the same problem with no use-fixed-fps and no /dev/video1

---

### Post by rdwtux on 2007-05-14
I have the same problem as mentioned above. 

Has anyone gotten this working?

---

### Post by buschi on 2007-05-17
same problem here... just wanted to add that it worked fine with feisty herd 5 (i did not test the beta version).

---

### Post by rdwtux on 2007-05-17
I did get my 1st gen Macbook Core Duo iSight working reliably... however I'm crossing my fingers I don't have to do it again as it was a bit wacky. 

Check out the webpage here with the patches... just download the all-in-one, don't worry about the rest. 
[http://i-nz.net/projects/linux-kernel/](http://i-nz.net/projects/linux-kernel/)

here are some very rough instructions i made for myself...
1 download the all in one patch from the website above.
2 untar, make, sudo make install of the all-in-one
3 here's the weird step:
    if you followed the Macbook wiki for installing the isight your going to have 2 versions of uvcvideo.ko on your system.
```
/lib/modules/2.6.20-15-generic/kernel/ubuntu/media/usbvideo/uvcvideo.ko
/lib/modules/2.6.20-15-generic/usb/media/uvcvideo.ko
```

    make sure two versions of uvcvideo.ko are the newer one (from the all-in-one download).. i believe the one in the ubuntu-specific module directory has to be replaced.

4 reinstall the all-in-one.. make; sudo make install;

Sorry for the very rough notes.. let me know if it works for you.

---

### Post by rei_t_ex on 2007-05-17
Thanks for the suggestion, rdwtux, but it did not work for me (also running a 1st gen Macbook).  Then again, I have been trying to get my isight to work for so long that maybe I have screwed something up elsewhere...

Will be interesting to see how others get along.

---

### Post by rdwtux on 2007-05-17
do you have the line in your rc.local to load the iSight firmware?  It comes from the macbook wiki

/etc/rc.local
```
/root/extract /root/AppleUSBVideoSupport
```

you should be able to see if the firmware is loading properly at startup just by trying to load it again using the line in the rc.local.  if it's loading properly, then the uvcvideo should just need to be patched (with the all-in-one download)..

Oh, one other thing I did do, i used the version of the firmware that comes with the all-in-one download package  rather than the version that comes an updated OSX install.. I don't know if that makes any difference. it's in the "firmware" directory of the downloaded package once unpacked.

sorry I can't offer better instructions.. i can't undo mine to try it again.

---

### Post by yannoo on 2007-05-29
This worked for me (until I applied the kernel update yesterday - I guess I need to recompile against the new kernel)

---

### Post by rdwtux on 2007-05-29
yeah, mine broke with the kernel update as well... when you compile the 'all-in-one' patched uvcvideo it installs them in the module dir of the current kernel, so with each kernel update you'll have to recompile the uvcvideo all-in-one... that is, until they fix uvcvideo in the kernel.

---

### Post by tulula on 2007-05-30
I am a first time Linux user, after using Macs since 1992 and I must say that so far I am pleased. Alas, I am a computer engineer, so getting all the things working has been fun.

I got it working in my Macbook Pro C2D replacing the kernel modules and modprobing... So far so good... Thanks for the help!!!!!!!!!!!

---

### Post by scorpio2002 on 2007-05-30
it worked until I rebooted -.-

---

### Post by rdwtux on 2007-05-30
scorpio2002, are you sure your loading the firmware in your rc.local?

You should have a line in your /etc/rc.local such as 
> /root/extract /root/AppleUSBVideoSupport

---

### Post by russo.mic on 2007-06-07
ARRRGGGG!!!

I had it working and now it just doesnt!  The worst kind of problem is one that makes no sense.   I turn to you my friends, to save my brains from the bashing there recieveing as I beat my head against the wall.

So, at one point, I had the GT Streamer test working.  However now, I get:

russo@russo-laptop:~$ gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=640,height=480 ! ffmpegcolorspace ! ximagesink
Setting pipeline to PAUSED ...
ERROR: Pipeline doesn't want to pause.
ERROR: from element /pipeline0/v4l2src0: Could not negotiate format
Additional debug info:
gstbasesrc.c(1865): gst_base_src_start (): /pipeline0/v4l2src0:
Check your filtered caps, if any
Setting pipeline to NULL ...
FREEING pipeline ...


In addition,  I try ekiga, both verson 2.0.3 from the repo, and a downloaded 2.0.9, and i both cases all I got was the camera working, but with these green lines over the entire screen.  
After an attempt at a reinstallation, now I don't even get the image with green lines, just a bunch of green static.  
Any ideas or help would be great!  

Thanks in advance, Russo

edit:
Okay,  this:

gst-launch-0.10 v4l2src ! ffmpegcolorspace ! xvimagesink

Now gets a grabled green gtstreamer window.  

Damn.

---

### Post by MrMEEE on 2007-06-13
Can anyone please help getting kopete-0.12.2 to compile?? I've grabbed the tarball from [http://kopete.kde.org/releases.php](http://kopete.kde.org/releases.php).. no matter if i add the isight patch or not i get alot of compile error, all related to "undefined reference to `QString"... can anyone please lead me the right way??

---

### Post by tideline on 2007-06-14
Worked for me too!  Thanks...

---

### Post by phonky on 2007-06-16
Great work dude,

wanted to add myself to the list of users who successfully followed your guide.

-------------------------------------------------------
MacBook Pro 15"
Feisty 7.04
Dual boot rEFIt

---

### Post by tigerplug on 2007-06-20
Where can you get the firmware?

---

### Post by mustang on 2007-06-23
Thanks a lot. Your quick installation directions worked perfectly on my first generation macbook running 2.6.20 kernel.

---

### Post by ivesjd on 2007-06-25
Heres a photobooth like program called cheese.
[http://live.gnome.org/Cheese](http://live.gnome.org/Cheese)

---

### Post by maluka on 2007-06-28
i'm complettely lost. if is there a series of things i need to do to get it installed? as someone who has been cold turkey off linux for the last year i need a bit more detailed instructions please :) all i know is sudo apt-get. nything beyond that confuses me and it must confuse many more noobs. after downloading from here [http://i-nz.net/projects/linux-kernel/](http://i-nz.net/projects/linux-kernel/) , what is the procedure, step by step please. also, my touch pad is very jumpy:(

---

### Post by cyberdork33 on 2007-06-28
I would get the touchpad fixed first. there are some threads on that around here somewhere (I have none on hand to link to as I do not use a Apple laptop).

The iSight how-to is pretty straight forward... all you have to do, pretty much, is copy/paste the commands on the first post. The URL you posted is the website for information. The post directly below that is where the first thing you need to download is taken care of. you might actually need to click/download it because this forum makes the URLs display differently (shortens) and so copy/pasting will fail in that regard.

---

### Post by rdwtux on 2007-06-28
Maluka, 

Start here: 

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
 - this is the main macbook documentation. 

Then work out any extra features/errors afterwards.

---

### Post by André Schnabel on 2007-06-29
Works perfect on my 24" iMac with Feisty. Thanks rapido!

---

### Post by grim1234 on 2007-06-30
Can anyone tell me if this works with skype?

---

### Post by benanzo on 2007-06-30
skype for linux doesn't have video support yet

---

### Post by yannoo on 2007-07-05
Works great with MBP 17", thanks!

---

### Post by Pausanias on 2007-07-17
Hi

Thanks for your efforts. My question: does anyone know whether ekiga  running on linux can connect to a mac user on iChat? This guy ( [http://ubuntuforums.org/showthread.php?t=254476](http://ubuntuforums.org/showthread.php?t=254476) ) asked the same question but appears to have had no luck whatsoever getting a response. Hopefully you experts can chime in.

Many many thanks for your answer!

P

---

### Post by benanzo on 2007-07-17
As far as I know iChat is just a standard SIP client like Ekiga.  I don't know of any reason why they couldn't talk to each other.

[Here]("http://wiki.ekiga.org/index.php/Which_programs_work_with_Ekiga_%3F") is the "Official" compatibility list for Ekiga (though any standard SIP client will work.)

---

### Post by Pausanias on 2007-07-18
Well, iChat is not on that compatibility list. And I've only heard reports of failure when trying to connect to iChat using ekiga. iChat works by connecting people through the AOL AIM network. As far as I can tell, there is no way for ekiga to initiate a chat request with iChat. I am sure that if someone were able to get ekiga to actually initiate a chat request with iChat, then they would be able to talk to each other. But apparently the roadblock is that first request for init.

What really surprises me is that nowhere on the ekiga website is iChat even mentioned. Don't believe me? [try the Google search](http://www.google.com/search?hl=en&q=site%3Aekiga.org+ichat&btnG=Google+Search). This is too bad, since iChat is very popular with mac users, is free when you buy a mac, and works exceedingly well (even my mother-in-law can figure out how to use it).

---

### Post by hoc on 2007-07-21
> **rdwtux said:**
> I did get my 1st gen Macbook Core Duo iSight working reliably... however I'm crossing my fingers I don't have to do it again as it was a bit wacky. 

Check out the webpage here with the patches... just download the all-in-one, don't worry about the rest. 
[http://i-nz.net/projects/linux-kernel/](http://i-nz.net/projects/linux-kernel/)

here are some very rough instructions i made for myself...
1 download the all in one patch from the website above.
2 untar, make, sudo make install of the all-in-one
3 here's the weird step:
    if you followed the Macbook wiki for installing the isight your going to have 2 versions of uvcvideo.ko on your system.
```
/lib/modules/2.6.20-15-generic/kernel/ubuntu/media/usbvideo/uvcvideo.ko
/lib/modules/2.6.20-15-generic/usb/media/uvcvideo.ko
```

    make sure two versions of uvcvideo.ko are the newer one (from the all-in-one download).. i believe the one in the ubuntu-specific module directory has to be replaced.

4 reinstall the all-in-one.. make; sudo make install;

Sorry for the very rough notes.. let me know if it works for you.

I have a Macbook 2nd generation Core2Duo (got it at the beginning of July 2007).

The method above worked for me in Kubuntu (gutsy-kernel 2.6.22-8-generic) with only 1 minor, but important difference. The weird step you are talking about is almost correct. 

The all-in-one package writes the ubuntu file, so instead of overwriting the ubuntu-specific file, you need to overwrite the other file. My guess is that udev uses that one, while the kernel uses the ubuntu one.

```

sudo cp /lib/modules/2.6.22-8-generic/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/2.6.22-8-generic/usb/media/uvcvideo.ko

```

This way /dev/video0 get's created and you get a device 'Built-In iSight' in Ekiga.

Thx for the info rwdtux. 

And as always I only tried this inverse swap after hours of apt-getting and troubleshooting... ;)

**[edit]Rapido mailed me that his script now compensates for this gotcha. [/edit]**

---

### Post by pveith on 2007-07-24
@hoc: Does your iSight work with gstreamer-properties? In gutsy mine works only with ekiga and i get a "could not negotiate format", when trying to access the isight cam with gstreamer-properties. And the gst-launch-0.10 command does not work. Is this the same for you?

---

### Post by MichaëlVD on 2007-07-24
> **pveith said:**
> @hoc: Does your iSight work with gstreamer-properties? In gutsy mine works only with ekiga and i get a "could not negotiate format", when trying to access the isight cam with gstreamer-properties. And the gst-launch-0.10 command does not work. Is this the same for you?

pveith, mine doesn't even work with ekiga... are you on an intel iMac as well? If so, which guide did you follow to get it to work in ekiga? Thanks!

---

### Post by cyberdork33 on 2007-07-24
This guide should work fine. I have used it several times without a problem.

You only need to follow the "New Quick Install" section

---

### Post by MichaëlVD on 2007-07-25
Thanks, it worked indeed. I had to change the following though:

$ sudo mv /lib/modules/$(uname -r)/kernel/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/$(uname -r)/kernel/ubuntu/media/usbvideo/uvcvideo.ko.original

On my computer, the media/ directory is directly under the `uname -r` directory, without the kernel/ directory in between.

---

### Post by cyberdork33 on 2007-07-25
> **MichaëlVD said:**
> Thanks, it worked indeed. I had to change the following though:

$ sudo mv /lib/modules/$(uname -r)/kernel/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/$(uname -r)/kernel/ubuntu/media/usbvideo/uvcvideo.ko.original

On my computer, the media/ directory is directly under the `uname -r` directory, without the kernel/ directory in between.
Interesting. Hope this will help others that might have a problem.

---

### Post by Wittiga on 2007-07-25
Is there a way to install this via apt-get and just make isight work?

---

### Post by cyberdork33 on 2007-07-25
> **Wittiga said:**
> Is there a way to install this via apt-get and just make isight work?

No, as stated in the tutorial, the uvcvideo module is included in feisty, but does not work. you need to get the fixed version. It is very easy to install, just follow the directions.

---

### Post by MichaëlVD on 2007-07-26
Is this guide supposed to work for sound as well? I can see the picture in ekiga, but I cannot record any sound.

---

### Post by cyberdork33 on 2007-07-26
> **MichaëlVD said:**
> Is this guide supposed to work for sound as well? I can see the picture in ekiga, but I cannot record any sound.

This guide is for the iSight, that's it.

---

### Post by YannickDefais on 2007-07-27
> **Pausanias said:**
> Well, iChat is not on that compatibility list. And I've only heard reports of failure when trying to connect to iChat using ekiga. iChat works by connecting people through the AOL AIM network. As far as I can tell, there is no way for ekiga to initiate a chat request with iChat. I am sure that if someone were able to get ekiga to actually initiate a chat request with iChat, then they would be able to talk to each other. But apparently the roadblock is that first request for init.

What really surprises me is that nowhere on the ekiga website is iChat even mentioned. Don't believe me? [try the Google search](http://www.google.com/search?hl=en&q=site%3Aekiga.org+ichat&btnG=Google+Search). This is too bad, since iChat is very popular with mac users, is free when you buy a mac, and works exceedingly well (even my mother-in-law can figure out how to use it).

Hi,

I maintain the Ekiga wiki. We do not mention iChat because it seems not able to connect to any other SIP softphone. I guess Apple simply does not want to allow that because there is no technical reason for this.

Complain to Apple.

Regards,
Yannick

---

### Post by phetre on 2007-07-27
Hi MichaelVD,

You may be able to get your microphone working by following the instructions in this thread: [http://ubuntuforums.org/showthread.php?t=438762](http://ubuntuforums.org/showthread.php?t=438762) Specifically, you should try setting the Input Source to "Line," then back to "Mic." Make sure the "Mic as Output" switch is disabled, and the "Mux" level on the Input tab is fairly high.

Unfortunately my recorded sound is choppy and gross, but at least it's progress...

---

### Post by feisty@mbc2d on 2007-08-01
Hi,

I have my iSight working in feisty. Both gstreamer test and ekiga work fine. cheese on the other hand, scrambles the picture. No webcam in any other application. My questions:

1) Is there a way to record the video stream from gstreamer?
2) Is there a way to tell other apps like camorama, aMSN and such to communicate with the iSight via v4l2?

Thanks,

---

### Post by cyberdork33 on 2007-08-01
> **feisty@mbc2d said:**
> Hi,

I have my iSight working in feisty. Both gstreamer test and ekiga work fine. cheese on the other hand, scrambles the picture. No webcam in any other application. My questions:

1) Is there a way to record the video stream from gstreamer?
2) Is there a way to tell other apps like camorama, aMSN and such to communicate with the iSight via v4l2?

Thanks,

As long as you set the default video device in gstreamer-properties then it should be available in any app that supports v4l2

---

### Post by YannickDefais on 2007-08-01
> **cyberdork33 said:**
> As long as you set the default video device in gstreamer-properties then it should be available in any app that supports v4l2

Well, supporting V4L2 *might* be different from supporting gstreamer.

e.g. Ekiga support V4L2 (a kernel API), but do not support gstreamer.

Regards,
Yannick

---

### Post by cyberdork33 on 2007-08-02
Wouldn't passing the gstreamer test mean that gstreamer can in fact use the device?

---

### Post by lezig2laisilles on 2007-08-05
Thanks a lot. the sh script works like a charme for me on my macbook core2!

---

### Post by erbedo on 2007-08-26
Hi
   on my macbook this procedure doesn't work.
It went fine through all the steps, but when i try to use for instance gqcam to see the images from the isight, the brightness starts to dazzle and I can't see anything. Other programs suck kopete or ekiga recognize the camera but display nothing.
I found in dmesg the following:
```
applesmc: wait status failed: 5 != 50
applesmc: wait status failed: 5 != 50
applesmc: wait status failed: 5 != 50
applesmc: wait status failed: 5 != 50
applesmc: wait status failed: 5 != 50
applesmc: wait status failed: 5 != 50
applesmc: wait status failed: 5 != 50
applesmc: wait status failed: 5 != 50
applesmc: wait status failed: 5 != 50
applesmc: wait status failed: 5 != 50
applesmc: wait status failed: 5 != 50
applesmc: wait status failed: 5 != 50
```
Could this be the problem?

Regards

---

### Post by karl_kashofer on 2007-09-01
Hi !

I tried the superfast method, but all i get in dmesg is this:

usbcore: registered new interface driver uvcvideo
USB Video Class driver (v0.1.0)
usbcore: deregistering interface driver uvcvideo
uvcvideo: iSight: firmware already loaded.
uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8501)
uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
usbcore: registered new interface driver uvcvideo
USB Video Class driver (v0.1.0)

There is no /dev/video device. This is on a Macbook 13.3 2.16Ghz 
I compiled my own kernel to get the touchpad working, so I am on 2.6.22. Could there be a missing kernel config option ?

Thanks,
Karl

---

### Post by cyberdork33 on 2007-09-02
The modified uvcvideo module in this how to is not yet compatible with 2.6.22

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105638](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105638)

---

### Post by centime on 2007-09-09
I finally managed to get my iSight camera work with kopete, using a "2nd gen" macbook (linux kernel 2.6.21)

I mainly followed the tutorial of this topic, here are the two main points :

- The iSight driver on my OSX partition was too recent, i needed to get an older version of the AppleUSBVideoSupport. 

- Although everything was fine in ekiga and mplayer i had a green screen in kopete (0.12.5), i had to get latest SVN version of kopete (stable branch) and now I've got full video support.

here's a reminder of the steps I've done [http://titix.org/blog/macbook-2nd-gen-isight-kopete-09-09-2007.html]("http://titix.org/blog/macbook-2nd-gen-isight-kopete-09-09-2007.html")

I hope this will be useful !

---

### Post by cyberdork33 on 2007-09-09
> **centime said:**
> I finally managed to get my iSight camera work with kopete, using a "2nd gen" macbook (linux kernel 2.6.21)

I mainly followed the tutorial of this topic, here are the two main points :

- The iSight driver on my OSX partition was too recent, i needed to get an older version of the AppleUSBVideoSupport. 

- Although everything was fine in ekiga and mplayer i had a green screen in kopete (0.12.5), i had to get latest SVN version of kopete (stable branch) and now I've got full video support.

here's a reminder of the steps I've done [http://titix.org/blog/macbook-2nd-gen-isight-kopete-09-09-2007.html](http://titix.org/blog/macbook-2nd-gen-isight-kopete-09-09-2007.html)

I hope this will be useful !

I had the newest firmware working in ekiga on my 2.6.22.6 kernel. I got a bit excited when I read this post, but the older firmware still doesn't seem to fix the problem with gstreamer... oh and the mplayer command gave a green screen... ekiga works fine though.

---

### Post by centime on 2007-09-10
I didn't  succeed in using the iSight camera directly with gstreamer (using gst-launch) or an application based upon gstreamer (such as Cheese) too. (gstreamer related pb ?)
With mplayer, using a larger resolution (640x480) or different fps shows a green screen too, but works fine @ 320x240 / 30 fps.

---

### Post by cyberdork33 on 2007-09-10
> **centime said:**
> I didn't  succeed in using the iSight camera directly with gstreamer (using gst-launch) or an application based upon gstreamer (such as Cheese) too. (gstreamer related pb ?)
Yes, Cheese relies on gstreamer working.

---

### Post by MichaëlVD on 2007-09-27
,,,which means that it's getting very late for the isight camera in my imac to work with Gutsy on the default gutsy kernel :-(

---

### Post by cyberdork33 on 2007-09-27
> **MichaëlVD said:**
> ,,,which means that it's getting very late for the isight camera in my imac to work with Gutsy on the default gutsy kernel :-(
yep or any 2.6.22 kernel. Although they have made progress...

---

### Post by tuaris on 2007-11-08
The "super easy script" has a small error.  

Open up the script with a text editor and change the line that says:

cd against-revision-100

to:

cd against-revision-140

---

### Post by cyberdork33 on 2007-11-08
> **tuaris said:**
> The "super easy script" has a small error.  

Open up the script with a text editor and change the line that says:

cd against-revision-100

to:

cd against-revision-140
.

---

### Post by panda1988 on 2008-01-08
> **cyberdork33 said:**
> You shouldn't need a script at all anymore in gutsy.
i used the super easy script and my isight works well on ekiga in my new macbook white santarosa with ubuntu gutsy.
unfortunately, it is different on cheese. i cant use it. the application starts and blocks immediatley. gstreamer test cant open neither from terminal in admin mode. i need help

thanks in advance, i am a newbie

---

### Post by cyberdork33 on 2008-01-08
> **panda1988 said:**
> i used the super easy script and my isight works well on ekiga in my new macbook white santarosa with ubuntu gutsy.
unfortunately, it is different on cheese. i cant use it. the application starts and blocks immediatley. gstreamer test cant open neither from terminal in admin mode. i need help

thanks in advance, i am a newbieThis how to is more up to date, although it really should be the same thing...
[http://ubuntuforums.org/showthread.php?p=2957042](http://ubuntuforums.org/showthread.php?p=2957042)

I think you need to block the isight_usb module to prevent it from loading as described there.

---

### Post by cyrustajik on 2008-04-27
hello everyone
I just got a C2D intel macbook. Its one of those late 2006 edition. after putting ubuntu 7.10 on it I decided to get the isight working.
for the past 2 days I have tried EVERYTHING i could find n these forums. used the quick install mentioned here , compiled myself, used different extracting methods (which by the extracted the firmware successfully).
But still no luck. the isight doesnt work. Ive tried cheese, ekiga and all the rest. 
I keep getting the " Device "/dev/video0" does not exist." error.
I think the problem is that my ubuntu doesnt know anything about my isight. I get the following when I use lsusb command.
Bus 005 Device 003: ID 05ac:8300 Apple Computer, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 05ac:8240 Apple Computer, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 05ac:021b Apple Computer, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 05ac:8205 Apple Computer, Inc. 
Bus 004 Device 001: ID 0000:0000  

and in my hardware information window I cant find anything about isight.
it seems so many people have managed to get this working here so I would really appreciate your help.
by the way my kernal is :  2.6.22-14-generic 

thanks in advance for your help
cheers
Cyrus

---

### Post by phetre on 2008-04-27
Hi Cyrustajik,

I have an older Macbook (1st-gen), but Etienne Bersac's isight-firmware-tools worked for me on Hardy. Get it here ([https://launchpad.net/isight-firmware-tools](https://launchpad.net/isight-firmware-tools)), extract the archive, and follow the instructions in the HOWTO file.

There was an effort to get it into the Hardy repositories, but it failed due to an apparent miscommuncation. The sad story is here: [https://bugs.edge.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/185634](https://bugs.edge.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/185634)

Good luck!

---

### Post by cyrustajik on 2008-04-27
hey
thanks for the quick reply.
Ive been through that website. got the isignt tools and extracted the firmware fine. still nothing. Im using gusty and it took a while to get the isight tools off the website but It was ok at the end. unfortunately the isight still doesnt work!

---

### Post by phetre on 2008-04-27
Oh, sorry that didn't work for you. I haven't used Gutsy for a while now, but it seemed like there was a chance that would work.

Does the kernel say anything about your iSight during the boot process? Here's what I get from a warm boot (note that the firmware appears be loaded already, since the iSight shows up as 8501 rather than 8300, like yours):

```
dmesg | grep -E '(uvcvideo|5\-4)'
[   26.518649] usb 5-4: new high speed USB device using ehci_hcd and address 3
[   26.650776] usb 5-4: configuration #1 chosen from 1 choice
[   39.176168] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8501)
[   39.178470] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   39.180400] usbcore: registered new interface driver uvcvideo
```

---

### Post by cyrustajik on 2008-04-28
hey
thanks for the reply.
this is what I get:
cyrus@cyrus-Macbook:~$ dmesg | grep -E '(uvcvideo|5\-4)'
[    5.544000] usb 5-4: new high speed USB device using ehci_hcd and address 3
[    5.676000] usb 5-4: configuration #1 chosen from 1 choice
[   21.336000] usbcore: registered new interface driver uvcvideo

as you can see there is no mention of isight what so ever!
I think my macbook doesnt even bothr looking for it!

any ideas ? :)

cheers then
cyrus

---

### Post by cyberdork33 on 2008-04-28
please post in the new forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

IFT is only for hardy it doesn't work in gutsy

---

