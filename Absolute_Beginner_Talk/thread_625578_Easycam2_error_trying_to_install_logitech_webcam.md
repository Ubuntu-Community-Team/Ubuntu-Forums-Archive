---
title: "Easycam2 error trying to install logitech webcam"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by acl123 on 2007-11-28
Hi,
I'm trying to install my logitech webcam using easycam2.
After download the packages it gives me the following error:

> 
rm -r -f drivers/usb/*.o drivers/usb/.spcadecoder.o.cmd \
        drivers/usb/.spca5xx.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i
mkdir -p /lib/modules/2.6.22-14-rt/kernel/drivers/usb/media/
rm -f /lib/modules/2.6.22-14-rt/kernel/drivers/usb/media/spca50x.ko
rm -f /lib/modules/2.6.22-14-rt/kernel/drivers/usb/media/et61x.ko
install -c -m 0644 spca5xx.ko /lib/modules/2.6.22-14-rt/kernel/drivers/usb/media/
install: cannot stat `spca5xx.ko': No such file or directory
make: *** [install] Error 1


Does anyone know what I can do?

When I open camorama it cannot connect to my video device.

I am using a Logitech Quickcam for Notebooks (although I'm doing this on my desktop). I have Gutsy "upgraded" to UbuntuStudio.

---

### Post by ukripper on 2007-11-28
try easycam1

---

### Post by acl123 on 2007-11-28
Hi thanks,
Easycam1 couldn't detect my webcam - it asked me to forward "ID 046d:08ae Logitech, Inc." to the developer's gmail account. I guess I could I try that hope for the best?

---

### Post by ukripper on 2007-11-28
> **acl123 said:**
> Hi thanks,
Easycam1 couldn't detect my webcam - it asked me to forward "ID 046d:08ae Logitech, Inc." to the developer's gmail account. I guess I could I try that hope for the best?

Bizarre, I am using unbranded webcam with 6 auto leds with easycam1 and all works great.Irony,  Logitech drivers are most supported in ubuntu

---

### Post by philinux on 2007-11-28
you need this driver.

[http://mxhaard.free.fr/spca50x/Download/gspcav1-20070508.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20070508.tar.gz)

---

### Post by acl123 on 2007-11-28
Thanks,
I downloaded and unzipped the file, then typed "make" in the directory. Then I restarted my computer.

I can open Camorama now and it doesn't complain, but I can only see a black screen.

Any ideas?

Where did you find the driver?

---

### Post by ukripper on 2007-11-29
> **acl123 said:**
> Thanks,
I downloaded and unzipped the file, then typed "make" in the directory. Then I restarted my computer.

I can open Camorama now and it doesn't complain, but I can only see a black screen.

Any ideas?

Where did you find the driver?

First try it on some other app like skype beta 2.0 probably comorama is not able to detect it properly.
Skype 2.0 beta might do [http://share.skype.com/sites/linux/2007/11/skype_20_beta_for_linux_with_video.html](http://share.skype.com/sites/linux/2007/11/skype_20_beta_for_linux_with_video.html)

---

### Post by philinux on 2007-11-29
Try using Kopete with your cam it seems to sort itself out pretty well.

You choose configure then devices, your cam should then fire up.

---

### Post by acl123 on 2007-11-29
Thanks guys.

My current status -

[LIST]
[*]Webcam picture is working fine on Skype Beta 2 as long as the camera is plugged in before I boot Ubuntu.
[*]Camorama is working now but has a black line with white static at the bottom of the picture. I'm not sure what caused Camorama to start working... possibly installing Skype triggered something.
[*]Kopete crashes completely when I select my webcam
[*]XawTV won't launch (terminates with message "X Error of failed request:  XF86DGANoDirectVideoMode"
[/LIST]

As a further annoyance -

With my camera plugged in my sound dies in all programs. I have to restart my computer without the camera plugged in to get sound back. I haven't tested it yet but I assume this means I won't have much fun with video chat until I can fix the sound.


So it's a bit hit and miss at this stage, but somewhat usable.

---

