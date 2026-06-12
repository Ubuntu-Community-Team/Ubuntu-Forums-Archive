---
title: "How do I recover data from old hard drive in Ubuntu running on VirtualBox ??"
date: 2011-06-04
forum: Apple Hardware Users
---

### Post by ujjwalkp on 2011-06-04
Hi,

My old laptop is no more usable, I want to recover the data from the hard drive. I had ubuntu 10.04 installed. 

On my mac, I have ubuntu 11.04 running on virtual box. When I plug in my old laptop's hard disk using SATA to USB adapter, ubuntu does not mount that. As such there is no problem of mounting another hard drive with ext4 partition. I am able to read it from Ubuntu.

Any help is appreciated.

---

### Post by bdentremont on 2011-06-10
> **ujjwalkp said:**
> Hi,

My old laptop is no more usable, I want to recover the data from the hard drive. I had ubuntu 10.04 installed. 

On my mac, I have ubuntu 11.04 running on virtual box. When I plug in my old laptop's hard disk using SATA to USB adapter, ubuntu does not mount that. As such there is no problem of mounting another hard drive with ext4 partition. I am able to read it from Ubuntu.

Any help is appreciated.

I believe you could setup a USB device filter in VirtualBox on your Mac which would forward particular devices of your choosing, such this hard drive, to Ubuntu via a virtual USB controller.  Then Ubuntu would see it like mounting any other hard drive.  I don't use this feature, and, at least in the past, it was only part of the binary distribution of VirtualBox, not the open source one, so you would need to make sure that that's what you have on your Mac.

Here's the portion of the VirtualBox manual that pertains to the device filter:
[http://www.virtualbox.org/manual/ch03.html#idp11145776]("http://www.virtualbox.org/manual/ch03.html#idp11145776")

My sister uses the device filters from her Mac host, so I know it's not too bad to configure. If you have difficult with this approach, I'd try asking for help on [http://forums.virtualbox.org/](http://forums.virtualbox.org/) rather than here.

Good luck -- Brian

---

### Post by ujjwalkp on 2011-06-11
Hi Brian,

Thanks a lot, adding filters resolved my problem

Cheers

---

