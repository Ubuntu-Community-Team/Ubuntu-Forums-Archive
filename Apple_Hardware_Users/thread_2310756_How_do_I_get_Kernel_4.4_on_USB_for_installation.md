---
title: "How do I get Kernel 4.4 on USB for installation?"
date: 2016-01-21
forum: Apple Hardware Users
---

### Post by craic on 2016-01-21
How can I get linux kernel 4.4 onto a live usb for installation of Ubuntu from usb? I'm trying to install on a Macbook Air (7,1), and installers are not recognizing the SSD. The new kernel is supposed to remedy that with LightNVM. Thanks in advance for any help. 

Tom D

---

### Post by howefield on 2016-01-21
Thread moved to the "*Apple Hardware Users*" sub forum.

---

### Post by monkeybrain20122 on 2016-01-21
You can make a usb with persistence, then boot off the usb from another machine, then in it download and install the kernel using mainline [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/)

To do this download three debs: kernel image for your arch (amd64 I suppose), the header for your arch, and headers all. Put all 3 in a folder, say ~/Downloads/kern then install them from the terminal

```
cd Downloads/kern
sudo dpkg -i *.deb

```

Now I have never done it in a live usb, may not work.

---

### Post by craic on 2016-01-23
Thanks for your reply. I followed those steps, but I am unable to boot from the USB drive on any system. I get the following error:

(initramfs) Unable to find a medium containing a live file system

I'm new to using a USB drive with persistence, so I could use some on help on what to do next. Thanks!

Updated: I performed a MD5sum check and they did not match, so I will recreate the USB drive with a newly downloaded iso. Hopefully, that does the trick.

---

### Post by craic on 2016-01-23
The md5sum problem was not the issue unfortunately. I still get the initramfs error.

---

### Post by craic on 2016-01-24
It might be best to just wait for Arch to release their next iso in the next few weeks.

---

