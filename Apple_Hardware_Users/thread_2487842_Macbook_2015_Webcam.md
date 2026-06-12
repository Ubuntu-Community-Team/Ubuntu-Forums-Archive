---
title: "Macbook 2015 Webcam"
date: 2023-06-16
forum: Apple Hardware Users
---

### Post by unfirthman on 2023-06-16
Hello all,

I am using Ubuntu 22.04.2 on an early 2015 MacBook Air, which has a 720p FaceTime HD Camera. I would like to use this camera, however I cannot get Cheese or Google Meet to recognize this device.

I have followed this [method]("https://www.linux.org/threads/installing-linux-on-an-imac.26009/") to install *isight-firmware-tools* and *AppleUSBVideoSupport*. No success.

And this [method]("https://github.com/patjak/facetimehd/wiki/Get-Started") to install the FaceTime HD Firmware. Also no success.

I have also installed *guvcview* and it does not recognize the camera.

Thanks in advance for the help!

---

### Post by ActionParsnip on 2023-06-16
What is the output of
```

lsb_release -a; uname -a; lsusb

```
Thanks

---

### Post by unfirthman on 2023-06-20
Thanks for replying! Sorry it took a few days to respond... I didn't have notifications on.

The output of the prompts:

```

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.2 LTS
Release:    22.04
Codename:    jammy
Linux USER 5.19.0-45-generic #46~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Wed Jun 7 15:06:04 UTC 20 x86_64 x86_64 x86_64 GNU/Linux
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05ac:0291 Apple, Inc. Apple Internal Keyboard / Trackpad
Bus 001 Device 006: ID 05ac:828f Apple, Inc. Bluetooth USB Host Controller
Bus 001 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Thank you!

---

### Post by MAFoElffen on 2023-06-20
These instructions (from [https://www.linux.org/threads/installing-linux-on-an-imac.26009/](https://www.linux.org/threads/installing-linux-on-an-imac.26009/)) seemed to have also worked for MacBook Air's with Ubuntu 20.04 LTS...
> 
**iSight Webcam**

The iSight Webcam requires some tools installed. You will need a file  from the MacOSX installation media (which I will attach below but it  will need to be unzipped). Once you have the media you can find the file  at: &#8220;/Mac OS X Install  DVD/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport&#8221;.  Place this file in a location that you can type in the full path  location. In a Terminal you need to type the following command:

*sudo apt install isight-firmware-tools*

After the download and installation a window will appear which will ask  you if you have the &#8216;AppleUSBVideoSupport&#8217; file. Answer &#8216;Yes&#8217; and you  will be prompted for the file location. Delete the current path and type  in the location of the file and press Enter. The drivers should be  extracted from the Apple file you copied. At this point you need to  reboot to get the webcam to work.

I tested the iSight video camera using &#8216;Cheese&#8217;. To install &#8216;Cheese&#8217; you need to open a Terminal and perform the commands:

[I]sudo apt update
sudo apt install cheese -y[/I]

For users at AskUbuntu, the Mint Forum, etc from other distributions.

---

### Post by unfirthman on 2023-06-23
Thank you for the help!

I have isight-firmware-tools v1.6-4 installed on this computer, but still nothing from either Cheese or GoogleMeet.

I did find this old bug associated with the Launchpad package: [https://bugs.launchpad.net/ubuntu/+source/isight-firmware-tools/+bug/757394](https://bugs.launchpad.net/ubuntu/+source/isight-firmware-tools/+bug/757394)

Any other help or advice would be greatly appreciated! Maybe it is time for me to register a bug report?

Most of these bug reports are pretty old: [https://bugs.launchpad.net/isight-firmware-tools/+bugs?orderby=-datecreated&start=0](https://bugs.launchpad.net/isight-firmware-tools/+bugs?orderby=-datecreated&start=0)

The last update is from 2019, I'm not sure if that is helpful!

Thanks again

---

### Post by QIII on 2023-06-23
Moved to Apple Hardware Users

---

### Post by MAFoElffen on 2023-06-23
I doubt that anyone is going to update a bug report from 11.04 beta, circa 2011...

I found some more recent instructions for 22.04: [https://askubuntu.com/questions/1430547/webcam-not-working-in-ubuntu-22-04-on-macbook-air](https://askubuntu.com/questions/1430547/webcam-not-working-in-ubuntu-22-04-on-macbook-air)

I wanted to make sure this time that I was recommending something that actually worked. I can confirm that it works on my A1181 MacBook (3,1), running 22.04.2 with the HWE kernel series.

Note that it doesn't work with 'cheese'. In fact, if I try to start 'cheese' on mine, that app locks up. It does work with 'guvcview'...

---

### Post by unfirthman on 2023-06-26
You are right! This has finally worked for me.

Ultimately it was my error. This is a two-step process: [extracting the firmware]("https://github.com/patjak/facetimehd/wiki/Get-Started#firmware-extraction"), then [installing it]("https://github.com/patjak/facetimehd/wiki/Installation#get-started-on-ubuntu"). These directions are on two different pages [here]("https://github.com/patjak/facetimehd/wiki/Get-Started#firmware-extraction") and [here]("https://github.com/patjak/facetimehd/wiki/Installation#get-started-on-ubuntu").

I had extracted the firmware just fine, but did not go through the process of installing it.

[This post]("https://askubuntu.com/questions/990218/camera-not-working-on-macbook-pro/1215628#1215628") was quite helpful; it condenses the directions into one block of code.

Thanks everyone for the help!

---

