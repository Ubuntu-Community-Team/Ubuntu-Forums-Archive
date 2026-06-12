---
title: "Help with Webcam"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by gothica on 2007-06-11
i just recently bought this webcam from my favorite store. I plugged it in one of my usb ports. I checked device manager:

[IMG]http://i15.tinypic.com/6co4774.png[/IMG]

So it says there that its detected as a PC Camera with Vimicro Corp as the vendor. Also i checked on the terminal and typed **lsusb**:

[IMG]http://i14.tinypic.com/5xf8rrk.png[/IMG]

These steps that i did where as directed by some how to's i've read. So i came into thinking that my webcam is detected/recognized by the system, am i right? Because when i try to use it on **Ekiga** it tells me that there were no video input device detected (i checked for both V4L and V4L2). I am not able to use my webcam for any video software at all (e.g. xawtv,skype).

Is there something i've missed? Do i have to install additional driver/software for me to use it? Any help would be much appreciated. ;)

PS. I've already checked out [http://mxhaard.free.fr/]("http://mxhaard.free.fr/"), i checked synaptic if it has the driver there for download, and it has. i installed it, but still nothing happens. So i came to thinking: it's either not working or i don't know how to use it. oh and for the record, the webcam works on windows with the bundled driver installed.

---

### Post by gothica on 2007-06-11
bump!

im sorry but any help would be appreciated. this problem is really frustrating me.

---

### Post by seshomaru samma on 2007-06-11
how about [_**this**_ ]("https://help.ubuntu.com/community/Webcam")?

---

### Post by gothica on 2007-06-11
i've already seen this site. thanks for replying anyway.
another thing, when i can connect my webcam in the usb port it gets listed on device manager, however it doesn't show up on my devices folder (no **/dev/video***).

---

### Post by Adramelech on 2007-06-11
Check if the driver is loaded: lsmod
if not, load it with:
sudo modprobe driver_name

---

### Post by gothica on 2007-06-11
which driver should i look for? there so many listed, so i did this next

**lsmod | grep "usb"**

then i got his result:

> usbcore               134280  3 ehci_hcd,uhci_hcd

---

### Post by chemtut on 2007-06-11
have you tried either camstream or camorama ?
they can both be downloaded with synaptic

---

### Post by xarroyo on 2007-09-04
[http://ubuntuforums.org/showthread.php?t=530727](http://ubuntuforums.org/showthread.php?t=530727) check this site!! for other users it worked..! for me the first time it worked... but i am trying to find out what happened!!

---

