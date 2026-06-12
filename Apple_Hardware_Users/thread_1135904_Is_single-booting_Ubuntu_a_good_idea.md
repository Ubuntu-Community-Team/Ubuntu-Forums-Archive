---
title: "Is single-booting Ubuntu a good idea?"
date: 2009-04-24
forum: Apple Hardware Users
---

### Post by aufan19 on 2009-04-24
Hi everyone,

I am considering installing Ubuntu 9.04 on my MacBook 4,1, but I am not sure if I should set it up as a single-boot or dual-boot. I have read that it is a good idea to at least keep OS X installed on a small partition for MacBook firmware updates. What is the best thing to do? Have any of you run into an major problems running Ubuntu on your Macs?

I am thinking of doing this because I am beginning to feel bored with OS X, and I think that Linux would be a good change. OS X also doesn't seem to have shipped with any scanning software, but my printer is supported under XSane. The ability to scan documents would be wonderful.

---

### Post by JK3mp on 2009-04-24
I would strongly recommend that you keep OSX on there. Always best. At least until you know that you won't have problems with Ubuntu. Could be hardware issue's etc. IM not sure how extreme this is, i've never put linux on a mac b4 though so :P

---

### Post by nathang1392 on 2009-04-24
Ubuntu is great, But if you arent pretty familiar with it...dont completely burn your bridges. it can be difficult and requires some learning.

---

### Post by mkvnmtr on 2009-04-24
I have one machine that is only Ubuntu and it is fine. It had a very fouled up windows os on it when I bought it for about $25 american. On my Mac I have both and would not delete the mac os even though I don't use it. I would never delete a paid for os. You never know when you might need something that that os can do easier than the one you are using.

---

### Post by kye_ on 2009-04-24
I recomend keeping an os x partition. Mainly because it greatly reduces boot time. Firmware updates are important too.

As far as ubuntu on a mac, I very happy with it on my macbook 2,1.

---

### Post by cyberdork33 on 2009-04-24
> **aufan19 said:**
> Hi everyone,

I am considering installing Ubuntu 9.04 on my MacBook 4,1, but I am not sure if I should set it up as a single-boot or dual-boot. I have read that it is a good idea to at least keep OS X installed on a small partition for MacBook firmware updates. What is the best thing to do? Have any of you run into an major problems running Ubuntu on your Macs?

I am thinking of doing this because I am beginning to feel bored with OS X, and I think that Linux would be a good change. OS X also doesn't seem to have shipped with any scanning software, but my printer is supported under XSane. The ability to scan documents would be wonderful.
Image Capture can use a scanner as source.

You can also get Xsane in OSX through Darwinports:
[http://xsane.darwinports.com/](http://xsane.darwinports.com/)

Kye, like the logo... that is a good one.

---

### Post by jamessnell on 2009-04-25
Mac OS can boot very happily from an external (such as usb) hard drive. So, if you have an extra USB hard drive or possibly even a flash drive (though I've never tried that). So if you wanted you could move your Mac OS setup over there. If you use the Disk Utility from the install disc, you can move your current setup over to the external drive without losing data provided your external drive is large enough - be sure to test it for speed :)

---

### Post by aufan19 on 2009-04-25
Thanks for the replies everyone!! I've decided to test Ubuntu in VirtualBox instead so that I can become more familiar with it.

---

### Post by jamessnell on 2009-04-25
> **aufan19 said:**
> Thanks for the replies everyone!! I've decided to test Ubuntu in VirtualBox instead so that I can become more familiar with it.

Cool, just know that the disk io will be a lot slower and you won't be able to see much eye candy. :)

---

### Post by markitoxs on 2009-04-25
The only way to properly learn... a single boot.

---

### Post by jamessnell on 2009-04-25
> **markitoxs said:**
> The only way to properly learn... a single boot.

Yeah, what he said.

---

### Post by TR1X on 2009-04-25
I don't see why you couldnt just reinstall osx if things went bad.

make sure to back up all files you need to keep though.

---

### Post by jamessnell on 2009-04-26
> **TR1X said:**
> I don't see why you couldnt just reinstall osx if things went bad.

make sure to back up all files you need to keep though.

Well, I can forsee some major pain with partitioning.. I'm pretty sure the OSX installer won't let you install to a non-GPT partitioned drive. So if you have a singly partitioned drive for Ubuntu and then use a MBR partitioning tool such as gparted to make a new partition for OSX, you'll still be screwed...

Does that make sense, need more detail?

---

### Post by cyberdork33 on 2009-04-27
> **jamessnell said:**
> Well, I can forsee some major pain with partitioning.. I'm pretty sure the OSX installer won't let you install to a non-GPT partitioned drive. So if you have a singly partitioned drive for Ubuntu and then use a MBR partitioning tool such as gparted to make a new partition for OSX, you'll still be screwed...

Does that make sense, need more detail?
I think his point was, try to do a single-boot, and if you are not happy with it, just reinstall OSX and start from scratch again.

---

### Post by jamessnell on 2009-04-27
> **cyberdork33 said:**
> I think his point was, try to do a single-boot, and if you are not happy with it, just reinstall OSX and start from scratch again.

Yeah, I suppose that's probably what he meant. :)

---

