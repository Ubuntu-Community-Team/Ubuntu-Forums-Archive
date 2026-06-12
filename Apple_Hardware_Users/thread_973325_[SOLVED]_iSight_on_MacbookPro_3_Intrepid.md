---
title: "[SOLVED] iSight on MacbookPro 3 Intrepid"
date: 2008-11-06
forum: Apple Hardware Users
---

### Post by bryonak on 2008-11-06
... doesn't work anymore.


These are what I took as guides: [rickycampbell's guide]("http://www.rickycampbell.com/isight-intrepid/"), [ubuntuforums.org thread for Hardy]("http://ubuntuforums.org/showthread.php?t=764616&highlight=isight")

I upgraded from Hardy, copied the AppleUSBVideoSupport file from my OSX install, aptitude'd isight-firmware-tools which prompted me to extract the file, which in turn gave me this little file:
```
ls -l /lib/firmware/isight.fw
-rw-r--r-- 1 root root 11K 2008-11-06 20:15 isight.fw
```

Then I powered the system completely down(no reboot). After booting both Cheese and Ekiga freeze if I try to get a picture (have to kill them). With Cheese, the green light comes on shortly, but no picture. No terminal output either if started from shell.

This is what I get from dmesg:
```

[  120.877399] uvcvideo: unknown event type 198.
[  121.025332] uvcvideo: unknown event type 182.
[  126.805538] uvcvideo: unknown event type 0.
[  126.941571] uvcvideo: unknown event type 115.
[  127.077574] uvcvideo: unknown event type 121.
[  127.209573] uvcvideo: unknown event type 121.
[  127.273451] uvcvideo: unknown event type 121.
[  127.341545] uvcvideo: unknown event type 121.
[  127.409573] uvcvideo: unknown event type 121.
[  127.477544] uvcvideo: unknown event type 121.
[  127.545583] uvcvideo: unknown event type 121.
[  127.613454] uvcvideo: unknown event type 121.
...
...

```

When I reload the uvcvideo kernel module (via modprobe), dmesg gives this:
```

[ 1507.765168] usbcore: deregistering interface driver uvcvideo
[ 1514.995992] Linux video capture interface: v2.00
[ 1515.010099] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8502)
[ 1515.012577] input: Built-in iSight as /devices/pci0000:00/0000:00:1d.7/usb7/7-4/7-4:1.0/input/input16
[ 1515.032900] usbcore: registered new interface driver uvcvideo
[ 1515.032918] USB Video Class driver (v0.1.0)

```
Sounds good, but Cheese/Ekiga show the same behaviour as before.
Cheese causes the same dmesg output as the first one.

running gstreamer-properties and testing for the default input gives me this:
```
Video for Linux (v4l): Could not get/set settings from/on resource.
```


However this one **does work**: Opening VLC, input from a capture device, choosing v4l2 and this as the device
```
/devices/pci0000:00/0000:00:1d.7/usb7/7-4/7-4:1.0/input/input16
```
which gives me a stream from my webcam.

The problem is: I cannot change the device in Cheese, and a symlink (after moving the default /dev/video0 to /dev/video0.OLD) doesn't work, because Cheese complains that the file doesn't exist.
Additionally, every time I reload the uvcvideo module, the device file in the /sys/devices/pci0000:00 interface gets increased by one (input18 by now).

I'm pretty clueless about what to try next...

---

### Post by cyberdork33 on 2008-11-06
From what I understand, there is a bug in Cheese that, when launched, causes other gstreamer-based applications to break.

See discussion here:
[http://ubuntuforums.org/showpost.php?p=6096594&postcount=126](http://ubuntuforums.org/showpost.php?p=6096594&postcount=126)
and bug reports here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290506](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290506)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287888/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287888/)

Can you try Skype?

---

### Post by bryonak on 2008-11-06
Thanks for the info. Looks I've got to wait for this to get fixed.

I don't really want to install Skype, but as I've written above, VLC works well.
I've also tried luvcview, which gives me a picture too.. so it's quite probably a Cheese problem. Especially since gstreamer-properties works if I don't start Cheese before.

---

### Post by cyberdork33 on 2008-11-06
> **bryonak said:**
> Thanks for the info. Looks I've got to wait for this to get fixed.

I don't really want to install Skype, but as I've written above, VLC works well.
I've also tried luvcview, which gives me a picture too.. so it's quite probably a Cheese problem. Especially since gstreamer-properties works if I don't start Cheese before.
OK... May want to add you input to the bug reports.

---

