---
title: "HOWTO: Fix iSight in Hardy"
date: 2008-04-24
forum: Apple Hardware Users
---

### Post by benanzo on 2008-04-24
Unfortunately despite all the great improvements we've seen in Hardy, the iSights on our Apple Intel Macs got left a little out in the cold.  First we're having problems getting the firmware to load, then after fixing that the stock uvcvideo.ko doesn't create a valid video chain which causes the camera not to work at all.

Below are the instructions to get your iSight up and running.

First, if you haven't already done it go ahead and add the Mactel PPA to your /etc/apt/sources.list.  This is a good repo to find Mactel-specific fixes and features, including where we'll find the tools to fix our iSights.

```

# Mactel PPA
deb http://ppa.launchpad.net/mactel-support/ubuntu hardy main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu hardy main

```

Next open a terminal and do:
```

$ sudo apt-get update
$ sudo apt-get install isight-firmware-tools

```

Go ahead and put the iSight firmware (AppleUSBVideoSupport) in /lib/firmware

Now we're going to use one of the utilities we just installed to extract the iSight firmware so it can be properly loaded:
```

$ sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport

```

We're now done messing with the iSight firmware portion of the fix.  Now test to see if your iSight works by doing:
```

$ sudo modprobe -r uvcvideo
$ sudo modprobe uvcvideo

```

If your camera works (test with Cheese or Ekiga) then you're done.  Otherwise you might try compiling a new uvcvideo as detailed below:

```

$ sudo modprobe -r uvcvideo
$ sudo mv /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko.orig
$ sudo apt-get install libusb-0.1-4 libusb-dev linux-headers-$(uname -r) subversion
$ svn co --revision 205 svn://svn.berlios.de/linux-uvc/linux-uvc/trunk uvcvideo-r205
$ cd uvcvideo-r205
$ make
$ sudo make install
$ sudo depmod -ae
$ sudo modprobe uvcvideo

```
If it worked then Cheese should autostart after that last command.  If it doesn't then try starting Cheese by hand.  If the camera still doesn't work go ahead and try rebooting.  It is also possible that halting your machine (power off completely) then starting it up again instead of a simple reboot will fix the problem.

Good Luck!

---

### Post by Dale Cooper on 2008-04-24
I got no problem at all, I just followed the basic instructions and it worked instantly.

I own a MB C2D 2nd gen. Is this a problem with newer machines?

---

### Post by benanzo on 2008-04-24
I'm using a first-gen MacBook (1,1)

This howto is in response to the following two bugs:
[https://bugs.launchpad.net/mactel-support/+bug/185634](https://bugs.launchpad.net/mactel-support/+bug/185634)
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/216310](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/216310)

---

### Post by cyberdork33 on 2008-04-24
> **benanzo said:**
> Now we need to mess with the uvcvideo module so it will create a valid video chain when it's loaded.

To do this we need to compile a new version of uvcvideo.

As far as I know, the version of uvcvideo in Hardy was working fine. (It is still working for me...) I think this might only affect certain models.

Also, going to try to get Dirk to replace the old iSight How-To in the FAQ.

---

### Post by benanzo on 2008-04-24
> **cyberdork33 said:**
> As far as I know, the version of uvcvideo in Hardy was working fine. (It is still working for me...) I think this might only affect certain models

That may be true since my iSight was working fine circa Alpha 3 but has stopped in Hardy final.  I found that I could only get it to work again by compiling a new uvcvideo in addition to the firmware extraction bit.

But you're right, compiling a new module *may* not be necessary.

---

### Post by exoticorn on 2008-04-24
Thanks for the HOWTO.
One note for those following it, though: You should really try your isight after just the firmware extraction - I followed the whole HOWTO and my isight only worked in ekiga, not in cheese. I then reverted the uvcvideo.ko back to the original one and everything worked fine.

---

### Post by benanzo on 2008-04-25
> **exoticorn said:**
> Thanks for the HOWTO.
One note for those following it, though: You should really try your isight after just the firmware extraction - I followed the whole HOWTO and my isight only worked in ekiga, not in cheese. I then reverted the uvcvideo.ko back to the original one and everything worked fine.

Good suggestion, I have updated the howto accordingly.

---

### Post by guj4_n3b3sk4 on 2008-04-25
I have edited source.list file as it was said in 1st step of howto. I follow steps and when I do 3rd code box, here's what happens:

```
ugljesha@blackbox:~$ sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport -f /lib/firmware/isight.fw 
** Message: Found Mac OS X.4 intel driver

** ERROR **: Unable to open /lib/firmware/lib/firmware/isight.fw for writing.
aborting...
Aborted
```

Where's the problem?

---

### Post by mabovo on 2008-04-25
> **guj4_n3b3sk4 said:**
> I have edited source.list file as it was said in 1st step of howto. I follow steps and when I do 3rd code box, here's what happens:

```
ugljesha@blackbox:~$ sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport -f /lib/firmware/isight.fw 
** Message: Found Mac OS X.4 intel driver

** ERROR **: Unable to open /lib/firmware/lib/firmware/isight.fw for writing.
aborting...
Aborted
```

Where's the problem?

Same here  :(

mabovo@macbook:~$ sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport -f /lib/firmware/isight.fw
** Message: Found Mac OS X.4 intel driver

** ERROR **: Unable to open /lib/firmware/lib/firmware/isight.fw for writing.
aborting...
Cancelado
mabovo@macbook:~$

Also running gstreamer-properties I got this:

mabovo@macbook:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
mabovo@macbook:~$

- Not supported std output video device for autovideosink channel
- None device found std input video for v4l2 plugin

Do we need still blacklist isight_usb in Hardy ?

Can we set iSight be loaded with udev instead of hal  ?

---

### Post by cyberdork33 on 2008-04-25
> **mabovo said:**
> Same here  :(

mabovo@macbook:~$ sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport -f /lib/firmware/isight.fw
** Message: Found Mac OS X.4 intel driver

** ERROR **: Unable to open /lib/firmware/lib/firmware/isight.fw for writing.
aborting...
Cancelado
mabovo@macbook:~$
Try running the command without the last part:
```
sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport
```

> **mabovo said:**
> Do we need still blacklist isight_usb in Hardy ?
I don't think it even exists

> **mabovo said:**
> Can we set iSight be loaded with udev instead of hal  ?The IFT dev said that there is a switch or something to force the use of udev, but as you know, there are problems using udev to do it. It should use hal.

mabovo, you have already done this part anyway... All you need to do is compile the newer uvcvideo module

---

### Post by guj4_n3b3sk4 on 2008-04-25
Strange, that command was giving me same result as the problem above, but worked now. But, anyway, problem is still here:

```
ugljesha@blackbox:~$ sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport
[sudo] password for ugljesha: 
** Message: Found Mac OS X.4 intel driver
** Message: Firmware extracted successfully in /lib/firmware/isight.fw
** Message: Apply patch 0 : Fix video control interface descriptor
** Message: Apply patch 1 : Fix video streaming interface descriptor
** Message: Apply patch 2 : Fix video streaming device qualifier
** Message: Firmware patched successfully
ugljesha@blackbox:~$ sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport -f /lib/firmware/isight.fw
** Message: Found Mac OS X.4 intel driver

** ERROR **: Unable to open /lib/firmware/lib/firmware/isight.fw for writing.
aborting...
Aborted
```

---

### Post by cyberdork33 on 2008-04-25
> **guj4_n3b3sk4 said:**
> Strange, that command was giving me same result as the problem above, but worked now. But, anyway, problem is still here
I don't understand your issue. Your first command extracts the firmware, then you try to extract it again to a different location with the second command. The second is not needed at all.

---

### Post by guj4_n3b3sk4 on 2008-04-25
Mea culpa. Mixed commands. I've done 1st successfuly, but Skype or Ekiga doesn't recognize iSight. :](*,)](*,) Where the hell is the problem then, and if that two clients doesn't recognize any video device, is that indicator that iSight hasn't been configurated?

---

### Post by mabovo on 2008-04-25
> **cyberdork33 said:**
> Try running the command without the last part:
```
sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport
```

mabovo, you have already done this part anyway... All you need to do is compile the newer uvcvideo module

Ok, I have already compiled uvcvideo and as You suggested 

mabovo@macbook:~$ sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport
[sudo] password for mabovo: 
** Message: Found Mac OS X.4 intel driver
** Message: Firmware extracted successfully in /lib/firmware/isight.fw
** Message: Apply patch 0 : Fix video control interface descriptor
** Message: Apply patch 1 : Fix video streaming interface descriptor
** Message: Apply patch 2 : Fix video streaming device qualifier
** Message: Firmware patched successfully
mabovo@macbook:~$ sudo modprobe -r uvcvideo
mabovo@macbook:~$ sudo modprobe uvcvideo
mabovo@macbook:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': It was not possible identify device '/dev/video0'. [v4l2_calls.c(429): gst_v4l2_open (): /pipeline0/v4l2src3:
system error: File or directory not existent]
mabovo@macbook:~$

I will try reboot and see what happens.

Thanks anyway !

---

### Post by guj4_n3b3sk4 on 2008-04-25
```
ugljesha@blackbox:~$ gstreamer-properties 
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /pipeline2/v4lsrc2]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(429): gst_v4l2_open (): /pipeline3/v4l2src4:
system error: No such file or directory]
```

Same thing. Not even after reboot anything better.:confused:

---

### Post by mabovo on 2008-04-25
:popcorn: One more happy happy happy Mac user with Hardy Heron  :)

After reboot I got iSight working again.

Thanks, Tank You, Thank you very much.

:guitar:


Now I will start struggle with Skype 2.0  :lolflag:

---

### Post by cyberdork33 on 2008-04-25
> **guj4_n3b3sk4 said:**
> ```
ugljesha@blackbox:~$ gstreamer-properties 
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /pipeline2/v4lsrc2]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(429): gst_v4l2_open (): /pipeline3/v4l2src4:
system error: No such file or directory]
```Same thing. Not even after reboot anything better.:confused:
ok, it not working with gstreamer still... did you compile the uvcvideo module as suggested in the OP? Ekiga doesn't use gstreamer so testing it separately will give more information about the status of your system. also if you can check dmesg to make sure the firmware is loading on bootup.

---

### Post by guj4_n3b3sk4 on 2008-04-25
> **cyberdork33 said:**
> ok, it not working with gstreamer still... did you compile the uvcvideo module as suggested in the OP? Ekiga doesn't use gstreamer so testing it separately will give more information about the status of your system. also if you can check dmesg to make sure the firmware is loading on bootup.

How to compile uvcvideo module (if that are those lines modprobe ... I've done that).

Here's my dmesg from terminal: [http://nopaste.ns-linux.org/?NmNkZD]("http://nopaste.ns-linux.org/?NmNkZD")

Then what?

---

### Post by pveith on 2008-04-25
For some reason i can't get it too work too. It is listed in hardware, but tehre is simply no /dev/video0 created. Under hardware the isight is listed as /dev/bus/usb/005/005. Did i miss a step?

Edit: Even in dmesg it is listed:
snip
[   46.610096] Linux video capture interface: v2.00
[   46.791716] usbcore: registered new interface driver uvcvideo
[   46.791720] USB Video Class driver (SVN r205)
snap
So it should be up an running, but it isn't working.

---

### Post by cyberdork33 on 2008-04-25
> **guj4_n3b3sk4 said:**
> How to compile uvcvideo module (if that are those lines modprobe ... I've done that).

Here's my dmesg from terminal: [http://nopaste.ns-linux.org/?NmNkZD](http://nopaste.ns-linux.org/?NmNkZD)

Then what?
It doesn't look like uvcvideo is loading at all... Try ```
sudo modprobe uvcvideo
``` then see if things work. To make this automatic, add 'uvcvideo' to /etc/modules

> **pveith said:**
> For some reason i can't get it too work too. It is listed in hardware, but tehre is simply no /dev/video0 created. Under hardware the isight is listed as /dev/bus/usb/005/005. Did i miss a step?

Edit: Even in dmesg it is listed:
snip
[   46.610096] Linux video capture interface: v2.00
[   46.791716] usbcore: registered new interface driver uvcvideo
[   46.791720] USB Video Class driver (SVN r205)
snap
So it should be up an running, but it isn't working.
Did you install iSight-Firmware-Tools? It doesn't have anything about loading the firmware. if it is installed, is the firmware extracted and in /lib/firmware/ ?

---

### Post by pveith on 2008-04-25
> **cyberdork33 said:**
> It doesn't look like uvcvideo is loading at all... Try ```
sudo modprobe uvcvideo
``` then see if things work. To make this automatic, add 'uvcvideo' to /etc/modules


Did you install iSight-Firmware-Tools? It doesn't have anything about loading the firmware. if it is installed, is the firmware extracted and in /lib/firmware/ ?

Yes and Yes. There are two files in /lib/firmware.
AppleUSBVideoSupport and isight.fw

---

### Post by guj4_n3b3sk4 on 2008-04-25
> **cyberdork33 said:**
> It doesn't look like uvcvideo is loading at all... Try ```
sudo modprobe uvcvideo
``` then see if things work. To make this automatic, add 'uvcvideo' to /etc/modules


```
ugljesha@blackbox:~$ sudo modprobe uvcvideo
ugljesha@blackbox:~$ 
```

Nothing, huh?

I've added uvcvideo into /etc/modules.

---

### Post by pveith on 2008-04-25
You have to watch dmesg to see something.

mine said:
snip
[  862.395672] usbcore: deregistering interface driver uvcvideo
[ 1235.496305] usbcore: registered new interface driver uvcvideo
[ 1235.496315] USB Video Class driver (SVN r205)
snap

Problem remains, no firmware loading.

---

### Post by cyberdork33 on 2008-04-25
> **guj4_n3b3sk4 said:**
> ```
ugljesha@blackbox:~$ sudo modprobe uvcvideo
ugljesha@blackbox:~$ 
```Nothing, huh?

I've added uvcvideo into /etc/modules.You have to try to use the camera now... all that does is load the module. If it still doesn't work, try completely restarting first, but you may need to compile a new version of uvcvideo (linux-uvc) as instructed in the first post.

> **pveith said:**
> Problem remains, no firmware loading.Strange. Try using the ift-load command to load firmware manually:
```
/usr/lib/udev/ift-load -f /lib/firmware/isight.fw -b 005 -d 003
``` The numbers after b and d are the Device and Bus number respectively. These can be found in lsusb.

---

### Post by guj4_n3b3sk4 on 2008-04-25
Here's mine dmsg after adding uvcvideo to sources.

[http://nopaste.ns-linux.org/?NmU2MT]("http://nopaste.ns-linux.org/?NmU2MT")

Same line as yours, but no this line: [ 1235.496305] usbcore: registered new interface driver uvcvideo

Rember maybe from earlier posts on this theme that I've removed uvcvideo.mod from trash as a part of configuring iSight on Gutsy Gibbon. Is that maybe causing problems?

---

### Post by cyberdork33 on 2008-04-25
> **guj4_n3b3sk4 said:**
> Here's mine dmsg after adding uvcvideo to sources.

[http://nopaste.ns-linux.org/?NmU2MT](http://nopaste.ns-linux.org/?NmU2MT)

Same line as yours, but no this line: [ 1235.496305] usbcore: registered new interface driver uvcvideo

Rember maybe from earlier posts on this theme that I've removed uvcvideo.mod from trash as a part of configuring iSight on Gutsy Gibbon. Is that maybe causing problems?
I doubt that is the problem, but your firmware is still not loading. You will see a message that says something along the lines of "firmware successfully loaded"

---

### Post by pveith on 2008-04-25
> **cyberdork33 said:**
> You have to try to use the camera now... all that does is load the module. If it still doesn't work, try completely restarting first, but you may need to compile a new version of uvcvideo (linux-uvc) as instructed in the first post.

Strange. Try using the ift-load command to load firmware manually:
```
/usr/lib/udev/ift-load -f /lib/firmware/isight.fw -b 005 -d 003
``` The numbers after b and d are the Device and Bus number respectively. These can be found in lsusb.

Ola? I don't have this command. My package only comes with ift-export and ift-extract. No ift-load listed in the packages filelist.

---

### Post by guj4_n3b3sk4 on 2008-04-25
> **cyberdork33 said:**
> I doubt that is the problem, but your firmware is still not loading. You will see a message that says something along the lines of "firmware successfully loaded"

Can you tell me once more step by step how things should be done? I've DL isight-firmware-tools_1.2-0ubuntu0~ppa1_amd64. Double clicked it, instaled it. Then:

```
sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport
```
```

sudo modprobe -r uvcvideo
sudo modprobe uvcvideo
```

Added uvcvideo to sources. isight.fw is in /lib/firmware/
```

ugljesha@blackbox:/lib/firmware$ ls
2.6.22-14-generic  2.6.24-16-generic  AppleUSBVideoSupport  isight.fw
```

PS: About that command from post above mine, here's what I get:

```
ugljesha@blackbox:/lib/firmware$ /usr/lib/udev/ift-load -f /lib/firmware/isight.fw -b 005 -d 003
bash: /usr/lib/udev/ift-load: No such file or directory
ugljesha@blackbox:/lib/firmware$ cd /usr/lib/udev/
ugljesha@blackbox:/usr/lib/udev$ ls
fix-persistent-net.pl  migrate-fstab-to-uuid.sh  migrate-iftab.pl
```


What can I possibly forgot to do?

---

### Post by pveith on 2008-04-25
Could it be, that the 64-Bit Version is missing some files? n3b3sk4 and me seem to have a 64-Bit Version of Ubuntu installed. Can anyone confirm a runing isight on 64-Bit?

Found this: [https://launchpad.net/isight-firmware-tools/](https://launchpad.net/isight-firmware-tools/)
Tried to compile the tools myself installs hal-version. Not working. Installed udev: again not wroking and no ift-load.

---

### Post by pveith on 2008-04-25
Okay. My iSight is up and running.

Here is what i did:

Instead of installing from Repro i compiled the tools myself.
Download them from [https://launchpad.net/isight-firmware-tools/](https://launchpad.net/isight-firmware-tools/)

Do a ```
./configure  --enable-udev --disable-hal && make
``` 

followed by a ```
sudo checkinstall
```

(checkinstall will autobuild a package, which can be removed using synaptic / apt. Replace it by make install, if you want. But i recommand installing checkinstall, it is mutch easier to handle.)

Then do a udev restart ```
sudo invoke-rc.d udev restart
```.

Then do anything as state in the first message.

If in the end there is no sight in cheese try a ```
sudo /usr/local/lib/udev/ift-load -f /lib/firmware/isight.fw -b 005  -d 003
```

Where as the last two number (in my case 005 003) can be found in Hardwareinfo und usb->isight.

---

### Post by benanzo on 2008-04-25
> 
ugljesha@blackbox:~$ sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport -f /lib/firmware/isight.fw 
** Message: Found Mac OS X.4 intel driver

** ERROR **: Unable to open /lib/firmware/lib/firmware/isight.fw for writing.
aborting...
Aborted


Yikes, there seems to be a bit of a bug when using the -f switch to specify the extracted firmware location.

You should use this command instead:
```

$ sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport

```
Basically just take off the -f switch portion.  I've updated the howto.

---

### Post by cyberdork33 on 2008-04-25
> **guj4_n3b3sk4 said:**
> Can you tell me once more step by step how things should be done?
You have installed ift correctly. You need to compile uvcvideo now like is instructed in the first post of this thread.
    ```
sudo modprobe -r uvcvideo
     $ sudo mv /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko.orig
$ sudo apt-get install libusb-0.1-4 libusb-dev linux-headers-$(uname -r) subversion
$ svn co --revision 205 svn://svn.berlios.de/linux-uvc/linux-uvc/trunk uvcvideo-r205
$ cd uvcvideo-r205
$ make
$ sudo make install
$ sudo depmod -ae
$ sudo modprobe uvcvideo
```> **pveith said:**
> Do a ```
./configure  --enable-udev --disable-hal && make
```
Sorry, I didn't realize that was required to get the executable, i thought it was just to set it up for loading via udev. I don't know why the hal script is not loading the firmware for you.

Oh yea, one more thing to try that I just realized. You may need to completely shut down, then boot up. restarting causes the isight not to unload firmware and change it's device ID back to 8300. That may be required for the hal loader to load the firmware again.

---

### Post by guj4_n3b3sk4 on 2008-04-25
```
ugljesha@blackbox:~$ sudo mv /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko.orig
mv: cannot stat `/lib/modules/2.6.24-16-generic/ubuntu/media/usbvideo/uvcvideo.ko': No such file or directory
ugljesha@blackbox:~$ ./configure  --enable-udev --disable-hal && make
bash: ./configure: No such file or directory
ugljesha@blackbox:~$ 
```

Earlier this day I've compiled uvcvideo successfuly, but now it won't (check 1st command in shell log). :confused:

---

### Post by guj4_n3b3sk4 on 2008-04-25
Well, I'll be damned.

uvcvideo won't recompile, can't do -f, nothing worked at all. I've only listened to that advice, turned off Macbook, turned on, typed:

```
sudo apt-get install cheese
cheese &
```

just to see what program am I never gonna use, and when Cheese opened, I saw myself on the screen. :D iSight is working, duuno how, dunno why, but it's working! :D

---

### Post by cyberdork33 on 2008-04-25
> **guj4_n3b3sk4 said:**
>  iSight is working, duuno how, dunno why, but it's working! :D
Great!

when you run ./configure, you have to be in the uvcvideo source directory. no biggie, you already had it compiled!

---

### Post by cyberdork33 on 2008-04-29
> **benanzo said:**
> Yikes, there seems to be a bit of a bug when using the -f switch to specify the extracted firmware location.
It wasn't a bug, but certainly an odd behavior...
[https://bugs.edge.launchpad.net/isight-firmware-tools/+bug/222093](https://bugs.edge.launchpad.net/isight-firmware-tools/+bug/222093)

---

### Post by benanzo on 2008-04-30
I see, the -f switch specifies the basename, not full path.  That would explain why I didn't encounter that problem when I was testing the process while originally writing the howto.  I must have been in /lib/firmware and specified "-f isight.fw" without thinking about it.  Good to know.

---

### Post by mabovo on 2008-05-03
Updated to 2.6.24-17 and iSight stopped work. :(

Recompiled uvcvideo following this Howto but iSight don't give any signal of life.

I did one more step - reinitialize Hal or reboot ! and again no video streaming from iSight.

Has 2.6.24-17 introduced a regression for uvcvideo ?

---

### Post by cyberdork33 on 2008-05-03
> **mabovo said:**
> Updated to 2.6.24-17 and iSight stopped work. :(

Recompiled uvcvideo following this Howto but iSight don't give any signal of life.

I did one more step - reinitialize Hal or reboot ! and again no video streaming from iSight.

Has 2.6.24-17 introduced a regression for uvcvideo ?
where are you getting -17? -16 is the latest in the repos.

---

### Post by mabovo on 2008-05-03
> **cyberdork33 said:**
> where are you getting -17? -16 is the latest in the repos.


2.6.24-17.31 (Hardy-proposed)

---

### Post by cyberdork33 on 2008-05-03
> **mabovo said:**
> 2.6.24-17.31 (Hardy-proposed)
ok well that is not really stable, so file a bug. nobody should be using that yet.

---

### Post by mabovo on 2008-05-04
> **cyberdork33 said:**
> ok well that is not really stable, so file a bug. nobody should be using that yet.

I just installed it to check the new acpi proposal but didn't see any improvements in power consumption on my MacBook. Still Hot !

I think they are missing uvcvideo driver in ubuntu-modules for 2.6.24-17.

---

### Post by cyberdork33 on 2008-05-04
> **mabovo said:**
> I think they are missing uvcvideo driver in ubuntu-modules for 2.6.24-17.Like I said, if that is case then file a bug... I don't know what else to tell you.

---

### Post by shadowtrk on 2008-05-04
Ok i have a very odd problem i extracted the firmware from the apple file and useing the uvcvideo driver that came with 
Hardy I get a no video chain messages

 Linux video capture interface: v2.00
[ 2022.558786] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8501)
[ 2022.559151] uvcvideo: No valid video chain found.
[ 2022.559741] usbcore: registered new interface driver uvcvideo
[ 2022.560069] USB Video Class driver (v0.1.0)



When I compile a new uvcvideo driver When i load Its seems not to decte the Camera any more. i have the isight.fw file in /lib/firmware.

Linux video capture interface: v2.00
[  376.866268] usbcore: registered new interface driver uvcvideo
[  376.866277] USB Video Class driver (SVN r205)

---

### Post by cyberdork33 on 2008-05-04
> **shadowtrk said:**
> When I compile a new uvcvideo driver When i load Its seems not to decte the Camera any more. i have the isight.fw file in /lib/firmware.

Linux video capture interface: v2.00
[  376.866268] usbcore: registered new interface driver uvcvideo
[  376.866277] USB Video Class driver (SVN r205)
i don't see any error there...

---

### Post by Quillero on 2008-05-05
Hi friends.

I am a new member and owner of a MacBook Pro 2 gen. I HAD problems with my isight cam but with your first recommendations is ready. Cheese, Ekiga and Amsn run perfect. shutdown n turn on again and all right.

thanks you.

:)
Saludos desde Barranquilla.

---

### Post by dado483 on 2008-05-05
> **shadowtrk said:**
> Ok i have a very odd problem i extracted the firmware from the apple file and useing the uvcvideo driver that came with 
Hardy I get a no video chain messages

 Linux video capture interface: v2.00
[ 2022.558786] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8501)
[ 2022.559151] uvcvideo: No valid video chain found.
[ 2022.559741] usbcore: registered new interface driver uvcvideo
[ 2022.560069] USB Video Class driver (v0.1.0)



When I compile a new uvcvideo driver When i load Its seems not to decte the Camera any more. i have the isight.fw file in /lib/firmware.

Linux video capture interface: v2.00
[  376.866268] usbcore: registered new interface driver uvcvideo
[  376.866277] USB Video Class driver (SVN r205)

Same problem here! I have a 2,4 Ghz Core 2 Duo Macbook
Please help

---

### Post by cyberdork33 on 2008-05-05
> **dado483 said:**
> Same problem here! I have a 2,4 Ghz Core 2 Duo Macbook
Please help
there is no error in what you quoted. Please check the output of dmesg for an error message.

---

### Post by mattgaunt on 2008-05-05
This how-to was awesome, worked for me, although had to do the last bit and then shutdown and start again

Just for anyone who is wondering, im on 5th Gen MacBook

Thanks again

Gaunt

---

### Post by shadowtrk on 2008-05-06
Im not seeing any error and the camera will not work... and theres still no /dev/video created

---

### Post by cyberdork33 on 2008-05-06
[https://bugs.edge.launchpad.net/mactel-support/+bug/216310](https://bugs.edge.launchpad.net/mactel-support/+bug/216310)

---

### Post by mcoyle on 2008-05-14
I followed these instructions, and got the Sight to work. After a reboot it quit, and now I notice that sometimes it works and sometimes it doesn't. 

So if I boot and it's working, it will continue to work until I reboot, then it's a coin flip as to whether it will work again.

Nothing is changing in between boots.

Any ideas gang?

Michael

---

### Post by hajk on 2008-05-18
Very useful thread Benanzo! I just installed Hardy on my old 1,1 MacBook in a single-boot arrangement, and the iSight Howto was just the ticket. May be you could emphasize that compiling the uvcvideo module from SVN is *in addition to* the firmware extraction bit.

Now, I also have a new MacBook Pro 4,1 where I have installed Hardy in a VMware Fusion VM. Here, the iSight must be switched on in the bottom panel of the VMware window (one of the USB icons) before booting Hardy. No firmware loading is needed in this case (as Mac OS X takes care of that), and indeed the Hardy kernel recognizes the iSight and loads the uvcvideo module etc. There is no "video chain" message, and Cheese starts without problem.

Unfortunately, it only *starts* OK, because it either freezes or stops before you can do much with it. The dmesg command shows lots of```

........ uvcvideo: unknown event type 0.
........ uvcvideo: unknown event type 24.
```
error messages (the 24 is variable, the 0 isn't). Trying the uvcvideo module compiled from SVN showed no difference.

(I'm not sure whether this last problem belongs to the Apple forum section, but then the Virtualization section seems to treat only installing virtualization programmes in Linux...)

---

### Post by hajk on 2008-05-18
Further to my above post, I get the same problem in Ekiga: once the video is turned on the syslog fills with an never-ending stream of similar "unknown event" messages, at least until video is again switched off.

I now believe that the problem applies to all MacBook Pro 4,1 users running Linux with the uvcvideo driver, whether directly on the hardware or in a VM, so perhaps my complaint should be discussed here. I've found some correspondence, [http://lists.berlios.de/pipermail/linux-uvc-devel/2008-February/003083.html](http://lists.berlios.de/pipermail/linux-uvc-devel/2008-February/003083.html), but, alas, no solution.

---

### Post by hajk on 2008-05-18
I'm also, on the same MBP, running a Debian testing/unstable VM, alternating between it and the Ubuntu Hardy VM with a shared virtual HD for personal files. On the Debian VM I have now installed the latest linux-uvc-source package 0.1.0.svn193-2 from unstable, compiled it against the 2.6.25-2 kernel presently in testing, and switched to the new uvcvideo module. No, "unknown event" messages still there...

---

### Post by skiwithpete on 2008-05-18
I'm also on a Macbook 4,1.

I followed the instructions, and still cheese does not get a picture.  I see some other Macbook 4,1 users are having this problem.  Please update as soon as possible - with very simple instructions (still newb-ish) as I really would like to get this installed.

I don't even know what to post to tell you where the error lies.  I have the two files (AppleUSBVideoSupport & isight.fw) in /lib/firmware.  Everything seemed to work fine in the instructions - I just open cheese and don't get a vid...

Cheers,

P

---

### Post by cyberdork33 on 2008-05-18
> **skiwithpete said:**
> I don't even know what to post to tell you where the error lies.  I have the two files (AppleUSBVideoSupport & isight.fw) in /lib/firmware.  Everything seemed to work fine in the instructions - I just open cheese and don't get a vid...
does it work in ekiga?

---

### Post by skiwithpete on 2008-05-18
cyberdork33,

Yes it does work in Ekiga!!!

Can you help make cheese work?

P

---

### Post by cyberdork33 on 2008-05-18
> **skiwithpete said:**
> cyberdork33,

Yes it does work in Ekiga!!!

Can you help make cheese work?

P
well that means it is a problem with gstreamer or cheese itself.

run 'gstreamer-properties' and on the video tab, make sure that under Default Input, the Plugin is v4l2 and that "built-in isight" is selected under device. Then hit the test button.

Post back any issues or errors.

---

### Post by skiwithpete on 2008-05-18
Thanks for the help,

After changing the video input and pressing "test" a window popped up and said:

Failed to construct test pipeline for 'Video For Linux 2 (v4l2)'

The pipeline: v4l2src device="/dev/video0" (but I can't edit that anyways).

Also, this appeared in terminal before the test:

```

$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

```

All things froze after the test.


///  And then after rebooting.  Cheese worked beautifully.  Cheers for the help.

---

### Post by cyberdork33 on 2008-05-18
> **skiwithpete said:**
> ```

$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

```That is normal.

IDK why it worked after that!

---

### Post by tehkain on 2008-05-23
Is there anywhere I might find the firmware? The tool wants me to locate it on my system. I do not do not have OS X installed and I have the system setup perfectly so I cannot reinstall it(efi legacy etc).

---

### Post by tomas.teijeiro on 2008-05-31
I have a 2nd generation Intel Macbook, with Kubuntu Hardy installed from
Gutsy. The built-in isight have worked perfectly following these steps:
[http://ubuntuforums.org/showthread.php?t=764616](http://ubuntuforums.org/showthread.php?t=764616)

But since a few days ago, probably due an upgrade, the uvcvideo module can't be loaded.
dmesg shows this:

[ * 53.478360] uvcvideo: disagrees about version of symbol video_devdata
[ * 53.478366] uvcvideo: Unknown symbol video_devdata
[ * 53.478972] uvcvideo: disagrees about version of symbol video_unregister_device
[ * 53.478976] uvcvideo: Unknown symbol video_unregister_device
[ * 53.479172] uvcvideo: disagrees about version of symbol video_device_alloc
[ * 53.479175] uvcvideo: Unknown symbol video_device_alloc
[ * 53.479304] uvcvideo: disagrees about version of symbol video_register_device
[ * 53.479308] uvcvideo: Unknown symbol video_register_device
[ * 53.479722] uvcvideo: disagrees about version of symbol video_device_release
[ * 53.479726] uvcvideo: Unknown symbol video_device_release
[ * 53.514097] uvcvideo: disagrees about version of symbol video_devdata
[ * 53.514103] uvcvideo: Unknown symbol video_devdata
[ * 53.514705] uvcvideo: disagrees about version of symbol video_unregister_device
[ * 53.514709] uvcvideo: Unknown symbol video_unregister_device
[ * 53.514903] uvcvideo: disagrees about version of symbol video_device_alloc
[ * 53.514906] uvcvideo: Unknown symbol video_device_alloc
[ * 53.515035] uvcvideo: disagrees about version of symbol video_register_device
[ * 53.515038] uvcvideo: Unknown symbol video_register_device
[ * 53.515449] uvcvideo: disagrees about version of symbol video_device_release
[ * 53.515453] uvcvideo: Unknown symbol video_device_release

I can't understand what is the problem, and I can't find much
information about it. Does anybody knows the solution?

Thank you very much

---

### Post by cyberdork33 on 2008-05-31
> **tomas.teijeiro said:**
> I have a 2nd generation Intel Macbook, with Kubuntu Hardy installed from
Gutsy. The built-in isight have worked perfectly following these steps:
[http://ubuntuforums.org/showthread.php?t=764616](http://ubuntuforums.org/showthread.php?t=764616)

I can't understand what is the problem, and I can't find much
information about it. Does anybody knows the solution?
Did you try to recompile the uvcvideo driver?

Also, the difference between the two locations is one is the ubuntu provided version, and one is the version you originally compiled. To make sure that you are not loading the ubuntu version you can rename it with .bak on the end.

---

### Post by tomas.teijeiro on 2008-05-31
Yes, i've recompiled some revisions of the driver, but the error persists.
 I can confirm that the location of the module that I try to load is /lib/modules/2.6.24-17-generic/usb/media/uvcvideo.ko.

Thanks

---

### Post by cyberdork33 on 2008-05-31
the message sounds like it is saying that the module is incompatible with your current kernel. If you have recompiled after the recent kernel update, IDK why you are getting that issue. Someone else may be able to share some better info with you.

---

### Post by tomas.teijeiro on 2008-06-03
I have just updated to the 2.6.24.18 kernel, and the isight is working by default, with the standard ubuntu module :)

---

### Post by Stu09 on 2008-06-06
I get this error when following the directions :(

It's on a MacBook C2D
```
stuart@MacBook:~$ sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport

** ERROR **: Unable to read driver /lib/firmware/AppleUSBVideoSupport.
aborting...
Aborted
stuart@MacBook:~$ 

```

---

### Post by theverant on 2008-06-06
Can anyone confirm this working on a Black 2.4 Macbook (4.1)?  I can't seem to get my iSight working at all. :confused:

After updates the iSight is now working.  Thanks for all the info!

---

### Post by mochiko on 2008-06-06
when i follow the second command in the last box, this is what i get:

chitra@chitra-laptop:~$ sudo mv /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko.orig
mv: cannot stat `/lib/modules/2.6.24-17-generic/ubuntu/media/usbvideo/uvcvideo.ko': No such file or directory


what should i do?

---

### Post by cyberdork33 on 2008-06-06
> **Stu09 said:**
> I get this error when following the directions :(

It's on a MacBook C2D
```
stuart@MacBook:~$ sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport

** ERROR **: Unable to read driver /lib/firmware/AppleUSBVideoSupport.
aborting...
Aborted
stuart@MacBook:~$ 

```

Is the AppleUSBVideoSupport file in /lib/firmware ? That command assume you have already got the AppleUSBVideoSupport file off your OSX partition.

> **mochiko said:**
> when i follow the second command in the last box, this is what i get:

chitra@chitra-laptop:~$ sudo mv /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko.orig
mv: cannot stat `/lib/modules/2.6.24-17-generic/ubuntu/media/usbvideo/uvcvideo.ko': No such file or directory


what should i do?You should upgrade and reboot first. The current kernel is 2.6.24-18

---

### Post by AbuAnsar on 2008-06-06
Hi guys, I've followed the whole how-to and Isight works fine when tested with Cheese and gstreamer-properties, but doesn't work at all with Ekiga. Any suggestions?

---

### Post by Stu09 on 2008-06-10
> **cyberdork33 said:**
> Is the AppleUSBVideoSupport file in /lib/firmware ? That command assume you have already got the AppleUSBVideoSupport file off your OSX partition.



How do I get it from my OSX partition ? Is that a different process from installing the isight tools from the repo ?

---

### Post by Stu09 on 2008-06-11
Bump. anyone ? bueller ??

---

### Post by cyberdork33 on 2008-06-11
> **Stu09 said:**
> How do I get it from my OSX partition ? Is that a different process from installing the isight tools from the repo ?
It is located at this path:
/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport

---

### Post by Stu09 on 2008-06-12
Thankyou cyberdork. I know have working iSight :)

but my wireless is now broken :confused: I guess that's for another thread

---

### Post by i_ll_be on 2008-06-24
Hello all,

Thanks for this topic.

I have a 1st gen MBP and I had no luck trying the original Howto on page 1.
So I tried the variant suggested on page 3 by pveith (compilation from the sources). This one is OK, my isight is working after I launch the command :
> sudo /usr/local/lib/udev/ift-load -f /lib/firmware/isight.fw -b 005  -d 003

The problem is that I need to launch this command each time after reboot. Any idea on how to make the driver launch automatically at boot ?

Thks for your help ! :)

---

### Post by i_ll_be on 2008-06-27
Any idea ?

I tried to add the command in the session manager (to be launched at startup) but it doesn't work...:(

---

### Post by phaedral on 2008-06-30
> Stu09 said: but my wireless is now broken  I guess that's for another thread

I had the same problem, had to re-build madwifi using the instructions at [https://help.ubuntu.com/community/MacBookPro#Wireless](https://help.ubuntu.com/community/MacBookPro#Wireless)

---

### Post by mabovo on 2008-07-01
They messed again with last kernel update 2.6.24-19. 
iSight doesn't work again close to 8.0.4.1

---

### Post by bluenode on 2008-07-05
I can confirm mabovo's experience.  

When I installed Hardy on my new Macbook on 5/3/08, the iSight worked perfectly.  An undate about a month later broke it.  It began to work again within a couple of weeks.  Now, with 2.6.24-19, it's broken again.  

It works for a few seconds before crashing.  Dmesg shows messages such as:  "uvcvideo: Failed to resubmit video URB (-45)."

Since I rely on Skype for work, I'm particularly anxious for this to get fixed.  Googling shows this to have been an off-and-on problem for a couple of years.  Can anyone explain why this happens and what is required for a fix?

---

### Post by i_ll_be on 2008-07-07
> **i_ll_be said:**
> Hello all,

Thanks for this topic.

I have a 1st gen MBP and I had no luck trying the original Howto on page 1.
So I tried the variant suggested on page 3 by pveith (compilation from the sources). This one is OK, my isight is working after I launch the command :


The problem is that I need to launch this command each time after reboot. Any idea on how to make the driver launch automatically at boot ?

Thks for your help ! :)

Hello,

I found the way to make the firmware loading automatically.

I wrote this script :
> #! /bin/bash

bus=`lsusb | awk '/iSight/ { print $2 ; }'`
device=`lsusb | awk '/iSight/ { print $4 ; }' | cut -c1-3`

command="/usr/local/lib/udev/ift-load -f /lib/firmware/isight.fw -b "$bus"  -d "$device

$command

and copied it to /etc/init.d :
```
cp launch_isight /etc/init.d/
```

and then add it to boot tasks :
```
sudo update-rc.d launch_isight defaults 90
```

The script does not install the firmware, it just runs the ift-load command (bus and device numbers are updated automatically).

Hope this helps !

---

### Post by cyberdork33 on 2008-07-08
> **i_ll_be said:**
> I found the way to make the firmware loading automatically.
The latest IFT already automatically loads the firmware at boot. There is no need for a separate script.

---

### Post by i_ll_be on 2008-07-09
> **cyberdork33 said:**
> The latest IFT already automatically loads the firmware at boot. There is no need for a separate script.

I have installed firmware tools version 1.2 from the sources, it does not load automatically.

Which version do you have ?

---

### Post by cyberdork33 on 2008-07-10
> **i_ll_be said:**
> I have installed firmware tools version 1.2 from the sources, it does not load automatically.

Which version do you have ?
I have 1.2 from here:
[https://launchpad.net/~mactel-support/+archive]("https://launchpad.net/%7Emactel-support/+archive")

Should be the same though as the developer of the software is the one that adds it to the PPA. This version uses HAL to detect the iSight rather than udev. you can force the udev method if you like. details are on the IFT website:
[http://bersace03.free.fr/ift/](http://bersace03.free.fr/ift/)

---

### Post by mbaucco on 2008-07-14
Hello,

I am a new Ubuntu user (v8.04) and I tried the instructions on the first post to get my iSight working. Although I did not get any errors while following the various steps, Cheese locks up my Intel macbook when I try to test the iSight. I only have ubuntu on my macbook, so I downloaded the camera file from a website I found on another forum post here. Could that be what I did wrong? I am comfortable with mac and windows, but very new to linux.

Thanks!
Matt

---

### Post by cyberdork33 on 2008-07-15
> **mbaucco said:**
> Hello,

I am a new Ubuntu user (v8.04) and I tried the instructions on the first post to get my iSight working. Although I did not get any errors while following the various steps, Cheese locks up my Intel macbook when I try to test the iSight. I only have ubuntu on my macbook, so I downloaded the camera file from a website I found on another forum post here. Could that be what I did wrong? I am comfortable with mac and windows, but very new to linux.

Thanks!
Matt
it could be a bad firmware file. try testing in 'gstreamer-properties' instead of cheese to make sure that it is just not cheese having issues.

---

### Post by mbaucco on 2008-07-16
Thanks! I re-installed Ubuntu and did everything over nad now it works, though I lost wireless right after fixing the iSight and had to reinstall the latest wireless drivers to get it back. Everything looks good now though!

thanks again,
Matt

---

### Post by Derviansoul on 2008-07-23
> **benanzo said:**
> Unfortunately despite all the great improvements we've seen in Hardy, the iSights on our Apple Intel Macs got left a little out in the cold.  First we're having problems getting the firmware to load, then after fixing that the stock uvcvideo.ko doesn't create a valid video chain which causes the camera not to work at all.

Below are the instructions to get your iSight up and running.

First, if you haven't already done it go ahead and add the Mactel PPA to your /etc/apt/sources.list.  This is a good repo to find Mactel-specific fixes and features, including where we'll find the tools to fix our iSights.

```

# Mactel PPA
deb http://ppa.launchpad.net/mactel-support/ubuntu hardy main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu hardy main

```

Next open a terminal and do:
```

$ sudo apt-get update
$ sudo apt-get install isight-firmware-tools

```

Go ahead and put the iSight firmware (AppleUSBVideoSupport) in /lib/firmware

Now we're going to use one of the utilities we just installed to extract the iSight firmware so it can be properly loaded:
```

$ sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport

```

We're now done messing with the iSight firmware portion of the fix.  Now test to see if your iSight works by doing:
```

$ sudo modprobe -r uvcvideo
$ sudo modprobe uvcvideo

```

If your camera works (test with Cheese or Ekiga) then you're done.  Otherwise you might try compiling a new uvcvideo as detailed below:

```

$ sudo modprobe -r uvcvideo
$ sudo mv /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko.orig
$ sudo apt-get install libusb-0.1-4 libusb-dev linux-headers-$(uname -r) subversion
$ svn co --revision 205 svn://svn.berlios.de/linux-uvc/linux-uvc/trunk uvcvideo-r205
$ cd uvcvideo-r205
$ make
$ sudo make install
$ sudo depmod -ae
$ sudo modprobe uvcvideo

```
If it worked then Cheese should autostart after that last command.  If it doesn't then try starting Cheese by hand.  If the camera still doesn't work go ahead and try rebooting.  It is also possible that halting your machine (power off completely) then starting it up again instead of a simple reboot will fix the problem.

Good Luck!


hello

just done your tutorial with hardy x64 and works great with ekiga not with cheese, i dunno if it's being posted or not,but i just had to do:


CODE]
$ sudo apt-get update
$ sudo apt-get install isight-firmware-tools
[/CODE]

Go ahead and put the iSight firmware (AppleUSBVideoSupport) in /lib/firmware

and restart hal
```
/etc/init.d/hal restart
```

great works 
regards

---

### Post by stickwithjosh on 2008-07-25
Just wanted to document that I had to go through all of the above steps (including a reboot) but my iSight (built in on a MacBook Pro 2.3 GHz Core 2 Duo) is working in both Cheese and Ekiga. 

Cheers!

---

### Post by atoc on 2008-07-31
Awesome. Thanks for this.
My iSight is working w/ Cheese, Ekiga and Skype.

---

### Post by jarhead14 on 2008-07-31
So I attempted setting this up and all went fine until I got to the command:

```
sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport
```

It gave me:

```
** ERROR **: Unable to read driver /lib/firmware/AppleUSBVideoSupport.
aborting...
Aborted

```

I checked lib/firmware and sure enough there was no Apple USB Video folder or file...

Should I redo the steps prior to that last one?

Any help would be greatly appreciated

---

### Post by cyberdork33 on 2008-07-31
> **jarhead14 said:**
> I checked lib/firmware and sure enough there was no Apple USB Video folder or file...


Just before that part:
> **benanzo said:**
> Go ahead and put the iSight firmware (AppleUSBVideoSupport) in /lib/firmware

This file is found on your OSX partition as it is part of OSX.

---

### Post by jarhead14 on 2008-07-31
Oh no.  So the step before when it asked me where to put the firmware file I should not have typed in /lib/firmware?

Is that going to effect its operation?

---

### Post by cyberdork33 on 2008-07-31
> **jarhead14 said:**
> Oh no.  So the step before when it asked me where to put the firmware file I should not have typed in /lib/firmware?

Is that going to effect its operation?
I am confused by what you are asking.


I think when you install IFT it asks you where the firmware file is located. Since you have not moved the AppleUSBVideoSupport file into /lib/firmware yet, then it cannot load the firmware. copy the file into /lib/firmware then continue with the ift-extract command. You are doing the same thing that the application is trying to do, just manually.

PS as an update for all, IFT has been added to the Intrepid repo. This means that you will not need the mactel-support ppa for this software when it is released. Please test the package to make sure it works OK for you:
[http://packages.ubuntu.com/intrepid/isight-firmware-tools](http://packages.ubuntu.com/intrepid/isight-firmware-tools)

---

### Post by Epamek on 2008-08-02
Running into a small problem.

I've pulled AppleUSBVideoSupport from OSX onto my desktop, but when I try to drag into the firmware folder it denies me permission.  On a possibly related note, I have three folders in lib/firmware, 2.6.24-16-generic, -19-generic, and -20 generic.  they're all (as far as I can tell) identical copies of one another, but I do not have the permission to delete any of them. Aside from the identical .bins and .fws, I have no files in lib/firmware at all.

---

### Post by cyberdork33 on 2008-08-03
> **Epamek said:**
> Running into a small problem.

I've pulled AppleUSBVideoSupport from OSX onto my desktop, but when I try to drag into the firmware folder it denies me permission.  On a possibly related note, I have three folders in lib/firmware, 2.6.24-16-generic, -19-generic, and -20 generic.  they're all (as far as I can tell) identical copies of one another, but I do not have the permission to delete any of them. Aside from the identical .bins and .fws, I have no files in lib/firmware at all.
don't worry about what is in there already...

You have to use sudo to copy the file
```
_sudo_ cp AppleUSBVideoSupport /lib/firmware/
```

---

### Post by mathtick on 2008-08-13
I have tried the instructions here and a number of other places but have had no luck so far:

Simple tests 

$ sudo modprobe -r uvcvideo
FATAL: Module uvcvideo not found.
$ sudo modprobe uvcvideo
FATAL: Module uvcvideo not found.

... anybody have ideas of what to try next?  I'm not quite sure how to diagnose the problem either. I think I'm on a first generation macbook (or what ever is listed as 'late 2006 macbook' on the mac site).

I seem to give up on this and then get motivated and retry every few weeks but I seem to be no longer finding new things to try.

---

### Post by mathtick on 2008-08-13
...some additional information which I think may be relavent:

> $ sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport 
** Message: Found Mac OS X.4 intel driver
** Message: Firmware extracted successfully in /lib/firmware/isight.fw
** Message: Apply patch 0 : Fix video control interface descriptor
** Message: Apply patch 1 : Fix video streaming interface descriptor
** Message: Apply patch 2 : Fix video streaming device qualifier
** Message: Firmware patched successfully

$ modprobe -l *vid*
/lib/modules/2.6.24-19-generic/volatile/nvidia.ko
/lib/modules/2.6.24-19-generic/volatile/nvidia_legacy.ko
/lib/modules/2.6.24-19-generic/volatile/nvidia_new.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/char/agp/nvidia-agp.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/acpi/video.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/hwmon/hwmon-vid.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/video1394.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/media/video/usbvideo/usbvideo.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/media/video/videobuf-vmalloc.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/media/video/videobuf-dvb.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/media/video/videocodec.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/media/video/videobuf-dma-sg.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/media/video/videodev.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/media/video/videobuf-core.ko

Am I just missing the uvcvideo driver?  or am *I* completely missing something?

---

### Post by mathtick on 2008-08-14
I have just notice that there is a uvcvideo.ko file in the following location
> /lib/modules/2.6.24-19-generic/ubuntu/media/usbvideo$ ls
uvcvideo.ko.orig


I have downloaded source and compiled a uvcvideo.ko file myself but am not quite sure where to put it.  The fact that there is a uvcvideo  with the lib/modules directory makes me think there is something wrong with modprobe.

---

### Post by cyberdork33 on 2008-08-14
> **mathtick said:**
> ... anybody have ideas of what to try next?  I'm not quite sure how to diagnose the problem either. I think I'm on a first generation macbook (or what ever is listed as 'late 2006 macbook' on the mac site).
See the "Before you post" link in my signature to determine your hardware version.

> **mathtick said:**
> I have downloaded source and compiled a uvcvideo.ko file myself but am not quite sure where to put it.  The fact that there is a uvcvideo  with the lib/modules directory makes me think there is something wrong with modprobe.

If you download the source, and do a 'make', 'sudo make install', then it will placed in the correct location itself.

Can you give the output of:
```
lsmod |grep uvcvideo
```and
```
dmesg |grep uvcvideo
```EDIT: Actually, I see in your output from before that there is a file...
```
/lib/modules/2.6.24-19-generic/kernel/drivers/media/video/usbvideo/usbvideo.ko
```
I am not sure how that came to be as it should be
```
/lib/modules/2.6.24-19-generic/kernel/drivers/media/video/usbvideo/uvcvideo.ko
```

---

### Post by blznazn on 2008-08-19
Thanks, I followed all the steps and it works perfect now.

---

### Post by hloupy on 2008-09-02
Hiya I'm stuck at an annoying point.. I want to follow this instruction:
[I]
Go ahead and put the iSight firmware (AppleUSBVideoSupport) in /lib/firmware[/I]

but I cant move the firmware because i dont have the permissions.

So then i was trying to do it using *sudo nano /lib/firmware* then the command *ctrl R*, but im got a bit confused with what comes up on screen, so i cancelled.

Im a newbie using Hardy on a Macbook 4.1. Thanks for any help!

---

### Post by flaggh on 2008-09-02
/lib/firmware is a directory, not a text file.  You should copy the firmware file from you OSX drive into the directory /lib/firmware/.  I forget what the firmware location is offhand, but the command would be:

```
sudo cp /path/to/firmware/file /lib/firmware/
```

---

### Post by hloupy on 2008-09-03
> **flaggh said:**
> /lib/firmware is a directory, not a text file.  You should copy the firmware file from you OSX drive into the directory /lib/firmware/.  I forget what the firmware location is offhand, but the command would be:

```
sudo cp /path/to/firmware/file /lib/firmware/
```


thanks for that, it's appreciated, now i can go further with trying to configure the isight. im finding the howto helpful, but hard to follow, so i will post back here what i did to help other newbies.
cheers!

---

### Post by cyberdork33 on 2008-09-03
> **hloupy said:**
> thanks for that, it's appreciated, now i can go further with trying to configure the isight. im finding the howto helpful, but hard to follow, so i will post back here what i did to help other newbies.
cheers!
It may not be worth it. This entire thing is about to change again in Ubuntu 8.10.

---

### Post by sneilan on 2008-09-15
My camera is working with Ekiga & Cheese, but, it crashes Firefox when I use the web camera feature in Adobe Flash 10 rc.

My output from $ lsmod | grep uvcvideo is
```
sneilan@sneilan-laptop:/usr/lib$ lsmod | grep uvcvideo
uvcvideo               59656  1
compat_ioctl32          2304  1 uvcvideo
videodev               29440  2 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
usbcore               146028  9 uvcvideo,ndiswrapper,hci_usb,usbhid,appleir,appletouch,ehci_hcd,uhci_hcd

```
My output from $ sudo modprobe uvcvideo
[ 2233.461235] uvcvideo: Found UVC 1.00 device Built-in iSight ```
(05ac:8501)
[ 2233.463641] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[ 2233.465654] input: Built-in iSight as /devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/input/input23
[ 2233.492064] usbcore: registered new interface driver uvcvideo
[ 2233.492075] USB Video Class driver (SVN r246)
```

My output of $ lsusb is:
```
Bus 005 Device 007: ID 05ac:8501 Apple Computer, Inc. Built-in iSight [Micron]
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 005: ID 05ac:1000 Apple Computer, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 003: ID 05ac:8240 Apple Computer, Inc. IR Receiver [build-in]
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 05ac:021a Apple Computer, Inc.
Bus 001 Device 001: ID 0000:0000

```

I properly loaded my apple isight driver from my osx partition & I used the ubuntu isight driver package thing in the ppa repositories. Everything appeared to work.

When I go to a site like [http://en.barcodepedia.com/](http://en.barcodepedia.com/) & I allow usage of my web camera in a flash thingy, either my firefox crashes with a segmentation fault or I see all these weird colors where the video would be displaying.

I'm running 8.04 i386 on a Core 2 Duo 3rd Generation Macbook.

---

### Post by cyberdork33 on 2008-09-15
> **sneilan said:**
> My camera is working with Ekiga & Cheese, but, it crashes Firefox when I use the web camera feature in Adobe Flash 10 rc.
I would file a bug on this. Since it is working on the system in general, it is likely a bug in firefox or flash player for linux.

---

### Post by sneilan on 2008-09-15
> **cyberdork33 said:**
> I would file a bug on this. Since it is working on the system in general, it is likely a bug in firefox or flash player for linux.

Alright. That sounds like a plan. Thank you very much for your reply!

---

### Post by sharelove on 2008-09-25
HI,
I've tried to get my webcam to work for days...I've followed many many tutorials and no success. HOWEVER, your tutorial worked perfect!!! Thanks soo sooo much!!! A question: what is 205? Thanks again for a well written command and it works!

---

### Post by sharelove on 2008-09-25
> **Derviansoul said:**
> hello

just done your tutorial with hardy x64 and works great with ekiga not with cheese, i dunno if it's being posted or not,but i just had to do:


CODE]
$ sudo apt-get update
$ sudo apt-get install isight-firmware-tools
[/CODE]

Go ahead and put the iSight firmware (AppleUSBVideoSupport) in /lib/firmware

and restart hal
```
/etc/init.d/hal restart
```

great works 
regards

Hi, your tutorial is the best! I added a response meant for you with this posting as it worked!!! Checkout the reply later on in this thread - it's for you. Thanks again!!

---

### Post by rickbsgu on 2008-10-01
I did this on an AMD-64 install of 8.04.  Had to do that last re-compile bit and reboot the system and then it came up fine.

I suspect it won't survive a kernel update, so I'll have to put together a script to do the last bits over, I suppose.

Be nice when this gets fixed in the mainstream distro.

thanx,
rickb

---

### Post by cyberdork33 on 2008-10-01
> **rickbsgu said:**
> I did this on an AMD-64 install of 8.04.  Had to do that last re-compile bit and reboot the system and then it came up fine.

I suspect it won't survive a kernel update, so I'll have to put together a script to do the last bits over, I suppose.

Be nice when this gets fixed in the mainstream distro.

thanx,
rickb
In Intrepid, you just have to place the isight.fw file in /lib/firmware everything else is in the kernel and works fine.

---

### Post by Heds on 2008-10-12
Sorry, I got stuck at this part:

"Go ahead and put the iSight firmware (AppleUSBVideoSupport) in /lib/firmware".

What EXACTLY am I supposed to do. I'm a newbie as far as how deep I've delved into Linux. I'm currently running ONLY Linux Mint5 on my MacBook, so any and all very specific help I can get I would greatly appreciate, thanks.

---

### Post by cyberdork33 on 2008-10-12
> **Heds said:**
> Sorry, I got stuck at this part:

"Go ahead and put the iSight firmware (AppleUSBVideoSupport) in /lib/firmware".

What EXACTLY am I supposed to do. I'm a newbie as far as how deep I've delved into Linux. I'm currently running ONLY Linux Mint5 on my MacBook, so any and all very specific help I can get I would greatly appreciate, thanks.
You have to get a file from your OSX install that has the iSight firmware in it. It is located in 
/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport

---

### Post by kbgabt on 2008-10-20
Hey guys.. well, this is a question that has to do a lot with this, so here it goes.
Is there a way to make the image of the webcam a little better (in pixel quality, i mean)? Because, if i'm not wrong, the image it gives under MacOS is a lot better.

---

### Post by sheybklyn on 2008-10-27
Man, I have been looking for DAYS how to get this webcam working and finally this howto worked seamlessly.

A tip though, if it does not work after the complete install, do the firmware extraction again. Cheese works flawlessly. Ill try Gyachi later for yahoo webcamming, I dont use Ekiga soooo I dunno..

MANY MANY MANY thanks to the how-to scriber.

Good lookin out troop.

---

### Post by Cifra on 2008-10-28
> **cyberdork33 said:**
> You have to get a file from your OSX install that has the iSight firmware in it. It is located in 
/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport

Well, I installed the firware package from synaptic (I'm using Intrepid).

And because nothing happened after reboot, I went on with the instructions here

[http://ubuntuforums.org/showthread.php?t=958326#3](http://ubuntuforums.org/showthread.php?t=958326#3)

and pasted this command
```
ift-extract -a /media/Macintosh\ HD/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport
```


output:

```
Unable to read driver /media/Macintosh HD/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport
```

And this is the error that I get. I already saw that other people got this error, but I don't get how the workaround works. SO, what should I do next?

---

### Post by cyberdork33 on 2008-10-28
> **Cifra said:**
> Well, I installed the firware package from synaptic (I'm using Intrepid).I don't know what you mean by this. What "firmware package"?

> **Cifra said:**
> and pasted this command
```
ift-extract -a /media/Macintosh\ HD/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport
```
output:

```
Unable to read driver /media/Macintosh HD/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport
```And this is the error that I get. I already saw that other people got this error, but I don't get how the workaround works. SO, what should I do next?

That just looks like a problem with permissions on that file. You can just boot into OSX, copy the file to a thumb drive, and copy onto your Ubuntu install if it is easier. I wrote a short post on iSight in Intrepid on my blog here:
[http://www.rickycampbell.com/isight-intrepid/](http://www.rickycampbell.com/isight-intrepid/)

---

### Post by moviemaniac on 2008-11-03
As my integrated iSight-camera works in Skype [on Intrepid 32bit] but fails in all other applications (Cheese, VLC...) I just tried to install the driver (iMac 8,1). 

It fails at this step: 

```
root@klaus-imac:/home/klaus# sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport

** (ift-extract:9169): WARNING **: Unknown driver. Please report it to https://bugs.launchpad.net/isight-firmware-tools/+filebug with machine description and Mac OS X version.

** ERROR **: Unable to find firmware in the file.
aborting...
Aborted

```


a bugreport has already been filed: [https://bugs.launchpad.net/isight-firmware-tools/+bug/292935](https://bugs.launchpad.net/isight-firmware-tools/+bug/292935)

---

### Post by kk555555 on 2008-11-03
welcome to our website: [www.cheap-nikejordan.com](www.cheap-nikejordan.com) ,We hope become your reliable shoes supplier in China. Authentic Shoes with original box,we insists that " Customer the highest, Quality first ". Our products include Air Jordan series,Mix jordan series, Air max Shoes series, Air force one, Nike shox series shoes, Adidas Shoes, Timberland Shoes, Prada Shoes,Gucci shoes,puma shoes,lv bags, and Bape, Lacoste,Polo T-shirt,Evisu hoody,Evisu coat etc. we are looking forward to building sincere and long-term business relationships with you.

---

### Post by cyberdork33 on 2008-11-03
> **moviemaniac said:**
> As my integrated iSight-camera works in Skype [on Intrepid 32bit] but fails in all other applications (Cheese, VLC...) I just tried to install the driver (iMac 8,1). 

It fails at this step: 

```
root@klaus-imac:/home/klaus# sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport

** (ift-extract:9169): WARNING **: Unknown driver. Please report it to https://bugs.launchpad.net/isight-firmware-tools/+filebug with machine description and Mac OS X version.

** ERROR **: Unable to find firmware in the file.
aborting...
Aborted

```
a bugreport has already been filed: [https://bugs.launchpad.net/isight-firmware-tools/+bug/292935](https://bugs.launchpad.net/isight-firmware-tools/+bug/292935)
Interesting. 

but your camera works in Skype? Very strange.

You might try to find some older AppleUSBVideoSupport file floating around on the net and see if it works.

---

### Post by moviemaniac on 2008-11-03
Yes. The first application I tried was Skype and I was happy. Then I wanted to use Cheese today but I don't get any image. When trying to change the resolution, Cheese freezes. The camera also doesn't work with VLC, Cinelerra and one other application I don't remember right now. So I assumed there was a problem with the driver and wanted to install it acording to the howto.

I think I'll go looking for an older AppleUSB.... file now, thanks!

---

### Post by cyberdork33 on 2008-11-03
> **moviemaniac said:**
> Yes. The first application I tried was Skype and I was happy. Then I wanted to use Cheese today but I don't get any image. When trying to change the resolution, Cheese freezes. The camera also doesn't work with VLC, Cinelerra and one other application I don't remember right now. So I assumed there was a problem with the driver and wanted to install it acording to the howto.

I think I'll go looking for an older AppleUSB.... file now, thanks!


If you run 'gstreamer-properties' it will open a window where you can configure and test the video source. That may yield helpful information as well.

---

### Post by moviemaniac on 2008-11-03
Well, I'll be damned - everything works with that gstreamer-thingy, but applications still don't want to work. VLC says "v4l2 error: cannot open video device (Not a directory)"

---

### Post by cyberdork33 on 2008-11-03
> **moviemaniac said:**
> Well, I'll be damned - everything works with that gstreamer-thingy, but applications still don't want to work. VLC says "v4l2 error: cannot open video device (Not a directory)"
hmm... I'd guess it was a bug with gstreamer or with the particular applications you are trying.

---

### Post by moviemaniac on 2008-11-03
I just searched in launchpad after trying a usb-microscope I had lying around that didn't work too (but worked in the gstreamer-thingy) and found this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290506](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290506)

It seems that using Cheese breaks the output for other applications (but not for Skype which might be due to Skype not using Gstreamer? ;) )

Oh, and then there's a problem concerning uvcvideo which might explain why so many applications fail: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287888/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287888/)

I guess I'll just have to wait (and until then use my old laptop when I want to use my USB-microscope...)

I sure have encountered more bugs in Intrepid during the last week than during the last six months with hardy :D

---

### Post by cyberdork33 on 2008-11-03
> **moviemaniac said:**
> I just searched in launchpad after trying an usb-microscope I had lying around that didn't work too (but worked in the gstreamer-thingy) and found this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290506](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290506)

It seems that using Cheese breaks the output for other applications (but not for Skype which might be due to Skype not using Gstreamer? ;) )

Oh, and then there's a problem concerning uvcvideo which might explain why so many applications fail: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287888/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287888/)

I guess I'll just have to wait (and until then use my old laptop when I want to use my USB-microscope...)

I sure have encountered more bugs in Intrepid during the last week than during the last six months with hardy :D
Good finds. Hopefully this will be fixed soon.

PS Ekiga also does not use gstreamer ;)

---

### Post by moviemaniac on 2008-11-03
Yup, Ekiga should work, too. The thing is that I mainly need a program that allows me to capture single frames when using my USB microscope. Cheese is perfect for that purpose, VLC works, too. I'm hoping for a quick fix here, but it's good to know that I don't have to pursue not being able to install the driver for the iSight cam :D

---

### Post by cyberdork33 on 2008-11-03
> **moviemaniac said:**
> Yup, Ekiga should work, too. The thing is that I mainly need a program that allows me to capture single frames when using my USB microscope. Cheese is perfect for that purpose, VLC works, too. I'm hoping for a quick fix here, but it's good to know that I don't have to pursue not being able to install the driver for the iSight cam :D
If nothing else you can do a screen capture :)

---

### Post by calebio on 2008-11-08
> **cyberdork33 said:**
> In Intrepid, you just have to place the isight.fw file in /lib/firmware everything else is in the kernel and works fine.

I followed the instructions in this thread to install **/lib/firmware/isight.fw**, restarted HAL, and then ran gstreamer-properties. But when I click to test Video Default Input (V4L2), I see the following on the command line:

```
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(463): gst_v4l2_open (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src3:

```
This is on an iMac6,1

EDIT: Video now works after a shutdown and reboot. Magic....

---

### Post by cyberdork33 on 2008-11-08
> **calebio said:**
> EDIT: Video now works after a shutdown and reboot. Magic....
Yep, that is key... Weird, I know, but it has to be done.

---

### Post by rakan21 on 2009-02-17
Thank you so much it worked like a charm. Of course I was able to uninstall it without having OS X installed. I'm 100% ubuntu I had to get the AppleUSBVideoSupport off my moms OS X. 

;)

---

