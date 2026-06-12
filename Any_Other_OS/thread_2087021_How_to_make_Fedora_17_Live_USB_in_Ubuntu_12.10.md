---
title: "How to make Fedora 17 Live USB in Ubuntu 12.10"
date: 2012-11-22
forum: Any Other OS
---

### Post by meijin3 on 2012-11-22
Unetbootin apparently does not support Fedora 17 (I've even tested and confirmed that this method does not work). Startup Disk Creator will not load the Fedora .iso. The "dd if=/path/to/iso-file of=/dev/sdc" method resulted in a blank screen when trying to boot from the USB. 

Does anyone know how I can make a Live USB of Fedora in Ubuntu? Even better, I'd like to just use my Class 10 32 GB SD Card as a separate hard drive with Fedora installed on it. Thanks Ubuntu Community.

---

### Post by snowpine on 2012-11-22
Hi, did you see these instructions?

[http://docs.fedoraproject.org/en-US/Fedora/17/html/Installation_Guide/Making_USB_Media-UNIX_Linux.html](http://docs.fedoraproject.org/en-US/Fedora/17/html/Installation_Guide/Making_USB_Media-UNIX_Linux.html)

---

### Post by meijin3 on 2012-11-22
Looking over the instructions you gave me, how does one format something to vfat? Is this similar to fat32?

---

### Post by snowpine on 2012-11-22
I *think* fat32 should be okay, but I am not really a Fedora user. :)

---

### Post by monkeybrain2012 on 2012-11-22
Easiest way which also has the option to add persistence, also creates  live usbs for many other distros and multiboot usbs. 

[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)


I can confirm that it works for F17 because I have done it many times. :) Strange that Unetbootin doesn't work. It used to work for Fedora 16 (though very basic, with no option for persistence)

EDITED: If you want you can also install Fedora's live usb creator in Ubuntu (not recommended as I remember that you needed to do some extra tweakings to get it to work, maybe things have changed, but it only works for Fedora, so the first method is definitely preferred if you are going to install something. :)

[http://ifireball.wordpress.com/2011/10/14/running-fedoras-liveusb-creator-on-ubuntu/](http://ifireball.wordpress.com/2011/10/14/running-fedoras-liveusb-creator-on-ubuntu/)

---

### Post by meijin3 on 2012-11-22
Thanks guys, I'm trying your suggestions.

---

