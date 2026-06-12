---
title: "HOW-TO: iSight setup"
date: 2007-07-03
forum: Apple Intel Users
---

### Post by ivesjd on 2007-07-03
**_*[CENTER][COLOR="Green"][SIZE="4"]Should be working now (11/10/2007) [/SIZE][/COLOR][/CENTER]*_**  


**_[CENTER][COLOR="Red"][SIZE="6"]Quick and easy iSight setup[/SIZE][/COLOR][/CENTER]_**

As of 10/27/2007 on Gutsy. Thanks to cyberdork33 for the fixes to get this working.


In this how-to, there is no need to mount your OS X partition.
```
sudo modprobe -r uvcvideo
sudo mv /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko.original
```

* Install prerequisites, libusb-dev, you might need kernel headers that match your kernel 
```
sudo apt-get install libusb-0.1-4 libusb-dev linux-headers-$(uname -r)

```

* Download the new all-in-one bundle, with firmware autoloader as provided by Ivan N. Zlatev by clicking  [_*here*_]("http://files.i-nz.net/projects/linux-kernel/isight/uvcvideo-isight.tar.gz") .
*Change directories to where the tar file is. Then untar it.
```
 tar -xvf uvcvideo-isight.tar.gz 
```

* Now build and Install the uvcvideo module
```
cd against-revision-140
sudo make
sudo make install
```

* Load the module
```
sudo modprobe uvcvideo
```

Now it should work. Here is a test you can run to see it in action.

GSTREAMER TEST
```
gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=640,height=480 ! ffmpegcolorspace ! ximagesink
```

---

### Post by cyberdork33 on 2007-07-03
There is a bug with newer kernels and the uvcvideo module. Upgrading will likely break it.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105638](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105638)

---

### Post by david_edmundson on 2007-07-03
If you are a kubuntu user you will need to install gstreamer to run the final command.
I installed gstreamer0.10*, though it's probably possible to do it with a bit less.

Another problem I encountered was when I mounted it, dmesg said the following

```

[28959.720000] Linux video capture interface: v2.00
[28959.828000] uvcvideo: iSight: firmware successfully loaded.
[28959.828000] uvcvideo: Found UVC 0.00 device <unnamed> (05ac:8300)
[28959.828000] uvcvideo: No valid video chain found.
[28959.828000] usbcore: registered new interface driver uvcvideo
[28959.828000] USB Video Class driver (v0.1.0)

```

This can be fixed by running
```

modprobe uvcvideo trace=15

```

If that fix works, add it to your module options.

---

### Post by cyberdork33 on 2007-07-03
you need at least gstreamer0.10 to use cheese too if you want that.

---

### Post by ramvi on 2007-07-27
**Heya!**

Thanks for what seems to be a great howto!
I've got a problem tough.

The dmesg says this when I modprobe uvcvideo:
```
[  782.604000] Linux video capture interface: v2.00
[  782.608000] usbcore: registered new interface driver uvcvideo
[  782.608000] USB Video Class driver (v0.1.0)
```

When I run the test I get this:
```
ramvi@ramvi:~$ gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=640,height=480 ! ffmpegcolorspace ! ximagesink
Setting pipeline to PAUSED ...
ERROR: Pipeline doesn't want to pause.
FEIL: fra element /pipeline0/v4l2src0: Cannot identify device '/dev/video0'.
Tilleggsinformasjon for feilsøking:
v4l2_calls.c(404): gst_v4l2_open (): /pipeline0/v4l2src0:
system error: No such file or directory
Setting pipeline to NULL ...
FREEING pipeline ...
```

---

### Post by cyberdork33 on 2007-07-27
> **ramvi said:**
> **Heya!**

Thanks for what seems to be a great howto!
I've got a problem tough.

The dmesg says this when I modprobe uvcvideo:
```
[  782.604000] Linux video capture interface: v2.00
[  782.608000] usbcore: registered new interface driver uvcvideo
[  782.608000] USB Video Class driver (v0.1.0)
```When I run the test I get this:
```
ramvi@ramvi:~$ gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=640,height=480 ! ffmpegcolorspace ! ximagesink
Setting pipeline to PAUSED ...
ERROR: Pipeline doesn't want to pause.
FEIL: fra element /pipeline0/v4l2src0: Cannot identify device '/dev/video0'.
Tilleggsinformasjon for feilsøking:
v4l2_calls.c(404): gst_v4l2_open (): /pipeline0/v4l2src0:
system error: No such file or directory
Setting pipeline to NULL ...
FREEING pipeline ...
```

Try rebooting. The correct module should load this time, then try the test again. It looks like one of the many errors I've gotten before try to get this to work right. I don't really have a solutiion because I just kinda fiddle with it until it starts working.

---

### Post by ramvi on 2007-07-30
I have tried that - same error :(

---

### Post by cyberdork33 on 2007-07-30
> **ramvi said:**
> I have tried that - same error :(
I am getting the same error in gutsy now.

---

### Post by ramvi on 2007-08-01
Gutsy here as well

---

### Post by cyberdork33 on 2007-08-01
did you try with that recent kernel update? I was hoping that might fix it.

EDIT: answering my own question here... It still does not work.

I found the bug report on this. It appears to have started with a kernel update in feisty.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105638](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105638)

---

### Post by cyberdork33 on 2007-08-22
an update. There is new working being done on the patch to get the uvcvideo module to work in the newer kernels.

[https://lists.berlios.de/pipermail/linux-uvc-devel/2007-August/002027.html](https://lists.berlios.de/pipermail/linux-uvc-devel/2007-August/002027.html)

---

### Post by maluka on 2007-08-26
thank you. this tutorial helped me a lot. i have also gone on to intall cheese and it's great! is there any software for video chat with ubuntu?

---

### Post by cyberdork33 on 2007-08-27
> **maluka said:**
> thank you. this tutorial helped me a lot. i have also gone on to intall cheese and it's great! is there any software for video chat with ubuntu?
ekiga is a softphone

---

### Post by maluka on 2007-08-28
thanks! i will give it a go.

---

### Post by Azathoth_ on 2007-08-29
Anyone can use it in gstreamer??

---

### Post by gnrfan713 on 2007-09-04
im a new linux user could someone be more specific on the whole "change tar derectory, untar thing, i have know idea what to do
                                   thanks

---

### Post by cyberdork33 on 2007-09-04
> **gnrfan713 said:**
> im a new linux user could someone be more specific on the whole "change tar derectory, untar thing, i have know idea what to do
                                   thanks

He literally means to navigate to the directory where you downloaded the tar file in the terminal. Use 'cd *directoryname*' to change your current directory, and 'ls' to list the directories and files in the current folder.

For instance, if I am in my home directory: /home/cyberdork33 and I downloaded the tar file to my desktop, I would use the command```
cd Desktop
``` to move into the 'Desktop' folder. Then to check, I can use 'ls' to list the files in the desktop and make sure I am in the right place.

The next command in the how to untars the package:```

 tar -xvf uvcvideo-isight.tar.gz
```

If you are new to linux, I might suggest checking out this site. [http://linuxcommand.org](http://linuxcommand.org) It will explain some of the basics of the terminal.

---

### Post by ivesjd on 2007-09-04
I'm glad your ontop of things cyberdork. I just dont have the time I used to on here, with class and my new baby. (Actually a baby girl, not just "my baby") :D

---

### Post by gnrfan713 on 2007-09-04
much thanks to cyberdork33
it so great to have people actualy help you :)

---

### Post by gnrfan713 on 2007-09-04
ok i still did something wrong
could someone maby tell me exactly what to type into the terminal

when i typed cd desktop it said "no such derectory"  and it said the same with a bunch of other commands

i feel sorta stupid havinng to ask this but any help would be great

---

### Post by cyberdork33 on 2007-09-04
> **ivesjd said:**
> I'm glad your ontop of things cyberdork. I just dont have the time I used to on here, with class and my new baby. (Actually a baby girl, not just "my baby") :DCongrats.

---

### Post by cyberdork33 on 2007-09-04
> **gnrfan713 said:**
> ok i still did something wrong
could someone maby tell me exactly what to type into the terminal

when i typed cd desktop it said "no such derectory"  and it said the same with a bunch of other commands

i feel sorta stupid havinng to ask this but any help would be great
Linux is case sensitive ;) Desktop vs desktop
I can't really give you really specific directions because I do not know where you download files

---

### Post by gnrfan713 on 2007-09-04
i downloaded them to the desktop

---

### Post by gnrfan713 on 2007-09-04
i dont know if this makes a difference but also, i am using kubuntu

---

### Post by cyberdork33 on 2007-09-05
> **gnrfan713 said:**
> i dont know if this makes a difference but also, i am using kubuntu

Ok so open a terminal. It should by default open to your home directory. You can always use the 'cd' command by itself to take you to your home folder.

Your Desktop directory is in your home folder. To navigate to the Desktop folder, you issue the command:```
cd Desktop
```The letter case is important. After you are in the Desktop directory, you can type 'ls' (that is an L not an I) to have all the files in your current directory displayed. You should see the downloaded file. You can then proceed with the how to by using the tar command to extract the files.```
tar -xvf uvcvideo-isight.tar.gz
``` In this command you use the tar utility. the '-xvf' section are flags that tell the utility what you want to do. x means that you want to extract, v is verbose to get lots of output, and the f means you want to input the following file. 
Then you follow the rest of the how to. It should not make a difference that you are using kubuntu except that you probably do not have the gstreamer stuff installed since it is a gnome thing. I hope this helps.

---

### Post by Levo75 on 2007-10-15
Allright it worked to the part where you open a little window with the image from the webcam. But i need it to be recognisable by other programs and apps.

I remember it had to have a path like /dev/vid0 or something.

Can someone enlighten me on this?

---

### Post by cyberdork33 on 2007-10-15
> **Levo75 said:**
> Allright it worked to the part where you open a little window with the image from the webcam. But i need it to be recognisable by other programs and apps.

I remember it had to have a path like /dev/vid0 or something.

Can someone enlighten me on this?
Unsure what you mean. If the gstreamer test works, then it is "available" to other applications. What are you trying to use it with? Are you on Feisty or Gutsy?

---

### Post by ivesjd on 2007-10-19
> **cyberdork33 said:**
> Unsure what you mean. If the gstreamer test works, then it is "available" to other applications. What are you trying to use it with? Are you on Feisty or Gutsy?

I'm guessing hes on Fiesty since the guide hasn't been updated to work on gutsy yet. Still havent had the time to mess with it. Maybe this weekend. Maybe.

---

### Post by cyberdork33 on 2007-10-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105638](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105638) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				> **ivesjd said:**
> I'm guessing hes on Fiesty since the guide hasn't been updated to work on gutsy yet. Still havent had the time to mess with it. Maybe this weekend. Maybe.
It works by default in gutsy. you just can't use 640x480 resolution on it for some reason. See bug report.

---

### Post by MichaëlVD on 2007-10-19
I'm confident that the resolution problem and the gstreamer problem will be solved one day... but what about the fact that I can't record sound? Does that work for anyone? Or is there a bug report on Launchpad? I can't seem to find it...

---

### Post by cyberdork33 on 2007-10-19
> **MichaëlVD said:**
> I'm confident that the resolution problem and the gstreamer problem will be solved one day... but what about the fact that I can't record sound? Does that work for anyone? Or is there a bug report on Launchpad? I can't seem to find it...
You might want to check in a sound thread on that one. This one is for iSight.

---

### Post by cyberdork33 on 2007-10-27
Ok try it with my changes:

```
sudo modprobe -r uvcvideo
sudo mv /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko.original
```* Install prerequisites, libusb-dev, you might need kernel headers that match your kernel 
 
```
sudo apt-get install libusb-0.1-4 libusb-dev linux-headers-$(uname -r)
```* Download the new all-in-one bundle, with firmware autoloader as provided by Ivan N. Zlatev by clicking  [_*here*_]("http://files.i-nz.net/projects/linux-kernel/isight/uvcvideo-isight.tar.gz") .
*Change directories to where the tar file is. Then untar it.
```
tar -xvf uvcvideo-isight.tar.gz
```* Now build and Install the uvcvideo module
```
cd against-revision-100
sudo make
sudo make install
```* Load the module

```
sudo modprobe uvcvideo
```Now it should work. Here is a test you can run to see it in action.

GSTREAMER TEST

```
gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=352,height=288 ! ffmpegcolorspace ! ximagesink
```Note: A bug in gstreamer prevents this from working at the full resolution of 640x480. Hopefully fixes are on the way.

---

### Post by ivesjd on 2007-10-27
Awesome, its working, hopefully we can get a resolution resolution.:lolflag: 
I'll update the how-to now.

---

### Post by madscientist032 on 2007-10-27
I have my iSight working, but it only works with Ekiga. Cheesy and Canorama camera viewer are unable to connect to my iSight.

---

### Post by bennyp on 2007-10-27
Works with Ekiga on my Macbook. Haven't tried any other apps yet. Cheers.

---

### Post by FunkyM on 2007-10-27
> **cyberdork33 said:**
> Note: A bug in gstreamer prevents this from working at the full resolution of 640x480. Hopefully fixes are on the way.

That is really annoying since Cheese for instance does not allow setting the lower format. Thus it attempts to use v4l2src with 640x480 and freezes. This is a regression since it worked a while ago. Do you have any information and perhaps a bug link regarding the issue?

---

### Post by cyberdork33 on 2007-10-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105638](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105638) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				> **FunkyM said:**
> That is really annoying since Cheese for instance does not allow setting the lower format. Thus it attempts to use v4l2src with 640x480 and freezes. This is a regression since it worked a while ago. Do you have any information and perhaps a bug link regarding the issue?
Of course.

It is not regression since it did not work at all with feisty... well not without compiling the patched module.

I compiled gstreamer, gst-plugins-base, and gst-plugins-good from cvs today, and that didn't help anything.

---

### Post by Levo75 on 2007-10-28
> **cyberdork33 said:**
> Unsure what you mean. If the gstreamer test works, then it is "available" to other applications. What are you trying to use it with? Are you on Feisty or Gutsy?

I'm running gutsy, and it's working with gstreamer now. thnx

But other programs exept Ekiga arent working. :(

I get this message: Could not connect to video device (/dev/video0).

Please check connection.

---

### Post by cyberdork33 on 2007-10-30
> **Levo75 said:**
> I'm running gutsy, and it's working with gstreamer now. thnx

But other programs exept Ekiga arent working. :(

I get this message: Could not connect to video device (/dev/video0).

Please check connection.
so ekiga works? and the gstreamer test works?

---

### Post by Zaff on 2007-10-30
I got the same issue, but yes it works with gstreamer and kopete for me. I haven't tried ekiga but I'm guessing it'll work too. it would be really cool if I could get it to work with cheese or camorama now...

---

### Post by cyberdork33 on 2007-10-30
> **Zaff said:**
> I got the same issue, but yes it works with gstreamer and kopete for me. I haven't tried ekiga but I'm guessing it'll work too. it would be really cool if I could get it to work with cheese or camorama now...
I asked the developer of cheese about this, and he said to just wait for updates to gstreamer.

---

### Post by cyberdork33 on 2007-11-01
Well, this is interesting. 

I just tried the 640x480 test command in 32bit Ubuntu Gutsy in VMWare Fusion, and it worked fine (after modprobing uvcvideo). Nothing else was needed, not even the recompile. Just modprobe uvcvideo, and go.

Maybe this is a result of being the VM, but it was my understanding that the USB devices are seen natively by the VM.

---

### Post by cyberdork33 on 2007-11-01
Ok, You completely do not need to compile anything for Gutsy. The modified module is included with gutsy and is called isight_usb rather than uvcvideo. The uvcvideo module exists as well, but I think it is unpatched, and is there for other uvc devices. The resolution bug still exists though.

[https://bugs.launchpad.net/ubuntu/+source/restricted-manager/+bug/144359](https://bugs.launchpad.net/ubuntu/+source/restricted-manager/+bug/144359)

```
cyberdork33@Grover-Ubuntu:~$ lsmod | grep videodev
videodev               31360  1 isight_usb
v4l1_compat            15364  2 isight_usb,videodev
v4l2_common            21888  3 isight_usb,compat_ioctl32,videodev
```

---

### Post by cyberdork33 on 2007-11-01
ok last post on this for awhile. This is really just for techinical information. 

It seems that the isight_usb module that is in the linux-ubuntu-modules-2.6.22-14 package checks that your idVendor is 05ac (Apple) and the idProduct is 8501, and it skips loading firmware. I don't quite understand why, but I guess only certain iSights need the Apple firmware in place (idProduct 8300 ?)

---

### Post by Levo75 on 2007-11-02
> **Zaff said:**
> I got the same issue, but yes it works with gstreamer and kopete for me. I haven't tried ekiga but I'm guessing it'll work too. it would be really cool if I could get it to work with cheese or camorama now...

Same here.

---

### Post by jslmg on 2007-11-08
Thanks for all the thorough work everyone. I see some very helpful voices in this thread. 

I followed the instructions given by ivesjd and Cyberdork, and all looked great until the test. I got a message similar to the one ramvi got. However, ramvi had an output from the modprobe, which I did not. Here's my terminal output, from modprobe through test:

jslmg@Ubuntu:~/Desktop/against-revision-140$ sudo modprobe uvcvideo
jslmg@Ubuntu:~/Desktop/against-revision-140$ gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=352,height=288 ! ffmpegcolorspace ! ximagesink
Setting pipeline to PAUSED ...
ERROR: Pipeline doesn't want to pause.
ERROR: from element /pipeline0/v4l2src0: Cannot identify device '/dev/video0'.
Additional debug info:
v4l2_calls.c(424): gst_v4l2_open (): /pipeline0/v4l2src0:
system error: No such file or directory
Setting pipeline to NULL ...
FREEING pipeline ...
jslmg@Ubuntu:~/Desktop/against-revision-140$ 

Some notes: My iSight is a Firewire model, not USB. Does that make a difference here? I thought all iSights were firewire.:confused:

Would rebooting help in this, or am I missing something else, given that I have no modprobe output?

I'll try a reboot and rerun the test, let everyone know what happens...

---

### Post by jslmg on 2007-11-08
Reboot did not help. Same terminal output as before. Any one else trying this on a Mac mini? My Linux kernel, btw, is 2.6.22-14-generic.

---

### Post by Levo75 on 2007-11-08
levent@levent-desktop:~/Desktop$  tar -xvf uvcvideo-isight.tar.gz
against-revision-140/patch/isight.patch
against-revision-140/patch/patch-README
against-revision-140/src/Makefile
against-revision-140/src/isight.c
against-revision-140/src/uvc_v4l2.c
against-revision-140/src/uvc_queue.c
against-revision-140/src/uvc_compat.h
against-revision-140/src/uvc_driver.c
against-revision-140/src/uvcvideo.h
against-revision-140/src/uvc_ctrl.c
against-revision-140/src/dynctrl.txt
against-revision-140/src/uvc_video.c
against-revision-140/src/isight.h
against-revision-140/firmware/AppleUSBVideoSupport
against-revision-140/patch/
against-revision-140/src/
against-revision-140/firmware/
against-revision-140/Makefile
against-revision-140/README
against-revision-140/
levent@levent-desktop:~/Desktop$ cd against-revision-100
bash: cd: against-revision-100: No such file or directory
levent@levent-desktop:~/Desktop$ 







Can someone help me?
It won't go further than this.

---

### Post by Zaff on 2007-11-08
> **Levo75 said:**
> 
against-revision-140/
levent@levent-desktop:~/Desktop$ cd against-revision-100
bash: cd: against-revision-100: No such file or directory


your directory is against-revision-140/ not against-revision-100/. You need to replace against-revision-100 by against-revision-140 everywhere.

Where did you get that tar file by the way ?

---

### Post by Levo75 on 2007-11-08
> **Zaff said:**
> your directory is against-revision-140/ not against-revision-100/. You need to replace against-revision-100 by against-revision-140 everywhere.

Where did you get that tar file by the way ?

It's in the original post.

How do i change the revision?

---

### Post by Zaff on 2007-11-08
> **Levo75 said:**
> It's in the original post.

How do i change the revision?
Sorry I didn't express myself properly. Apparently there was an update in the file and now it's called against-revision-140 instead of against-revision-100. All you need to do it type 140 where you where typing 100 before.
For instance :
```
cd against-revision-100/
```
is now
```
cd against-revision-140/
```

That's all. :)

---

### Post by Levo75 on 2007-11-08
> **Zaff said:**
> Sorry I didn't express myself properly. Apparently there was an update in the file and now it's called against-revision-140 instead of against-revision-100. All you need to do it type 140 where you where typing 100 before.
For instance :
```
cd against-revision-100/
```
is now
```
cd against-revision-140/
```

That's all. :)

Thank you, thank you very much.

---

### Post by cyberdork33 on 2007-11-08
> **jslmg said:**
> Thanks for all the thorough work everyone. I see some very helpful voices in this thread. 

I followed the instructions given by ivesjd and Cyberdork, and all looked great until the test. I got a message similar to the one ramvi got. However, ramvi had an output from the modprobe, which I did not. Here's my terminal output, from modprobe through test:

jslmg@Ubuntu:~/Desktop/against-revision-140$ sudo modprobe uvcvideo
jslmg@Ubuntu:~/Desktop/against-revision-140$ gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=352,height=288 ! ffmpegcolorspace ! ximagesink
Setting pipeline to PAUSED ...
ERROR: Pipeline doesn't want to pause.
ERROR: from element /pipeline0/v4l2src0: Cannot identify device '/dev/video0'.
Additional debug info:
v4l2_calls.c(424): gst_v4l2_open (): /pipeline0/v4l2src0:
system error: No such file or directory
Setting pipeline to NULL ...
FREEING pipeline ...
jslmg@Ubuntu:~/Desktop/against-revision-140$ 

Some notes: My iSight is a Firewire model, not USB. Does that make a difference here? I thought all iSights were firewire.:confused:

Would rebooting help in this, or am I missing something else, given that I have no modprobe output?

I'll try a reboot and rerun the test, let everyone know what happens...

This is for internal iSights (that are really connected via usb) so this will not work for Firewire iSight cameras.

Try this for firewire iSight:

Try this for the external iSight:
[http://ubuntuforums.org/showthread.php?t=572039](http://ubuntuforums.org/showthread.php?t=572039)

---

### Post by cyberdork33 on 2007-11-10
Initial post is now updated. Full 640x480 is supported.

---

### Post by zmjjmz on 2007-11-11
Trying this on Gutsy, but I keep getting this error output from the gstreamer test, on both resolutions...
```
zj1992@Blokhmen:~$ gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=352,height=288 ! ffmpegcolorspace ! ximagesink
Setting pipeline to PAUSED ...
ERROR: Pipeline doesn't want to pause.
ERROR: from element /pipeline0/v4l2src0: Cannot identify device '/dev/video0'.
Additional debug info:
v4l2_calls.c(424): gst_v4l2_open (): /pipeline0/v4l2src0:
system error: No such file or directory
Setting pipeline to NULL ...
FREEING pipeline ...

```

---

### Post by Zaff on 2007-11-11
> **cyberdork33 said:**
> Initial post is now updated. Full 640x480 is supported.

Still not working for me... it's turning the isight on and the green light is on and all but I don't see the video output whereas if I use 320x240 it works.
I thought Gstreamer needed an upgrade as well ? any news about that ?

---

### Post by cyberdork33 on 2007-11-11
> **Zaff said:**
> Still not working for me... it's turning the isight on and the green light is on and all but I don't see the video output whereas if I use 320x240 it works.
I thought Gstreamer needed an upgrade as well ? any news about that ?

Nope, I can verify it is fixed as I have used it. make sure you are using the uvcvideo module (against revision 140) and that you are not using Ubuntu's isight_usb module.
```
sudo modprobe -r isight_usb
sudo modprobe uvcvideo
```

---

### Post by cyberdork33 on 2007-11-11
> **zmjjmz said:**
> Trying this on Gutsy, but I keep getting this error output from the gstreamer test, on both resolutions...
```
zj1992@Blokhmen:~$ gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=352,height=288 ! ffmpegcolorspace ! ximagesink
Setting pipeline to PAUSED ...
ERROR: Pipeline doesn't want to pause.
ERROR: from element /pipeline0/v4l2src0: Cannot identify device '/dev/video0'.
Additional debug info:
v4l2_calls.c(424): gst_v4l2_open (): /pipeline0/v4l2src0:
system error: No such file or directory
Setting pipeline to NULL ...
FREEING pipeline ...

```

You might need to restart first.

---

### Post by zmjjmz on 2007-11-11
Already did...
And it's been happening at every resolution...

---

### Post by cyberdork33 on 2007-11-11
> **zmjjmz said:**
> Already did...
And it's been happening at every resolution...

Your module is not loading properly or something. It won't matter what res for that error, it is basically saying that the system doesn't even see the iSight at all. 

Are you running the default kernel? Can you try doing the installation instructions over. It sounds as though the default uvcvideo module is loading instead of the updated one.

---

### Post by zmjjmz on 2007-11-11
Well, I tried redoing the Howto, but upon executing the second command, I get this error message
```
mv: cannot stat `/lib/modules/2.6.22-14-generic/ubuntu/media/usbvideo/uvcvideo.ko': No such file or directory

```
But, I went there in File Browser, only to find that the file is right there...
EDIT: Nevermind that, it's just because I already did the installation...

---

### Post by MichaëlVD on 2007-11-11
Does anyone know what this means?
> 
michael@desktop:~/against-revision-140$ gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=640,height=480 ! ffmpegcolorspace ! ximagesink
Setting pipeline to PAUSED ...
Pipeline is live and does not need PREROLL ...
Setting pipeline to PLAYING ...
New clock: GstSystemClock

---

### Post by zmjjmz on 2007-11-11
^
That happened to me on a previous install...
I left it alone for a while, and then it magically worked...
Try 352x288

---

### Post by MichaëlVD on 2007-11-11
It works now, maybe because of the reboot I just did? First time I can use cheese! Photobooth was something I really missed from my time in OS X.

---

### Post by zmjjmz on 2007-11-11
Mine's working now, but at 352x288 only...

---

### Post by cyberdork33 on 2007-11-11
> **MichaëlVD said:**
> Does anyone know what this means?

This is what it was doing with the OLD version when you tried to use 640x480.

---

### Post by Zaff on 2007-11-12
> **cyberdork33 said:**
> Nope, I can verify it is fixed as I have used it. make sure you are using the uvcvideo module (against revision 140) and that you are not using Ubuntu's isight_usb module.
```
sudo modprobe -r isight_usb
sudo modprobe uvcvideo
```

Thanks, it works now... I can do effect with cheese. However camorama doesn't seem to find the isight but I don't really care.

I now have a fully working macbook under linux...

How cool is that ?
:guitar:

---

### Post by zmjjmz on 2007-11-12
After 
```
sudo modprobe -r isight_usb
sudo modprobe uvcvideo
```
and a restart, 640x480, and thus cheese, works fine.
But Skype still won't work...

---

### Post by cyberdork33 on 2007-11-12
> **zmjjmz said:**
> After 
```
sudo modprobe -r isight_usb
sudo modprobe uvcvideo
```and a restart, 640x480, and thus cheese, works fine.
But Skype still won't work...
Skype is a completely different problem. There is an issue that needs to be fixed before it will work with iSight.
[http://ubuntuforums.org/showthread.php?t=607758](http://ubuntuforums.org/showthread.php?t=607758)

---

### Post by trevelyn on 2007-11-23
MacBook 13" rev 2, iSight fix.

OK!! could someone please ammend in the 7.10 Gutsy install on the MacBook 13" that YOU CANNOT reuse the same AppleUSBVideoSupport File MORE THAN ONCE.  I see in the tutorial he mentions something about "boot OS X before booting Gutsy" I think he/she meant "install"  because I have the factory HDD in my MacBook which is TINY 60GB, and could not really handle both OS's efficiently.  So, I TESTED this with 5 installs.  Eachtime to get the iSight Working i actually had to install OS X (the quickest base install works/takes 15 minutes (MAKE SURE YOU INCLUDE PhotoBooth!!)) then erase the AppleUSBVideoSupport file from my external and then put the NEW one on it.  Then bot up the live CD install the most beautiful OS ever, Ubuntu, then do the 
```

cp /path/to/external/AppleUSBVideoSupport /lib/firm[tab]/2.[tab]

```
and
```

Also, in /etc/default/acpi-support, edit the line that begins with MODULES such that it reads: MODULES="isight_usb"

```
REBOOT
and this worked each time perfectly.  The Video doesnt work in CHEESE or GSTREAMER-PROPERTIES, (they both hang and become zombies) but in Ekiga its fine.

I have read a bunch of errors in these threads that i have read from my screen today in testing this theory, and this clears it up.  Also, you guys should stop asking for the AppleUSBVideoSupport folder itself because obviously that doesn't to work that way.

If you guys get it working in Cheese lemme know!! ;) - trev.

---

### Post by madscientist032 on 2007-11-23
> **trevelyn said:**
> MacBook 13" rev 2, iSight fix.

OK!! could someone please ammend in the 7.10 Gutsy install on the MacBook 13" that YOU CANNOT reuse the same AppleUSBVideoSupport File MORE THAN ONCE.  I see in the tutorial he mentions something about "boot OS X before booting Gutsy" I think he/she meant "install"  because I have the factory HDD in my MacBook which is TINY 60GB, and could not really handle both OS's efficiently.  So, I TESTED this with 5 installs.  Eachtime to get the iSight Working i actually had to install OS X (the quickest base install works/takes 15 minutes (MAKE SURE YOU INCLUDE PhotoBooth!!)) then erase the AppleUSBVideoSupport file from my external and then put the NEW one on it.  Then bot up the live CD install the most beautiful OS ever, Ubuntu, then do the 
```

cp /path/to/external/AppleUSBVideoSupport /lib/firm[tab]/2.[tab]

```
and
```

Also, in /etc/default/acpi-support, edit the line that begins with MODULES such that it reads: MODULES="isight_usb"

```
REBOOT
and this worked each time perfectly.  The Video doesnt work in CHEESE or GSTREAMER-PROPERTIES, (they both hang and become zombies) but in Ekiga its fine.

I have read a bunch of errors in these threads that i have read from my screen today in testing this theory, and this clears it up.  Also, you guys should stop asking for the AppleUSBVideoSupport folder itself because obviously that doesn't to work that way.

If you guys get it working in Cheese lemme know!! ;) - trev.

I've looked everywhere and I have not found anything that says the iSight's compatibility with Cheese. The only app that my built-in iSight works with is Ekiga. Cheese and sometimes aMSN don't work, both of which I gave up on installing the iSight drivers for. Hopefully the next version of Pidgin will support video chat/conferencing.

Nice to know I'm not the only one who wants iSight to work with Cheese.

---

### Post by zmjjmz on 2007-11-23
By following this tutroial ~two times, I got it to work with Cheese and all...

---

### Post by madscientist032 on 2007-11-23
> **zmjjmz said:**
> By following this tutroial ~two times, I got it to work with Cheese and all...

Two questions for you.
1. Cheese doesn't hang when you start it? 
2. what kind of webcam are we talking about?

---

### Post by cyberdork33 on 2007-11-24
> **trevelyn said:**
> MacBook 13" rev 2, iSight fix.

OK!! could someone please ammend in the 7.10 Gutsy install on the MacBook 13" that YOU CANNOT reuse the same AppleUSBVideoSupport File MORE THAN ONCE.  I see in the tutorial he mentions something about "boot OS X before booting Gutsy" I think he/she meant "install"  because I have the factory HDD in my MacBook which is TINY 60GB, and could not really handle both OS's efficiently.  So, I TESTED this with 5 installs.  Eachtime to get the iSight Working i actually had to install OS X (the quickest base install works/takes 15 minutes (MAKE SURE YOU INCLUDE PhotoBooth!!)) then erase the AppleUSBVideoSupport file from my external and then put the NEW one on it.  Then bot up the live CD install the most beautiful OS ever, Ubuntu, then do the 
```

cp /path/to/external/AppleUSBVideoSupport /lib/firm[tab]/2.[tab]

```and
```

Also, in /etc/default/acpi-support, edit the line that begins with MODULES such that it reads: MODULES="isight_usb"

```REBOOT
and this worked each time perfectly.  The Video doesnt work in CHEESE or GSTREAMER-PROPERTIES, (they both hang and become zombies) but in Ekiga its fine.

I have read a bunch of errors in these threads that i have read from my screen today in testing this theory, and this clears it up.  Also, you guys should stop asking for the AppleUSBVideoSupport folder itself because obviously that doesn't to work that way.

If you guys get it working in Cheese lemme know!! ;) - trev.

You need to use the more up-to-date uvcvideo module... the isight_usb module does not work correctly.

---

### Post by zmjjmz on 2007-11-24
> **madscientist032 said:**
> Two questions for you.
1. Cheese doesn't hang when you start it? 
2. what kind of webcam are we talking about?

1. It takes a few seconds to load it, but that's all...
2. Built in iSight on a 2006 MacBook...

---

### Post by madscientist032 on 2007-11-24
> **zmjjmz said:**
> 1. It takes a few seconds to load it, but that's all...
2. Built in iSight on a 2006 MacBook...

I'm going to try what you did on after I reinstall 7.10 for the hundredth time.

---

### Post by Grey Box on 2007-11-26
Thanks for the HOWTO. I am having some success with getting iSight to work with gstreamer and Cheese, but has anyone had any success getting it working with Gyachi?

When opening the cam, no popup comes up - I'm getting nowhere with it. It is set to receive video from /dev/video0.

I get the following error output:

> GThread-ERROR **: GThread system may only be initialized once.


Anyone had this problem? Anyone know what it means?

---

### Post by Grey Box on 2007-11-26
delete this pls

---

### Post by karl_kashofer on 2007-11-30
Hi !

I cant get the isight to work, all I get is this:

[   45.587846] uvcvideo: iSight: firmware already loaded.
[   45.587849] uvcvideo: iSight: Patching broken iSight USB interface descriptors
[   45.587859] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8501)
[   45.590184] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).

this is on a 2007 C2D Macbook.
Any help anyone ?

Thanks,
Karl

---

### Post by Zaff on 2007-11-30
is it a new generation MacBook C2D ?
try : 
```

sudo modprobe -r isight_usb uvcvideo
sudo modprobe uvcvideo

```

---

### Post by karl_kashofer on 2007-11-30
Thanks for trying to help:

karl@karl-laptop:~$ sudo modprobe uvcvideo
karl@karl-laptop:~$ dmesg | less

[18954.440616] usbcore: deregistering interface driver isight
[18954.444231] usbcore: deregistering interface driver uvcvideo
[18957.857118] Linux video capture interface: v2.00
[18957.868450] uvcvideo: iSight: firmware already loaded.
[18957.868457] uvcvideo: iSight: Patching broken iSight USB interface descriptors
[18957.868731] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8501)
[18957.871304] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[18957.873251] usbcore: registered new interface driver uvcvideo
[18957.873378] USB Video Class driver (v0.1.0)

Still nothing....
Anything else I can try ?

Cheers,
Karl

---

### Post by Zaff on 2007-11-30
you didn't answer my question, what generation is your macbook ? Did you buy the latest one ? Because as I understand it, the drivers aren't the same.

---

### Post by karl_kashofer on 2007-11-30
I bought it in September 07, I am not sure what generation that would be.

karl@karl-laptop:~/against-revision-140$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7400  @ 2.16GHz

Does that help ?

thanks,
Karl

---

### Post by Zaff on 2007-11-30
> **karl_kashofer said:**
> I bought it in September 07, I am not sure what generation that would be.

karl@karl-laptop:~/against-revision-140$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7400  @ 2.16GHz

Does that help ?

thanks,
Karl

Yep, so you have the same one I do. I think anyway.
I'm sorry, I don't think I know where your problem comes from though. Did you go through the whole tutorial at the beginning of this thread ? did you get errors during that ?

---

### Post by karl_kashofer on 2007-11-30
I went through the whole tutorial, no errors anywhere.

This is really annoying. Could it be that I need to activate it in osx somewhere ?
I never use osx, and have wiped my hd and re-installed a minimal install of it just for firmware updates.  I did the firmware update for getting the keyboard working in grub a while ago, could this be related ?

I am grateful for any help...
Cheers,
Karl
just checked, works in osx

---

### Post by cyberdork33 on 2007-11-30
It says it is finding the camera, it is just cannot communicate with it.

Try resetting the SMC controller and try again...
[http://docs.info.apple.com/article.html?artnum=303319](http://docs.info.apple.com/article.html?artnum=303319)

Also, are you on the standard Ubuntu kernel?

---

### Post by karl_kashofer on 2007-12-02
Hi !

I have reset the SMC but it is still not working.

I use the stock ubuntu gutsy kernel.

Any other hints ?

Thanks, 
karl

---

### Post by karl_kashofer on 2007-12-04
I am on 64 bit, could that be related ? 

karl@karl-laptop:~$ uname -a
Linux karl-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux
karl@karl-laptop:~$ 

Edit: ...no, same error on 32 bit feisty....

thanks,
Karl

---

### Post by cyberdork33 on 2007-12-04
> **karl_kashofer said:**
> I am on 64 bit, could that be related ? 

karl@karl-laptop:~$ uname -a
Linux karl-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux
karl@karl-laptop:~$ 

Edit: ...no, same error on 32 bit feisty....

thanks,
Karl
No, I am running on 64bit, and it works just fine.
Can you verify that the firmware is in place?
look in /lib/firmware there should be a file named 'AppleUSBVideoSupport'

---

### Post by MergeMedia on 2007-12-04
non 64 here too, and working fine on my intel mac pro..

---

### Post by Zaff on 2007-12-04
anyone get it working with camorama ? It won't even detect my Isight whereas cheese works perfectly.
Just wondering, I don't even know what camorama does really.

---

### Post by cyberdork33 on 2007-12-04
> **Zaff said:**
> anyone get it working with camorama ? It won't even detect my Isight whereas cheese works perfectly.
Just wondering, I don't even know what camorama does really.It looks like it currently only supports v4l, while the iSight is v4l2.

---

### Post by Zaff on 2007-12-04
> **cyberdork33 said:**
> It looks like it currently only supports v4l, while the iSight is v4l2.

thanks, was just wondering.

---

### Post by karl_kashofer on 2007-12-04
Firmware is there:

karl@karl-laptop:~$ ls -l /lib/firmware
insgesamt 96
drwxr-xr-x 4 root root  4096 2007-11-29 16:42 2.6.22-14-generic
-rw-r--r-- 1 root root 86712 2007-11-30 15:28 AppleUSBVideoSupport
karl@karl-laptop:~$              

And it says in dmesg it has loaded it:

[   43.235490] uvcvideo: iSight: firmware already loaded.
[   43.235494] uvcvideo: iSight: Patching broken iSight USB interface
descriptors
[   43.235504] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8
501)
[   43.238231] uvcvideo: Failed to query (135) UVC control 1 (unit 0)
: -32 (exp. 26).

Any other hints ?
Thanks,
Karl

---

### Post by cyberdork33 on 2007-12-04
I get this message when loading uvcvideo:
```
uvcvideo: iSight: firmware already loaded.
uvcvideo: iSight: Patching broken iSight USB interface descriptors
uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8501)
uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
usbcore: registered new interface driver uvcvideo
USB Video Class driver (v0.1.0)
``` The camera works fine.

---

### Post by karl_kashofer on 2007-12-04
> **cyberdork33 said:**
> I get this message when loading uvcvideo:
```
uvcvideo: iSight: firmware already loaded.
uvcvideo: iSight: Patching broken iSight USB interface descriptors
uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8501)
uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
usbcore: registered new interface driver uvcvideo
USB Video Class driver (v0.1.0)
``` The camera works fine.

How do you check the camera ?
I tried with VLC, as i am on KDE, the gstreamer command is not working for me. VLC just does not get any frames from /dev/video0

I am just looking at my VLC command, it seems to be for v4l not v4l2....

Will have to check later, thanks for the hint !
Would still be grateful for a kde program that will work with the cam.

Cheers,
Karl

---

### Post by Zaff on 2007-12-04
try with kopete, and get cheese as well. If those two work then you should be fine. cheese is using gstreamer though.

---

### Post by cyberdork33 on 2007-12-04
yea there are some oddities about the iSight that you must be able to work around still, even if v4l2 compatible. 

Ekiga works (without gstreamer), and I had seen posts here previously where someone got it working with kopete.

---

### Post by Zaff on 2007-12-05
> Ekiga works (without gstreamer), and I had seen posts here previously where someone got it working with kopete.

Mine worked with kopete out of the box...

---

### Post by karl_kashofer on 2007-12-05
Hi !

I do feel stupid now, it works fine with cheese....

Sorry for having bothered you all, thanks for your help !
Cheers,
Karl

---

### Post by dmber on 2007-12-08
just wanted to say thanks!

it worked perfectly following the directions in the first post with cheese on my first-gen macbook.

---

### Post by tiiim on 2007-12-08
> **Zaff said:**
> is it a new generation MacBook C2D ?
try : 
```

sudo modprobe -r isight_usb uvcvideo
sudo modprobe uvcvideo

```

Hello i just tried it on my c2d and works fine - however when i restart it doesnt work unless i run this command everytime? How do i set up so this will load when i load up ubuntu do i need to add this to a module file somewhere?

---

### Post by tiiim on 2007-12-08
> **tiiim said:**
> Hello i just tried it on my c2d and works fine - however when i restart it doesnt work unless i run this command everytime? How do i set up so this will load when i load up ubuntu do i need to add this to a module file somewhere?

dont worry sorted it! renamed the modules so uvcvideo.ko is active and renamed the isight usb module so it simply doesnt load.. excellent

---

### Post by tehkain on 2007-12-09
Hey all I got mine to work in ekiga but not cheese or the gstreamer test. I am using Xubuntu.

```

Setting pipeline to PAUSED ...
Pipeline is live and does not need PREROLL ...
Setting pipeline to PLAYING ...
New clock: GstSystemClock

```

But I get no window with a feed.

---

### Post by cyberdork33 on 2007-12-09
newer code builds on 2.6.24 and userspace firmware loading:
[http://bersace03.free.fr/ift/](http://bersace03.free.fr/ift/)

---

### Post by xoai on 2007-12-21
I have just followed this tutorial but I got a trouble. one of my usb ports died. My kernel version is 2.6.22-14. I noticed while booting up, I see something like HC died and PCI ..... hmmm. Any one can help me?

---

### Post by Zaff on 2007-12-21
> I have just followed this tutorial but I got a trouble. one of my usb ports died. My kernel version is 2.6.22-14. I noticed while booting up, I see something like HC died and PCI ..... hmmm. Any one can help me?
You're not very specific, can you tell us exactly what happened. Maybe give the output of the gstreamer command ?
```
gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=640,height=480 ! ffmpegcolorspace ! ximagesink
```

---

### Post by cyberdork33 on 2007-12-21
> **xoai said:**
> I have just followed this tutorial but I got a trouble. one of my usb ports died. My kernel version is 2.6.22-14. I noticed while booting up, I see something like HC died and PCI ..... hmmm. Any one can help me?
HCI?

Can you unload the uvcvideo module and see if that changes whether your USB port works or not?

```
 sudo modprobe -r uvcvideo
```

---

### Post by xoai on 2007-12-21
@Zaff: I got the error
```

Setting pipeline to PAUSED ...
ERROR: Pipeline doesn't want to pause.
ERROR: from element /pipeline0/v4l2src0: Cannot identify device '/dev/video0'.
Additional debug info:
v4l2_calls.c(424): gst_v4l2_open (): /pipeline0/v4l2src0:
system error: No such file or directory
Setting pipeline to NULL ...
FREEING pipeline ...

```

@cyberdork33:
it's still not useable. Booting up speed is too quick, I just see something HC died, fatal error, cleaning up, bla bla.

---

### Post by Zaff on 2007-12-23
ok so once in a while when I boot, the isight won't work. I don't know why and it's only been doing this recently. If i launch the gstreamer I get : ```
Setting pipeline to PAUSED ...
ERROR: Pipeline doesn't want to pause.
ERROR: from element /pipeline0/v4l2src0: Cannot identify device '/dev/video0'.
Additional debug info:
v4l2_calls.c(424): gst_v4l2_open (): /pipeline0/v4l2src0:
system error: No such file or directory
Setting pipeline to NULL ...
FREEING pipeline ...

```
Now I'll restart and it'll work fine so it might not be isight related at all but be something else completely.
Any ideas ?

---

### Post by xoai on 2007-12-24
Thank you. I just upgraded kernel to 2.6.23.12 version and everything works well. I know it's not a solution for problem like this and I still don't know exactly what's wrong.

---

### Post by [woodstock] on 2007-12-25
> **xoai said:**
> Thank you. I just upgraded kernel to 2.6.23.12 version and everything works well. I know it's not a solution for problem like this and I still don't know exactly what's wrong.

Hi,
have you tried the patch for the IR remote control yet? It is available for the 2.6.23 kernel only. [https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro]("https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro")

---

### Post by xoai on 2007-12-25
Not yet. I set up Ubuntu server then installed xorg and fluxbox. I tried to config the kernel manually but I alway get the error when boot up. My system could not mount an ext3 partition (not / partition). Something error with superblock...

I will try your configuration.

---

### Post by mabovo on 2008-01-08
Hy, when I tried to install iSight got this:

mabovo@macbook:~/downloads/against-revision-140$ sudo modprobe uvcvideo
FATAL: Could not open '/lib/modules/2.6.24-3-generic/ubuntu/media/usbvideo/uvcvideo.ko': No such file or directory
mabovo@macbook:~/downloads/against-revision-140$ 

Any clues ?

---

### Post by cyberdork33 on 2008-01-08
> **mabovo said:**
> Hy, when I tried to install iSight got this:

mabovo@macbook:~/downloads/against-revision-140$ sudo modprobe uvcvideo
FATAL: Could not open '/lib/modules/2.6.24-3-generic/ubuntu/media/usbvideo/uvcvideo.ko': No such file or directory
mabovo@macbook:~/downloads/against-revision-140$ 

Any clues ?

it says the module does not exist yet. Can you verify that it is in the location specified?  Can you try to reboot first?

---

### Post by mabovo on 2008-01-09
I follow patiently all discussions in this thread and finally got i-sight working when testing it with the command "gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=352,height=288 ! ffmpegcolorspace ! ximagesink"

The problem now is that it doesn't work with cheese (I have Hardy amd64 installed on MacBook2,1) and also when I start ekiga it opens a windows with a message: "O Ekiga não encontrou nenhum plugin de áudio utilizável. Verifique se a sua instalação está correta."
translating: Ekiga didn't find any useful audio plugin. Please check your instalation to see if it is correct" 

Besides this problem with  i-sight webcam I guess that something is missing to fix with sound too.

---

### Post by cyberdork33 on 2008-01-10
> **mabovo said:**
> I follow patiently all discussions in this thread and finally got i-sight working when testing it with the command "gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=352,height=288 ! ffmpegcolorspace ! ximagesink"If it is working with this test command, and not the one that uses width=640 and height=480, then I think you are still using the isight_usb module rather than the compiled and patched uvcvideo module.

Specifically, try this:
```
sudo modprobe -r isight_usb uvcvideo
sudo modprobe uvcvideo
```This will unload the isight_usb module, and the uvcvideo module, then reload only the uvcvideo module. Then the full-size test string should work:
```
gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=640,height=480 ! ffmpegcolorspace ! ximagesink
```
and it should work with cheese (which tried to use the full 640x480 resolution and couldn't)

If after rebooting, the behavior reverts, then you may need to blacklist the isight_usb module so that it will not load.

---

### Post by mabovo on 2008-01-10
Perfect, it worked like a charm.

Now isight is showing video in 640x480 and cheese runs very well too in 640x480.

Now I need to solve an issue with audio plugin that is blocking ekiga from running.

Thank you very much !

Complementing my post:  Ekiga is working perfect with iSight now, after installing mpg123 audio plugin.

---

### Post by punkshui on 2008-01-12
Hello,

I have been struggling to get my isight to work for a very long time in Ubuntu. I am now on Gutsy Gibbon, and have tried this tutorial and continue to receive the same errors.

My dmesg error is as follows:

> 13.752000] uvcvideo: iSight: firmware loading finish-up failed.

Running the gstreamer test I receive the following error:

> gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=352,height=288 ! ffmpegcolorspace ! ximagesink
Setting pipeline to PAUSED ...
ERROR: Pipeline doesn't want to pause.
ERROR: from element /pipeline0/v4l2src0: Cannot identify device '/dev/video0'.
Additional debug info:
v4l2_calls.c(424): gst_v4l2_open (): /pipeline0/v4l2src0:
system error: No such file or directory
Setting pipeline to NULL ...
FREEING pipeline ...]

I am running an Ubuntu only system and downloaded the isight firmware, and placed it in my /lib/firmware directory. 

I get an error with the first step of this tutorial, indicating that I don't have this uvcvideo.ko file it refers to. However, I look in the modules directory and see that a uvcvideo.ko.original is already there. I think I've already done this section of the tutorial in the past and so the uvcvideo.ko file is no longer there and is now called uvcvideo.ko.original thus giving me the error. Perhaps I am wrong though...

Thanks in advance to the community.

---

### Post by cyberdork33 on 2008-01-13
using the method in this tutorial does not require you to copy your own firmware. Please use the firmware in the package as it is known to work.

After installing the new module, make sure to reboot to make sure that all the module chnages are made known to the kernel.

---

### Post by argotnaut on 2008-01-27
This worked fine for me -- thanks for the tutorial.

Now, only one problem: I can't use iSight with sites that use the Flash plugin for video capture. Usually I have to choose "USB class device" or something similar in the plugin drop-down menu, but it's not available; only "Built-in iSight" is there, and I get a black screen.

I'm guessing that maybe the usb module that's removed in this tutorial is probably what would make this work, so I have to choose one or the other and can't have both. :(

---

### Post by cyberdork33 on 2008-01-27
> **argotnaut said:**
> This worked fine for me -- thanks for the tutorial.

Now, only one problem: I can't use iSight with sites that use the Flash plugin for video capture. Usually I have to choose "USB class device" or something similar in the plugin drop-down menu, but it's not available; only "Built-in iSight" is there, and I get a black screen.

I'm guessing that maybe the usb module that's removed in this tutorial is probably what would make this work, so I have to choose one or the other and can't have both. :(all this does is replace the usbvideo module with one that is patched for the iSight.

---

### Post by argotnaut on 2008-01-27
> **cyberdork33 said:**
> all this does is replace the usbvideo module with one that is patched for the iSight.

Oh, hmm...well then...I'm not sure where to start looking for the problem. Anyone have any ideas?

---

### Post by Zaff on 2008-01-28
> Oh, hmm...well then...I'm not sure where to start looking for the problem. Anyone have any ideas?
I would say it's flash related. I know flash is dodgy on linux at best so it would seem logical that the problem be there. For instance transparence in flash is broken on linux (as far as I know anyway)...
unfortunately if that's the case there's not much to do about it...
Let us know if you ind anything though...

---

### Post by argotnaut on 2008-01-28
Good guess, but I don't think that's it. I just plugged in my Logitech webcam, and it worked with that.  Usually there are two entries in the plugin menu for the iSight: "Built-in iSight" (which doesn't work, even on OS X) and "USB Class Video" (which does work), but only the "built-in" option appears for some reason.

---

### Post by berg82 on 2008-02-05
Hi, 

I have problem to go make the command: 

sudo apt-get install libusb-0.1-4 libusb-dev linux-headers-$(uname -r)

It says: Could not find the package linux-headers-2.6.22-12-generic

Im running 2.6.22-12 beacuse of the suspend problem in the latest kernel. 

I have downloaded the above package and then ran: sudo aptitude install linux-headers-2.6.22-12-generic and that work. 

But when I try to do a "sudo make" i got the following error: 

:~/against-revision-140$ sudo make
make -C src
make[1]: Entering directory `/home/andreas/against-revision-140/src'
Building USB Video Class driver...
cd: 1: can't cd to /lib/modules/2.6.22-12-generic/build
make[1]: *** [uvcvideo] Fel 2
make[1]: Leaving directory `/home/andreas/against-revision-140/src'
make: *** [all] Fel 2
andreas@andreas-laptop:~/against-revision-140$ 

Can Anyone help? 

Best Regards 
Berg

---

### Post by cyberdork33 on 2008-02-05
you have to have the kernel headers to link against for compiling. Did you compile this manually or something? I cannot find 2.6.22-12 for anything in the repositories (gutsy, feisty, etc)

You could try upgrading to the hardy kernel which seems to have working suspend for many people.

---

### Post by berg82 on 2008-02-05
Hi, 
Thank you for your answer. I read this thread about the suspend solution: 

[https://help.ubuntu.com/community/MacBook#head-892377c4270fcad4b93624aa340dc9077353057a](https://help.ubuntu.com/community/MacBook#head-892377c4270fcad4b93624aa340dc9077353057a)

Suspend works now and I really need this feature. Is Hardy the next release of Ubuntu? 

// Berg //

---

### Post by cyberdork33 on 2008-02-05
> **berg82 said:**
> [https://help.ubuntu.com/community/MacBook#head-892377c4270fcad4b93624aa340dc9077353057a](https://help.ubuntu.com/community/MacBook#head-892377c4270fcad4b93624aa340dc9077353057a)
Well the headers packages are right there, you just need to download and install them. If you have already, I would check that the directory it is trying to use even exists (/lib/modules/2.6.22-12-generic/build).

> **berg82 said:**
>  Suspend works now and I really need this feature. Is Hardy the next release of Ubuntu?Hardy Heron is the next version of Ubuntu, yes. You can always try getting the newer kernel, and if suspend doesn't work for you, your old kernel will still exist right there alongside it, and you can choose it in the grub menu. You can then uninstall the newer kernel if you desire.

---

### Post by JMC_Rimmer on 2008-02-17
Where is the uvcvideo module in the kernel config?  I apparently didn't build it in my new kernel :(

It sounds like it's better to use the uvcvideo-isight module anyway, but I would still like to know for future reference.

Thanks in advance.

---

### Post by cyberdork33 on 2008-02-17
> **JMC_Rimmer said:**
> Where is the uvcvideo module in the kernel config?  I apparently didn't build it in my new kernel :(

It sounds like it's better to use the uvcvideo-isight module anyway, but I would still like to know for future reference.

Thanks in advance.
I don't know that is part of the kernel actually. It is a separate module/software.

---

### Post by JMC_Rimmer on 2008-02-17
> **cyberdork33 said:**
> I don't know that is part of the kernel actually. It is a separate module/software.

I just assumed that uvcvideo must be part of the default 7.10 kernel because the first step in all the guides is:

modprobe -r uvcvideo

Thanks for the info.

---

### Post by eL_vErDe on 2008-02-17
Hello,

I'm trying to get iSight working on an iMac running Debian Lenny, kernel 2.6.24.

Here is what happens when I load uvcvideo (build from current linux-uvc today's svn snapshot).

uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8501)
uvcvideo: No valid video chain found.
usbcore: registered new interface driver uvcvideo
USB Video Class driver (v0.1.0)

gandalf@thrall:~$ md5sum /lib/firmware/isight.fw
6d4b6764538e85ab9e7e15ed21b7a60c  /lib/firmware/isight.fw

(extracted from my OSX partition, running 10.5.2).


Thanks in advance for your help,

Regards, Adam.

---

### Post by cyberdork33 on 2008-02-17
> **JMC_Rimmer said:**
> I just assumed that uvcvideo must be part of the default 7.10 kernel because the first step in all the guides is.It is included with Ubuntu by default, but it is not part of the Linux kernel (yet anyway).

> **eL_vErDe said:**
> I'm trying to get iSight working on an iMac running Debian Lenny, kernel 2.6.24.

Here is what happens when I load uvcvideo (build from current linux-uvc today's svn snapshot).

uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8501)
uvcvideo: No valid video chain found.
usbcore: registered new interface driver uvcvideo
USB Video Class driver (v0.1.0)

gandalf@thrall:~$ md5sum /lib/firmware/isight.fw
6d4b6764538e85ab9e7e15ed21b7a60c  /lib/firmware/isight.fw

(extracted from my OSX partition, running 10.5.2).
Do you have a guide that you are using to install? I am not sure how much support there is for the Leopard firmware yet, nor do I know if the iSight is supported by default in uvcvideo (we have been patching it).

---

### Post by eL_vErDe on 2008-02-18
Hello,

It's shown as supported here:
[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

See note [4] o figure out how I extracetd the firmware.


If it's not the right way, could you please tell me how I'm supposed to do ?
Could someone please email me a firmware from 10.4 ? (gandalf@le-vert.net)

---

### Post by cyberdork33 on 2008-02-18
> **eL_vErDe said:**
> Hello,

It's shown as supported here:
[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

See note [4] o figure out how I extracetd the firmware.


If it's not the right way, could you please tell me how I'm supposed to do ?
Could someone please email me a firmware from 10.4 ? (gandalf@le-vert.net)They have added some code to the main branch to support internal iSights now, yes, but nobody seems to be able to get it working, including myself. The Leopard firmware should work. If the isight-firmware-tools can use it then it is fine.

---

### Post by eL_vErDe on 2008-02-18
Okay, then I'm just missing the right linux-uvc patch.

Where can I grab it ?

Regards, Adam.

---

### Post by cyberdork33 on 2008-02-18
> **eL_vErDe said:**
> Okay, then I'm just missing the right linux-uvc patch.

Where can I grab it ?

Regards, Adam.
There is no patch anymore if you are using the latest linux-uvc. That is what is not working.

The older method to enable the iSight as shown in this thread should still work unless it is not compiling anymore. That package includes some firmware known to work previous to Leopard anyway.

---

### Post by mabovo on 2008-02-18
I am testing Hardy and when kernel changed from 2.6.24-7 to 2.6.24-8 there was no need to run against-revision-140. I tested Ekiga and it was working properly.
May I presume that uvcvideo was included in the last kernel update so ?

---

### Post by eL_vErDe on 2008-02-18
Hey, I used uvcvideo source from the first page link and applied that patch [1] to make it build.
It worked fine, but now it fails to load the firmware.

Where I'm supposed to copy the firmware ? I copied firmware/AppleUSBVideoSupport to /lib/firmware but it doesn't seem to do the trick.

Thanks in advance.

[1] [https://lists.berlios.de/pipermail/linux-uvc-devel/2007-November/002410.html](https://lists.berlios.de/pipermail/linux-uvc-devel/2007-November/002410.html)

---

### Post by eL_vErDe on 2008-02-19
Well,

Finally I got it working with current linux-uvc svn trunk.
First I checked out current svn, make, and make install

Then I rebuilt isight-firmware-tools package for my Debian system ([https://launchpad.net/isight-firmware-tools](https://launchpad.net/isight-firmware-tools)).

A last step...
I had to fix udev rules that load the firmware. In fact, I read somewhere (gentoo) that ift-load is buugy and that you'll have to specify the right usb bus and device idea.

Here is lsusb:
Bus 005 Device 003: ID 05ac:8501 Apple Computer, Inc. Built-in iSight [Micron]

And then udev rule:
ACTION=="add", SYSFS{idVendor}=="05ac", SYSFS{idProduct}=="8501", RUN+="@udevdir@/ift-load -b 005 -d 003 --firmware /lib/firmware/isight.fw"

Now the webcam works fine with ekiga and amsn, but I ve not been able to use it through gstreamer yet (I'd like to be able to use cheese)...

Here is what happens when I click test in gstreamer-properties:
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Could not negotiate format [gstbasesrc.c(2359): gst_base_src_start (): /pipeline2/v4l2src6:
Check your filtered caps, if any]

Any pointer?

Thanks.

---

### Post by eL_vErDe on 2008-02-19
Here is the errors that appear when I try to use the webcam with gstlaunch:

ERROR: Pipeline doesn't want to pause.
ERROR: from element /pipeline0/v4l2src0: Could not negotiate format

---

### Post by cyberdork33 on 2008-02-19
> **eL_vErDe said:**
> Well,

Finally I got it working with current linux-uvc svn trunk.
First I checked out current svn, make, and make install

Then I rebuilt isight-firmware-tools package for my Debian system ([https://launchpad.net/isight-firmware-tools](https://launchpad.net/isight-firmware-tools)).

A last step...
I had to fix udev rules that load the firmware. In fact, I read somewhere (gentoo) that ift-load is buugy and that you'll have to specify the right usb bus and device idea.

Here is lsusb:
Bus 005 Device 003: ID 05ac:8501 Apple Computer, Inc. Built-in iSight [Micron]

And then udev rule:
ACTION=="add", SYSFS{idVendor}=="05ac", SYSFS{idProduct}=="8501", RUN+="@udevdir@/ift-load -b 005 -d 003 --firmware /lib/firmware/isight.fw"

Now the webcam works fine with ekiga and amsn, but I ve not been able to use it through gstreamer yet (I'd like to be able to use cheese)...

Here is what happens when I click test in gstreamer-properties:
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Could not negotiate format [gstbasesrc.c(2359): gst_base_src_start (): /pipeline2/v4l2src6:
Check your filtered caps, if any]

Any pointer?

Thanks.
Well that is helpfull, I assumed that the udev rule was fine. I will have to mess with this tonight.
> **eL_vErDe said:**
> ERROR: Pipeline doesn't want to pause.
ERROR: from element /pipeline0/v4l2src0: Could not negotiate formatThat sounds like it is not handling the UYVY format of the isight correctly (again). it might be the the new driver fixes it or something. can you run gstreamer-properties and see what you get there?

---

### Post by chrisvdb on 2008-02-20
Hi,

I have been playing around with the latest uvcvideo driver, but had no luck in getting my isight to work.

Linux darwin 2.6.24-8-generic #1 SMP Thu Feb 14 20:40:45 UTC 2008 i686 GNU/Linux
CVS revision 186 of uvcvideo driver

The firmware and module load successfully, but no /dev/video device is created...

Feb 20 23:35:52 darwin kernel: [   35.648328] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8501)
Feb 20 23:35:52 darwin kernel: [   35.648336] uvcvideo: No valid video chain found.
Feb 20 23:35:52 darwin kernel: [   35.649122] usbcore: registered new interface driver uvcvideo
Feb 20 23:35:52 darwin kernel: [   35.649126] USB Video Class driver (SVN r186)

Does anybody have any idea on how to fix this?  I tried (almost) everything mentioned in the forum...

Thanks,
Chris.

---

### Post by cyberdork33 on 2008-02-20
> **chrisvdb said:**
>  The firmware and module load successfully, but no /dev/video device is created...

Feb 20 23:35:52 darwin kernel: [   35.648328] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8501)
Feb 20 23:35:52 darwin kernel: [   35.648336] uvcvideo: No valid video chain found.
Feb 20 23:35:52 darwin kernel: [   35.649122] usbcore: registered new interface driver uvcvideo
Feb 20 23:35:52 darwin kernel: [   35.649126] USB Video Class driver (SVN r186)

Does anybody have any idea on how to fix this?  I tried (almost) everything mentioned in the forum...That looks like what I was getting when I attempted it. Did you try editing the udev rule as suggested?

---

### Post by cyberdork33 on 2008-02-20
> **eL_vErDe said:**
> Here is lsusb:
Bus 005 Device 003: ID 05ac:8501 Apple Computer, Inc. Built-in iSight [Micron]

And then udev rule:
ACTION=="add", SYSFS{idVendor}=="05ac", SYSFS{idProduct}=="8501", RUN+="@udevdir@/ift-load -b 005 -d 003 --firmware /lib/firmware/isight.fw"
I think that is still the wrong Product ID. The iSight doesn't get the 8501 ID until after you have loaded the firmware. Until that happens it is 8300. ([http://ubuntuforums.org/showpost.php?p=4242885&postcount=3](http://ubuntuforums.org/showpost.php?p=4242885&postcount=3)) I have my verbose lsusb before loading firmware attached.

Running the ift-load command from the commandline seems to indicate that you *should* specify the Bus and Device IDs although the software is supposed to detect this automatically. I am still not getting the firmware to load though. Tried Tiger and Leopard firmware.
```
/usr/local/lib/udev/ift-load -b 005 -d 004 -f /lib/firmware/isight.fw 
ift-load: Failed to init firmware loading
ift-load: Failed to upload firmware to 005:004 (5ac:8300)
```

---

### Post by cyberdork33 on 2008-02-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/185634](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/185634) [br].[/br] ---------------------------- [br].[/br] [br].[/br]                 Ok, I think there is a bug. Try reading through this and see what  you think.
There are i386 and amd64 packages for the iSight Firmware Tools here:
[http://ppa.launchpad.net/bersace/ubuntu/pool/main/i/isight-firmware-tools/isight-firmware-tools_1.0.2-0ubuntu0~ppa1_i386.deb]("http://ppa.launchpad.net/bersace/ubuntu/pool/main/i/isight-firmware-tools/isight-firmware-tools_1.0.2-0ubuntu0%7Eppa1_i386.deb")
[http://ppa.launchpad.net/bersace/ubuntu/pool/main/i/isight-firmware-tools/isight-firmware-tools_1.0.2-0ubuntu0~ppa1_amd64.deb]("http://ppa.launchpad.net/bersace/ubuntu/pool/main/i/isight-firmware-tools/isight-firmware-tools_1.0.2-0ubuntu0%7Eppa1_amd64.deb")

The method in the bug report worked for me. Including gstreamer. I am on 2.6.24-8-generic (from hardy).

---

### Post by andybotting on 2008-02-24
> I think that is still the wrong Product ID. The iSight doesn't get the 8501 ID until after you have loaded the firmware. Until that happens it is 8300. ([http://ubuntuforums.org/showpost.php...85&postcount=3](http://ubuntuforums.org/showpost.php...85&postcount=3)) I have my verbose lsusb before loading firmware attached.

I also found this. I hacked the isight.rules file, so that it matches on the product name, rather than the ID. This doesn't change, so it works every time.

```
ACTION=="add", SYSFS{idVendor}=="05ac", SYSFS{product}=="Built-in iSight", RUN+="@udevdir@/ift-load --firmware /lib/firmware/isight.fw"
```

---

### Post by cyberdork33 on 2008-02-24
> **andybotting said:**
> I also found this. I hacked the isight.rules file, so that it matches on the product name, rather than the ID. This doesn't change, so it works every time.

```
ACTION=="add", SYSFS{idVendor}=="05ac", SYSFS{product}=="Built-in iSight", RUN+="@udevdir@/ift-load --firmware /lib/firmware/isight.fw"
```
If you look at the lsusb output I posted, it does not show that description anywhere.  The productid should be 8300 since if it is not 8300, then the firmware is already loaded.

---

### Post by mabovo on 2008-02-25
Ok, I meseed again with isight. :(
It was working properly but cheese not, so ...

All I did ? 

sudo addgroup --system usbfs
cat /etc/group | grep usbfs | sed -e 's/.*:.*:\([0-9]*\):.*/\1/' | \
xargs -iUSBFS_ID echo none /proc/bus/usb usbfs devgid=USBFS_ID,devmode=664 0 0 | sudo tee -a /etc/fstab

and isight stopped working.

Then I installed [http://ppa.launchpad.net/bersace/ubuntu/pool/main/i/isight-firmware-tools/isight-firmware-tools_1.0.2-0ubuntu0%7Eppa1_amd64.deb](http://ppa.launchpad.net/bersace/ubuntu/pool/main/i/isight-firmware-tools/isight-firmware-tools_1.0.2-0ubuntu0%7Eppa1_amd64.deb)

Now I am trying to revert this situation installing uvcvideo but something is getting wrong. 
Can be the #185634 curse ?

---

### Post by cyberdork33 on 2008-02-25
> **mabovo said:**
> Now I am trying to revert this situation installing uvcvideo but something is getting wrong.
Did you extract the firmware from the AppleDriver? Is the firmware loading on bootup?

The bug still applies as there is an issue with things somewhere, likely the usb system.

---

### Post by mabovo on 2008-02-25
mabovo@macbook:~$ sudo modprobe uvcvideo
[sudo] password for mabovo: 
mabovo@macbook:~$ 

[   40.552716] applesmc: driver successfully loaded.
[   40.611970] Linux video capture interface: v2.00
[   40.697738] usbcore: registered new interface driver uvcvideo

I guess yes !

---

### Post by cyberdork33 on 2008-02-25
Try an app that does not rely on gstreamer. Ekiga?

---

### Post by mabovo on 2008-02-25
Ekiga doesn't work too.
This problem is similar to HP printers not functioning like before.
Kernel 2.6.24 changed the way it communicates with usb devices.

I am downgrading to isight-firmware-tools-1.0.1 and installing it again to see what happens.

---

### Post by cyberdork33 on 2008-02-25
> **mabovo said:**
> Ekiga doesn't work too.
This problem is similar to HP printers not functioning like before.
Kernel 2.6.24 changed the way it communicates with usb devices.

I am downgrading to isight-firmware-tools-1.0.1 and installing it again to see what happens.
I am pretty sure that is not that issue. All the tools do is extract the firmware from the file, and load it to the iSight. If your lsusb output shows that you have an iSight (product id 8501 or 8502) then the firmware is loading... I think there is a bug in Ubuntu's uvcvideo module still.

---

### Post by mabovo on 2008-02-25
If I had a system restore point in Hardy now I could just make isight work just like early in the morning

---

### Post by cyberdork33 on 2008-02-25
> **mabovo said:**
> If I had a system restore point in Hardy now I could just make isight work just like early in the morning
don't fix what isn't broken

---

### Post by mabovo on 2008-02-26
You are buried of reasons :)

But that is the joy of alpha test.
Kernel in Hardy still not freeze and soon they will release another update.

MacBook has a series of needs of kernel improvements not just isight.

I will keep on track.

Thanks by now Cyberdork33 !

---

### Post by cyberdork33 on 2008-02-26
> **mabovo said:**
> But that is the joy of alpha test.I agree, but you have to expect stuff to break. 

Someone posted a step by step for getting it working in the iSight bug report. It looks the same as the information already posted, but better organized. You might try that.

I am probably going to do a full install of Hardy on my iMac tonight and I should be better able to tackle the problem (if I end up with a working system at all).

---

### Post by mabovo on 2008-02-26
I wish You Good Luck !

Definitely Hardy A5 kernel doesn't accept iSight module.

[HTML]
mabovo@macbook:~$ cd /lib/firmware/
mabovo@macbook:/lib/firmware$ sudo ift-extract --apple-driver AppleUSBVideoSupport
[sudo] password for mabovo: 
** Message: Found Mac OS X.4 intel driver
** Message: Firmware extracted successfully in /lib/firmware/isight.fw
** Message: Apply patch 0 : Fix video control interface descriptor
** Message: Apply patch 1 : Fix video streaming interface descriptor
** Message: Apply patch 2 : Fix video streaming device qualifier
** Message: Firmware patched successfully
mabovo@macbook:/lib/firmware$ lsusb
Bus 005 Device 003: ID 05ac:8300 Apple Computer, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 05ac:8205 Apple Computer, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 05ac:8240 Apple Computer, Inc. IR Receiver [build-in]
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 05ac:021b Apple Computer, Inc. 
Bus 001 Device 001: ID 0000:0000  
mabovo@macbook:/lib/firmware$ sudo modprobe uvcvideo
mabovo@macbook:/lib/firmware$ gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=640,height=480 ! ffmpegcolorspace ! ximagesink
Deixando a conexão como PAUSADA ...
ERRO: a conexão não quer pausar.
ERRO: do elemento /pipeline0/v4l2src0: Não foi possível identificar o dispositivo '/dev/video0'.
Informação de depuração adicional:
v4l2_calls.c(429): gst_v4l2_open (): /pipeline0/v4l2src0:
system error: Arquivo ou diretório inexistente
Deixando a conexão em NULL ...
LIBERANDO a conexão ...
mabovo@macbook:/lib/firmware$ 
[/HTML]

---

### Post by cyberdork33 on 2008-02-26
> **mabovo said:**
> Definitely Hardy A5 kernel doesn't accept iSight module.I have already got it to work once.

---

### Post by eL_vErDe on 2008-02-26
I confirm the usbid that change when loading the firmware.
It's pretty weird. The only way to get it working is to load by hand the firmware with ift-load and specify the right bus/devices ids.

Strange.

---

### Post by mabovo on 2008-02-26
> **cyberdork33 said:**
> I have already got it to work once.

I also had it working with the correct busid but when updated ift-firmware-tools to a  new version couldn't reinstall uvcvideo driver.
Where is the filled bug about isight in launchpad ? Can you post here the link again ?

Thanks.

---

### Post by eL_vErDe on 2008-02-26
I got it working everytime by adding this to /etc/rc.local:

# Load iSight firmware
for i in `seq -w 1 10`; do
  /usr/lib/udev/ift-load -b 005 -d $i --firmware /lib/firmware/isight.fw
done
rmmod uvcvideo
modprobe uvcvideo

That's dirty, really, but it does the trick until ift-load really works with udev.

Moreover, I had some bad color while using 10.5.2 firmware. I grab isight.fw from
[http://files.i-nz.net/projects/linux-kernel/isight/uvcvideo-isight.tar.gz](http://files.i-nz.net/projects/linux-kernel/isight/uvcvideo-isight.tar.gz) and it now works fine :)

However, I still only have ekiga working. Here is what happens when I click "test" in gstreamer properties:

gandalf@thrall:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Could not negotiate format [gstbasesrc.c(2359): gst_base_src_start (): /pipeline0/v4l2src3:
Check your filtered caps, if any]

---

### Post by cyberdork33 on 2008-02-26
> **eL_vErDe said:**
> I confirm the usbid that change when loading the firmware.
It's pretty weird. The only way to get it working is to load by hand the firmware with ift-load and specify the right bus/devices ids.
OK, that semi-confirms my thoughts about the issue, but I haven't messed with it anymore. I would guess there is a problem with letting udev handle the loading for some reason... maybe firmware loading should come after / before loading uvcvideo, and it's currently got it backwards.

> **mabovo said:**
> I also had it working with the correct busid but when updated ift-firmware-tools to a  new version couldn't reinstall uvcvideo driver.
Where is the filled bug about isight in launchpad ? Can you post here the link again ?You can always find the bugs that are related to mactel-support on it's launchpad page:
[https://bugs.launchpad.net/mactel-support/](https://bugs.launchpad.net/mactel-support/)

> **eL_vErDe said:**
> I got it working everytime by adding this to /etc/rc.local:

# Load iSight firmware
for i in `seq -w 1 10`; do
  /usr/lib/udev/ift-load -b 005 -d $i --firmware /lib/firmware/isight.fw
done
rmmod uvcvideo
modprobe uvcvideo

That's dirty, really, but it does the trick until ift-load really works with udev.
Great, can you post this info to the bug report. That ought to help things get fixed.

> **eL_vErDe said:**
>  Moreover, I had some bad color while using 10.5.2 firmware. I grab isight.fw from
[http://files.i-nz.net/projects/linux-kernel/isight/uvcvideo-isight.tar.gz](http://files.i-nz.net/projects/linux-kernel/isight/uvcvideo-isight.tar.gz) and it now works fine :)
That's good to know. I have firmware from Tiger and and older Leopard version. I used the leopard version and it worked fine. I am guessing that uvcvideo has not been updated to handle the newest Leopard firmware yet for some reason.

However, I still only have ekiga working. Here is what happens when I click "test" in gstreamer properties:

> **eL_vErDe said:**
>  gandalf@thrall:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Could not negotiate format [gstbasesrc.c(2359): gst_base_src_start (): /pipeline0/v4l2src3:
Check your filtered caps, if any]Does a window not open up? You can test the video on the Video tab. Those messages look semi-normal (except maybe the last part.)

---

### Post by eL_vErDe on 2008-02-26
I tried again and again, and finally, with debian unstable gstreamer packages it worked.

But I had no 640x480. I rebooted and now it works fine.

Do you want me 10.5.2 firmware that cause weird colors ?

---

### Post by cyberdork33 on 2008-02-26
> **eL_vErDe said:**
> Do you want me 10.5.2 firmware that cause weird colors ?
If you are asking what I think you are, then that should be a bug against [linux-uvc]("http://linux-uvc.berlios.de/")

---

### Post by mabovo on 2008-02-26
Finally I got it running. There is a trick pointing to the correct isight busid changing it from 005 -d 008 to 005 -d 003

---

### Post by cyberdork33 on 2008-02-26
> **mabovo said:**
> Finally I got it running. There is a trick pointing to the correct isight busid changing it from 005 -d 008 to 005 -d 003if that is what your device ID is, yes. Mine is 004.

---

### Post by cyberdork33 on 2008-02-27
Ok, got Hardy installed, (that was an effort, still no 3D acceleration >:( ).
Following the steps shown in the bug, everything is working nicely. (This is the first time I have got to use the up to date version of cheese!)

We will see if it makes it through a reboot, otherwise will do the rc.local hack to get it working. It might be better to put that in its own script and add it to your session...

---

### Post by mabovo on 2008-02-27
I hate to say that after reboot isight stopped work. :(  
Open terminal and make "gstreamer-properties" testing video results a message Video4Linux2 (v4l2) "there was not possible identify device /dev/video0" for standard input test.
Need to do a workaround as posted here before: 

mabovo@macbook:~$ sudo /usr/lib/udev/ift-load -f /lib/firmware/isight.fw -b 005 -d 003
ift-load: Firmware loaded succesfully to 005:003
mabovo@macbook:~$ sudo modprobe -r uvcvideo
mabovo@macbook:~$ sudo modprobe uvcvideo
mabovo@macbook:~$

---

### Post by mabovo on 2008-02-27
With workaround in /etc/rc.local...
Output from dmesg:

[   38.691322] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8501)
[   38.693987] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).

and lsusb:
mabovo@macbook:~$ lsusb
Bus 005 Device 004: ID 05ac:8501 Apple Computer, Inc. Built-in iSight [Micron]

---

### Post by cyberdork33 on 2008-02-27
Mine was still working after reboot. I didn't modify the udev rule, but I had to manually load the firmware the first time.

Ok, it reverted, and the ID changed back to 8300. I reloaded the firmware manually and it worked (no need to reprobe uvcvideo)

---

### Post by mabovo on 2008-02-28
Any news with the last kernel modules released on Hardy ?
I had to install all it again.  :(

---

### Post by alinux on 2008-03-14
Hello,

I'm on Hardy Alpha 6 Now.

My kernel is:

```
Linux MacBook 2.6.24-11-mactel #1 SMP Fri Mar 7 07:10:44 UTC 2008 i686 GNU/Linux
```

I've installed isight-firmware-tools

My final message is
```
** Message: Found Mac OS X.5.1 late 2007 driver
** Message: Firmware extracted successfully in /lib/firmware/isight.fw
** Message: Apply patch 0 : Fix video control interface descriptor
** Message: Apply patch 1 : Fix video streaming interface descriptor
** Message: Apply patch 2 : Fix video streaming device qualifier
** Message: Firmware patched successfully
```

Everyting seems to be done in a right way... but I can't still use my WebCam :/

[http://paste.ubuntu-nl.org/59641/](http://paste.ubuntu-nl.org/59641/) <-- Here is my entire Bash command list...

Thank you all in advance!

---

### Post by mabovo on 2008-03-14
Finally  isight is working under kernel 2.6.24-12.22 generic  in Hardy.
I don't know about Gutsy.

Just follow instructions on [http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoAppleiMac24#Update_for_Ubuntu_8_04_Hardy_Her](http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoAppleiMac24#Update_for_Ubuntu_8_04_Hardy_Her)
and write in /etc/rc.local  "sudo /usr/lib/udev/ift-load -f /lib/firmware/isight.fw -b 005 -d XXX" as an workaround for every reboot.
XXX must b replaced for your uvcvideo device in lsusb

---

### Post by cyberdork33 on 2008-03-14
> **mabovo said:**
> write in /etc/rc.local  "sudo /usr/lib/udev/ift-load -f /lib/firmware/isight.fw -b 005 -d XXX" as an workaround for every reboot.
XXX must b replaced for your uvcvideo device in lsusb
You only need to do that if it does not load by itself (like it is supposed to). It is working fine for me.

---

### Post by cyberdork33 on 2008-03-14
> **alinux said:**
> My final message is
```
** Message: Found Mac OS X.5.1 late 2007 driver
** Message: Firmware extracted successfully in /lib/firmware/isight.fw
** Message: Apply patch 0 : Fix video control interface descriptor
** Message: Apply patch 1 : Fix video streaming interface descriptor
** Message: Apply patch 2 : Fix video streaming device qualifier
** Message: Firmware patched successfully
```Everyting seems to be done in a right way... but I can't still use my WebCam :/
That is the firmware extraction. It is succeeded! You have to load the firmware into the camera now.

---

### Post by mabovo on 2008-03-15
> **cyberdork33 said:**
> You only need to do that if it does not load by itself (like it is supposed to). It is working fine for me.

So I let udev load it automatically ?

---

### Post by alinux on 2008-03-15
Dear People,

I solved my iSight issue... now it works!

so my iSight ID was on:

Bus 007 Device 003

I loaded firmware with this command:

```
sudo /usr/lib/udev/ift-load -f /lib/firmware/isight.fw -b 007 -d 003
```

and then added this line in /etc/rc.local . So i have firmware loaded on every reboot.

---

### Post by cyberdork33 on 2008-03-16
> **mabovo said:**
> So I let udev load it automatically ?
Yes, that is what the udev rule is for...

---

### Post by mabovo on 2008-03-16
No, for it doesn't work. If I remove it uvcvideo doesn't load in the next reboot.

---

### Post by cyberdork33 on 2008-03-16
> **mabovo said:**
> No, for it doesn't work. If I remove it uvcvideo doesn't load in the next reboot.
I didn't say it will work, I said it should work. It works for me, I don't know why the difference... I was having the same issue as you were having, but after a reinstall it started working by itself. I was trying to determine if the udev rule was even executing, which it seems to not be for some people for some reason.

---

### Post by mabovo on 2008-03-16
I will reinstall Hardy after beta freeze because gnome is behaving weird. Sound is no good and gdm is a trouble too. In general all devices are running well with Hardy.
MacBook 2,1.

---

### Post by cyberdork33 on 2008-03-16
yea, I had all sorts of problems recently so I have been waiting for beta release.

---

### Post by cyberdork33 on 2008-03-26
There is a new version of isight-firmware-tools:
[http://ppa.launchpad.net/bersace/ubuntu/pool/main/i/isight-firmware-tools/](http://ppa.launchpad.net/bersace/ubuntu/pool/main/i/isight-firmware-tools/)

This version uses HAL to load the firmware rather than relying on a udev script. Please test!

---

### Post by xerosis on 2008-03-26
I've never gotten my iSight to work ever, period. But I installed the hardy backports modules and it now works pretty well. It crashes my system every now and then but seems to work pretty well.

---

### Post by zmjjmz on 2008-03-26
> **cyberdork33 said:**
> There is a new version of isight-firmware-tools:
[http://ppa.launchpad.net/bersace/ubuntu/pool/main/i/isight-firmware-tools/](http://ppa.launchpad.net/bersace/ubuntu/pool/main/i/isight-firmware-tools/)

This version uses HAL to load the firmware rather than relying on a udev script. Please test!

I tried installing it (the 1.2 i386.deb), but the installer says it can't satisfy a libc6 dependency...

---

### Post by cyberdork33 on 2008-03-26
> **zmjjmz said:**
> I tried installing it (the 1.2 i386.deb), but the installer says it can't satisfy a libc6 dependency...
I think it requires Hardy...

---

### Post by mabovo on 2008-03-26
I did amd64 installation of  isight-firmware-tools_1.2-0ubuntu0~ppa1_amd64.deb.
Not sure but seems that video is more green and less brown on Ekiga (i945GM)

---

### Post by thaumaturge on 2008-03-30
Hi there,

I have recently upgraded to Hardy and when I follow the instructions, i.e. sudo make, I get an Error 2 message.

Any solutions?

Peter

---

### Post by cyberdork33 on 2008-03-30
> **thaumaturge said:**
> Hi there,

I have recently upgraded to Hardy and when I follow the instructions, i.e. sudo make, I get an Error 2 message.

Any solutions?

Peter
this doesn't work on hardy. you need the iSight-Firmware-Tools package.
[https://edge.launchpad.net/~mactel-support/+archive](https://edge.launchpad.net/~mactel-support/+archive)

---

### Post by sheffrem on 2008-03-30
HI.
I dont know what i did wrong but i did everything from download of the uvcvideo tar file to the make install and it all went well.
The gstreamer test fails. So used dmesg after loading the module. Here are the output of both gstreamer and dmesg.

root@haku-laptop:/home/haku# gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=352,height=288 ! ffmpegcolorspace ! ximagesink
Setting pipeline to PAUSED ...
ERROR: Pipeline doesn't want to pause.
ERROR: from element /pipeline0/v4l2src0: Cannot identify device '/dev/video0'.
Additional debug info:
v4l2_calls.c(424): gst_v4l2_open (): /pipeline0/v4l2src0:
system error: No such file or directory
Setting pipeline to NULL ...
FREEING pipeline ...


[ 1243.646304] uvcvideo: iSight: invalid firmware file
[ 1243.646383] usbcore: registered new interface driver uvcvideo
[ 1243.646389] USB Video Class driver (v0.1.0)

---

### Post by sheffrem on 2008-03-30
GOD is Gooooooooooooooo00D
Its Working.

Why?
I just went to the /lib/firmware folder and realized that there was a file called
AppleUSBVideoSupport
So i copied the file to /lib/firmware/2.6.22-14-generic/
And then executed the following commands

modprobe  -r uvcvideo
modprobe  uvcvideo

then 
gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=352,height=288 ! ffmpegcolorspace ! ximagesink


Et Voila. Ca marche.

---

### Post by madscientist032 on 2008-03-30
Is that for Hardy or Gusty?

---

### Post by sheffrem on 2008-03-31
i used 7.10. 
I'm the only one who had this kind of problems. See below to get what i'm talking about

Note: For some unknown reasons when make install is run, it does not copy the file uvcvidoe.ko from the against-revision-140/src folder to /lib/modules/2.6.22-14-generic/ubuntu/media/usbvideo/ wich made cheese to hang and other application either behave strangely.
 So i copied it manually and now all is ok.

---

### Post by cyberdork33 on 2008-04-01
> **madscientist032 said:**
> Is that for Hardy or Gusty?For Hardy, the uvcvideo module does not need replaced. Just install iSight-Firmware-Tools
[https://edge.launchpad.net/~mactel-support/+archive](https://edge.launchpad.net/~mactel-support/+archive)

You will need to extract the firmware from theAppleUSBVideoSupport file.
Follow the** "**From deb on mactel" section of the how to at:
[http://bersace03.free.fr/ift/](http://bersace03.free.fr/ift/)

---

### Post by sheffrem on 2008-04-06
HI,
When i start cheese it just hangs.
Then i have to run
modprobe  -r isght_usb
modprobe  -r uvcvideo

and then 

modprobe uvcvideo before it works ok with the application like chees, ekiga why is that so. Pls help me

---

### Post by cyberdork33 on 2008-04-06
you should block isight_usb from loading. Add "blacklist isight_usb" to /etc/modprobe.d/blacklist

---

### Post by russo.mic on 2008-04-11
ERROR: pipeline could not be constructed: no element "v4l2src".

upon Gstreamer launch,  

Any ideas?

Thanks!

Russo

---

### Post by cevans on 2008-04-12
> **cyberdork33 said:**
> For Hardy, the uvcvideo module does not need replaced. Just install iSight-Firmware-Tools
[https://edge.launchpad.net/~mactel-support/+archive](https://edge.launchpad.net/~mactel-support/+archive)

You will need to extract the firmware from theAppleUSBVideoSupport file.
Follow the** "**From deb on mactel" section of the how to at:
[http://bersace03.free.fr/ift/](http://bersace03.free.fr/ift/)

Hmmm... this isn't working for me, at least with the hal-based loading. It appears that hal simply doesn't try to load the firmware at all, despite anything I try to do. Loading manually with ift-load works fine, however.

The problem with dbus/hal based systems, it seems, is that when they don't work, there's simply no way for the user to fix them manually, whereas the systems dbus and hal are replacing are generally more transparent. How can I even tell if hal is trying to load the firmware?

---

### Post by cyberdork33 on 2008-04-12
> **russo.mic said:**
> ERROR: pipeline could not be constructed: no element "v4l2src".

upon Gstreamer launch,  

Any ideas?
What distro are you using?

> **cevans said:**
> How can I even tell if hal is trying to load the firmware?Well, let first see how you know that it is not working.... What are you doing to test the camera?

check the output of dmesg when you load the firmware, this should also show when it is being loaded via HAL.

---

### Post by Fr3eMaN on 2008-04-18
Whats with Isight on Hardy Heron? Does it work with the guid from page 1 ? Also with ne newest kernel?
Thanks

---

### Post by cyberdork33 on 2008-04-18
> **Fr3eMaN said:**
> Whats with Isight on Hardy Heron? Does it work with the guid from page 1 ? Also with ne newest kernel?
Thanks
On Hardy, you need to install iSight-Firmware-Tools. It has all changed since gutsy. You can get the packages in the mactel-support repo:
[https://edge.launchpad.net/~mactel-support/+archive](https://edge.launchpad.net/~mactel-support/+archive)

---

### Post by guj4_n3b3sk4 on 2008-04-21
I need step by step explanation how to set up iSight camera on Intel based Macbook, 64-bit with Hardy on it. 

Thank you.

---

### Post by Fr3eMaN on 2008-05-01
hey
now, my Isight Camera works very well with Hardy Heron, but the Image and videoquality is really bad . Is there an option to improve the quality?

---

### Post by cyberdork33 on 2008-05-01
> **Fr3eMaN said:**
> hey
now, my Isight Camera works very well with Hardy Heron, but the Image and videoquality is really bad . Is there an option to improve the quality?
no

Please avoid posting here. There is a new forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

