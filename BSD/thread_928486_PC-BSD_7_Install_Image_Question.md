---
title: "PC-BSD 7 Install Image Question"
date: 2008-09-24
forum: BSD
---

### Post by kpkeerthi on 2008-09-24
[http://www.pcbsd.org/content/view/21/11/#USB](http://www.pcbsd.org/content/view/21/11/#USB)

What is this .img file? How do I copy the img file to my flash drive? Should I simply dd it to my flash drive? 

My flash drive's capacity is 2GB. Will this image fit in the drive?

---

### Post by mips on 2008-09-24
dd

---

### Post by kpkeerthi on 2008-09-24
Thanks. I wish the PC-BSD folks documented it somewhere.

---

### Post by mips on 2008-09-25
> **kpkeerthi said:**
> Thanks. I wish the PC-BSD folks documented it somewhere.

They did, you were just to lazy to follow their instructions ;)

The very page you linked to says:
> 
Download PC-BSD    PDF    Print 
  Download PC-BSD 7 (Release name: Fibonacci Edition)
(Download PC-BSD Legacy 1.x here )

PC-BSD is released under the BSD license

**Before downloading PC-BSD, you may want to have a look at the** **[COLOR="Red"]quick guide[/COLOR]**. You can report issues on the bug tracker or on the mailing list. If you like PC-BSD, please consider making a donation! If you are on a high-speed connection, and want to help mirror these files, you may do so here . 

Now if you looked at the quick guide you would have seen under section 2.6

> 2.6 Writing the ISO to Flash media
To write the USB ISO file to a Flash Card or USB pen drive you can do this with the Unix command 'dd':
[COLOR="Red"]dd if=<path_to/img_file.iso> of=/dev/da0 bs=1m[/COLOR]
Just substitute da0 with the device name of your USB stick.

---

### Post by kpkeerthi on 2008-09-25
I didn't mean to criticize. Well... Yes, I'm an idiot.

---

### Post by mips on 2008-09-25
> **kpkeerthi said:**
> I didn't mean to criticize. Well... Yes, I'm an idiot.

No you are not an idiot. Never refer to yourself in a negative way. You just did not follow their instructions.

---

### Post by thisllub on 2008-11-11
> **mips said:**
> They did, you were just to lazy to follow their instructions ;)

The very page you linked to says:


Now if you looked at the quick guide you would have seen under section 2.6

2.6 Writing the ISO to Flash media
To write the USB ISO file to a Flash Card or USB pen drive you can do this with the Unix command 'dd':
dd if=<path_to/img_file.iso> of=/dev/da0 bs=1m
Just substitute da0 with the device name of your USB stick. 


From Linux bs=1m is not accepted.
bs=1M is.

---

### Post by OTuRaNBoGHa on 2008-12-14
> **mips said:**
> They did, you were just to lazy to follow their instructions ;)

The very page you linked to says:


Now if you looked at the quick guide you would have seen under section 2.6
well, the code is for the *.iso file. does it also apply for the *.img file? btw, I'm currently using Vista x64. how can I install the pcbsd_usb.img file to my USB flash drive?

---

### Post by mips on 2008-12-14
> **OTuRaNBoGHa said:**
> well, the code is for the *.iso file. does it also apply for the *.img file? btw, I'm currently using Vista x64. how can I install the pcbsd_usb.img file to my USB flash drive?

It's a typo on their part as far as i can tell, I'm sure they meant *.img file as it's kinda pointless trying to write a *.iso to a flash key.

No idea on how to do this in Vista, sorry.

---

### Post by luposolo on 2008-12-15
im trying to figure thisout my self how do i boot with .img file with windows

---

### Post by luposolo on 2008-12-15
i tried to copy the .img file to the usb thumb drive and boot with it but it didnt work

---

### Post by mips on 2008-12-15
> **luposolo said:**
> i tried to copy the .img file to the usb thumb drive and boot with it but it didnt work

You cannot simply copy the file as that will not write the image to disk and creat a filesystem etc.

I did some googling for you and see there is a dd for Windows.

[http://www.chrysocome.net/dd](http://www.chrysocome.net/dd)
[http://software.intel.com/en-us/articles/dd-for-windows](http://software.intel.com/en-us/articles/dd-for-windows)
[http://uranus.chrysocome.net/linux/rawwrite/](http://uranus.chrysocome.net/linux/rawwrite/)
[http://kennethhunt.com/archives/001030.html](http://kennethhunt.com/archives/001030.html)


Be CAREFULL wit dd as it is a powerfull tool that if used wrong could cause loss of your data.

---

### Post by luposolo on 2008-12-15
I just got cd today, so i'm just gonna download the 3 iso images for pc bsd and install it that way

---

