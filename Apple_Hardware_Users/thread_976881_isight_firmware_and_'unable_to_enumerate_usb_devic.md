---
title: "isight firmware and 'unable to enumerate usb device' issues"
date: 2008-11-09
forum: Apple Hardware Users
---

### Post by nitrofurano on 2008-11-09
Hi!

I recently saw some tips for using for using iSight on Ubuntu, but i'm having some problems with it

[http://www.rickycampbell.com/isight-intrepid/#comment-198](http://www.rickycampbell.com/isight-intrepid/#comment-198)

When i follow the steps from there, i start getting a ‘unable to enumerate usb device on port 7&#8242; when having sight.fw at /lib/firmware/ , and the whole boot process hangs there. And when rarelly booting (mostly with every usb devices disconnected), iSight is not working...

guest@macbook:~$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.27-7-generic)
xinerama 0: 1280×800+0+0
can’t open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available
guest@macbook:~$

i'm using Ubuntu 8.10 amd64, and the MacBook is model A1181 (core2duo 1.85ghz), and the pressuposed '/lib/firmware/isight.fw' md5sum is 6d4b6764538e85ab9e7e15ed21b7a60c 

If some more info is needed, please let me know
thanks!

---

### Post by cyberdork33 on 2008-11-09
This is the same md5sum I get and it seems to work fine. Can you get your model version as defined in the "Before You Post" link in my signature?

---

### Post by wolfen13fr on 2008-11-12
Hello, 

I have the same MacBook model (A1181) and I have the same issue too : my iSight still not work with Intrepid Ibex (it used to work with Hardy Heron).

I try [this tutorial](https://wiki.edubuntu.org/MacBook/SantaRosa#iSight), [this other one](http://ubuntu-tutorials.com/2008/11/03/enable-apple-isight-camera-ubuntu-810/) and many others but no result.

Do you have an idea ?
(sorry for my bad english, I'm french ...)

---

### Post by Rog-Mahal on 2008-11-12
*bump*

I believe I have the same macbook (2,1). I have isight.fw extracted in /lib/firmware. My md5sum is 6d4b6764538e85ab9e7e15ed21b7a60c  /lib/firmware/isight.fw

I've rebooted to no avail, and cheese doesn't give any errors except 'No camera found!'

lsusb lists the camera:
```
$ lsusb
Bus 005 Device 003: ID 05ac:8501 Apple, Inc. Built-in iSight [Micron]
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 011: ID 05ac:8205 Apple, Inc. Bluetooth HCI MacBookPro
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 05ac:8240 Apple, Inc. IR Receiver [build-in]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ac:021a Apple, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
I have also tried unloading and then loading the uvcvideo module. I am mystified, I had this working fine on Hardy.

Any thoughts would be appreciated!

---

### Post by cyberdork33 on 2008-11-12
Cheese/GStreamer is broken in Intrepid.

Try using ekiga to test.

[https://help.ubuntu.com/community/AppleiSight](https://help.ubuntu.com/community/AppleiSight)

Additionally, I couldn't get it to work until I used ift-load (part of isight-firmware-tools) to load the firmware manually, and it works on every boot now.

---

### Post by Rog-Mahal on 2008-11-13
Hmm, I tried to run 'ift-load' and terminal spat out 'command not found' I have isight-firmware-tools installed, is another package I need? I must be missing something, I did a quick google search and found that during Ibex testing the isight-firmware-tools package was shipped without this command, is that still the case?

---

### Post by cyberdork33 on 2008-11-13
> **Rog-Mahal said:**
> Hmm, I tried to run 'ift-load' and terminal spat out 'command not found' I have isight-firmware-tools installed, is another package I need? I must be missing something, I did a quick google search and found that during Ibex testing the isight-firmware-tools package was shipped without this command, is that still the case?

The version in the mactel-support PPA is newer than the intrepid version.

The command my not be in your PATH, so you have to specify the directory. use 'locate ift-load' to find it, then run it explicitily like /usr/bin/ift-load (or whatever the path is).

---

### Post by Rog-Mahal on 2008-11-13
Found another issue. First of all the man page for this command is completely unreadable (as in it's a garbled mass of characters). Secondly, here's the output 

```
roger@hephaestos:~$ /usr/lib/udev/ift-load /lib/firmware/isight.fw
ift-load: Unable to read firmware isight.fw.
roger@hephaestos:~$ /usr/lib/udev/ift-load 
ift-load: Unable to read firmware isight.fw.

```

---

### Post by cyberdork33 on 2008-11-13
try sudo. I just ran it without anything beyond the command itself and it loaded the firmware just fine.

---

### Post by Rog-Mahal on 2008-11-13
No luck running it with sudo and without specifying the file. It still says it's unable to load. What version of isight-firmware-tools should I have? Should I try to delete everything and start again from scratch?

---

### Post by Romu on 2008-11-14
I take benefit of this thread to expose my problem with iSight. I recently downgraded my Macbook Pro 2G from Intrepid to Hardy 64 bits, because of blocking wifi issues.

This is the first time I use a 64 bits Ubuntu on my computer. I added the mactel PPA, but there is no entry in Synaptics for "isight".

I tried to download the package from [this site]("http://ubuntu-tutorials.com/2008/11/03/enable-apple-isight-camera-ubuntu-810/") and I have an unsatisfied dependency error on libgcrypt11 which is well installed on my mac.

Any idea? Thanks.

---

### Post by cyberdork33 on 2008-11-16
> **Romu said:**
> This is the first time I use a 64 bits Ubuntu on my computer. I added the mactel PPA, but there is no entry in Synaptics for "isight".

IFT was not in the repos in Hardy. You need to add the mactel-support PPA to your sources:
[https://wiki.ubuntu.com/MactelSupportTeam#Mactel-Support%20PPA](https://wiki.ubuntu.com/MactelSupportTeam#Mactel-Support%20PPA)

---

### Post by Romu on 2008-11-17
Thanks Cyberdork, but as I said the mactel PPA is already in my sources.list, and it simply appears none of the mactel ppa packages are provided for x64. I tried the keywords isight, apple, usbhid and Synaptics returns no entry from mactel ppa.

Any idea?

---

### Post by cyberdork33 on 2008-11-17
> **Romu said:**
> Thanks Cyberdork, but as I said the mactel PPA is already in my sources.list, and it simply appears none of the mactel ppa packages are provided for x64. I tried the keywords isight, apple, usbhid and Synaptics returns no entry from mactel ppa.

Any idea?

Yes I see that the package did not build the 64 bit package. I will let the dev know.

You can download the Intrepid build here:
[http://packages.ubuntu.com/intrepid/isight-firmware-tools](http://packages.ubuntu.com/intrepid/isight-firmware-tools)

You can build the official source from here:
[http://bersace03.free.fr/ift/](http://bersace03.free.fr/ift/)

EDIT: PPA should be fixed now.

---

### Post by Rog-Mahal on 2008-11-18
Well, I'm not entirely sure what changed, but my isight is working fine now. I never did get ift-load to work, but I guess it doesn't matter now :) Thanks for all the help!

---

### Post by Romu on 2008-11-19
Same Cyberdork, no mactel ppa packages visible in Synaptics for Hardy x64.

If I download the Intrepid package I have an unsatisfied dependency error on libgcrypt11 which is though well installed...but with the Hardy version not the Intrepid one indeed.

---

### Post by Rog-Mahal on 2009-05-05
I had my isight functioning with the green capture issue under 9.04, but oddly enough now I'm having the same problem as these earlier posters. I have isight.fw in /lib/firmware, yet I have no /dev/video0 and ift-load cannot read the isight.fw file. Any thoughts? I've tried deleting the isight.fw and removing isight-firmware-tools, but no luck. Rebooting also had no effect.

---

### Post by Rog-Mahal on 2009-05-06
Rather embarrassingly, shutting down (NOT rebooting) got the isight to load, however the green capture issue is still there for cheese and ekiga, even with the gstreamer pipeline fix in place in gconf. gstreamer-properties test reveals correct video coloring, however.

---

### Post by mauricescherer on 2010-11-13
> **Rog-Mahal said:**
> Found another issue. First of all the man page for this command is completely unreadable (as in it's a garbled mass of characters). Secondly, here's the output 

```
roger@hephaestos:~$ /usr/lib/udev/ift-load /lib/firmware/isight.fw
ift-load: Unable to read firmware isight.fw.
roger@hephaestos:~$ /usr/lib/udev/ift-load 
ift-load: Unable to read firmware isight.fw.

```


I tried this:

sudo /usr/lib/udev/ift-load --firmware /lib/firmware/

then run Cheese and... Voila!!

---

