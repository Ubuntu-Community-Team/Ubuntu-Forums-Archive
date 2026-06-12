---
title: "Webcam-less"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by ElvisGump on 2008-02-05
I've been puzzling over how to get my Philips SPC610 webcam running in Skype or running at all for that matter. 

I've been all through trying to get EasyCam and a variety of other software to tell me how to do this, but a lot of the posts I've searched have been a bit vague for a newbie like me. 

On this page which seems to be connected with EasyCam though it's all in French which I don't read I did find this mention of my model
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

Philips  237 	0x093a 	0x2601 	spc610nc  Pac7311  Pac7311  Yes 	jpeg 	gspcav1  ***

Which leads me to believe there is some way to get this thing going.

I've followed the steps on these pages
[http://ralph.n3rds.net/index.php?/archives/128-ubuntu-webcam.html](http://ralph.n3rds.net/index.php?/archives/128-ubuntu-webcam.html)
When I tried the steps there I got to the part about 

> Now you simply run the installed script by:
sudo easyspca

And got a ton of stuff in the command line that ended with 

> mv: cannot stat `/lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/spca5xx.ko': No such file or directory
install: cannot stat `spca5xx.ko': No such file or directory
make: *** [install] Error 1
FATAL: Module spca5xx not found.
insmod: can't read 'spca5xx.ko': No such file or directory
FATAL: Module spca5xx not found.

I went through Synaptic and installed it from there but can't get it to run either.

Also read through and followed this stuff as best I could with no joy
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

None of this seems to get me going to a functional cam. I tried installing and running Cheese, but it reports no cam installed.

What's the trick?

---

### Post by linuxwizard on 2008-02-05
Try using Ekiga see if webcam is detected/works. Also you might have to change settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings there.

---

### Post by spiderbatdad on 2008-02-05
did you try looking in this file for the actual file name, instead of spcxx..../lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/spca5xx.ko?

---

