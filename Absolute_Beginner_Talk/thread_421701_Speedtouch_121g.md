---
title: "Speedtouch 121g"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by HaydnRobinson on 2007-04-24
Hi,

I am a complete newbie and have never used Linux before.  I've installed Ubuntu successfully, but unfortunately it doesn't recognise my Speedtouch 121g USB adapter.

Now, I've been round all the threads here and elsewhere, printed them all off and nothing works.

I've downloaded the ndiswrapper 1.8 from sourgeforge to my Windows data drive as this seemed to be required.  What do I do with it?  Do I move it to a linux drive/folder?  If so where - I don't understand any of the folder structures on Linux?  I've read the install document that comes with it, but all I get is access denied, file/folder not found, etc. errors and the program fails to compile.

I've followed the instructions on thread 245651.  This simply says that to start with run:  "sudo apt-get install ndiswrapper-utils".  Problem is this just says ndiswrapper-utils cannot be found.  Great.

Could someone please explain as simply and clearly as possible how on earth I get my Speedtouch 121g to work under Ubuntu (7.04 version)?  My router is set up with WPA encryption and its SSID hidden from view, so any help here too would be appreciated.

Thanks if you can help.

Haydn

---

### Post by mikeyphi on 2007-04-24
Have a look here 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

for a start - if that doesn't help come back again!

---

### Post by HaydnRobinson on 2007-04-24
How complicated can something so simple be?

I've found all the necessary instructions and seem to have made a small amount of progress.  One step says to run the following:

sudo apt-get install dh-make fakeroot gcc-3.4 build-essential

This whinges that it doesn't know what dh-make and gcc-3.4 are.  What are they?  Where are they?  How (dare  I ask) do you install these?

Sounds stupid, but is there not the Windows equivalent to an msi file in Linux?  I can't believe it's so difficult to install something.

---

### Post by BOK on 2007-07-20
I've come til the point when using the latest NDISwrapper (v1.47), inserting the 121g USB dongle and Ubuntu 7.04 crashes with a kernel-panic time after time...
```
Jul 20 10:44:50 localhost kernel: [  480.972571]  <0>Kernel panic - not syncing: Fatal exception in interrupt
Jul 20 10:44:50 localhost kernel: [  480.972578]  BUG: at arch/i386/kernel/smp.c:547 smp_call_function()
Jul 20 10:44:50 localhost kernel: [  480.972589]  [smp_call_function+323/336] smp_call_function+0x143/0x150[

Etc. etc.
```
I gave up trying.

---

### Post by HaydnRobinson on 2007-07-20
I've upgraded my XP-Ubuntu dual boot machine to Vista and blatted Ubuntu for good.  Vista may have issues with drivers, but at least my wireless works straight off. 

The Ubuntu home page claims:
"Everything you need on one CD, which provides a complete working environment"

Clearly not!:mad:

---

### Post by Mornedhel on 2007-07-20
The equivalent of *.msi, install.exe, setup.exe... etc., is usually nicely wrapped in a .deb package which does all of the installing (open with gdebi). Since you don't have access to Internet on your Ubuntu, you'll have to manually download ndiswrapper-utils for your architecture on packages.ubuntu.com .

Also, once you do have Internet access, you'll notice how installing something on Ubuntu is much simpler than on Windows. This is something newcomers often complain about, because they try downloading an installer off some non-Ubuntu-related site (often an install script, a foreign package, or even sources). All you have to do is open Add/Remove or Synaptic, check what you wish to install, and Apply : the software is downloaded, installed in all the right places, and shortcuts are (most of the time) added.

Until then, you can only install the packages on the install CD.

FYI, wireless worked out of the box in my Feisty. Sound also did. It took about 1 min 30 secs to install my ATI X1400, and no reboot was needed (not in the strict sense of the word "reboot"). Compare this to the installation procedure on my WinXP box : install separately drivers for sound, ethernet, video card, rebooting inbetween each installation. And there was a different CD for each one.

---

