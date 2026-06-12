---
title: "How do I disable faulty laptop hardware ??"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by jadedjay on 2007-05-10
This may seem like a strange request, as searching through much of the forum trying to find how to fix my problem, I found many discussions how to getting something working.
My situation is slightly different.

I have a laptop which over the years I have been running dapper,edgy and no feisty ubuntu.
A while ago the internal cdrom died (a hardware issue I think) and the cost of replacing it is not worth it.  

When I boot into Feisty now and I switch out of gdm to the text prompt I see no stop error messages reporting that the cdrom is not working.

If I do "dmesg"  I receive a log list of 
[ 5545.680000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 5545.680000] sr: Current: sense key: Hardware Error
[ 5545.680000]     Additional sense: Head select fault
[ 5547.704000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 5547.704000] sr: Current: sense key: Hardware Error
[ 5547.704000]     Additional sense: Head select fault
[ 5549.728000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 5549.728000] sr: Current: sense key: Hardware Error
[ 5549.728000]     Additional sense: Head select fault
[ 5551.752000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[ 5551.752000] sr: Current: sense key: Hardware Error
[ 5551.752000]     Additional sense: Head select fault

I dont think I can fix the cdrom so what I need is someway of disabling it from the unbuntu services?  Is there a command I can give to stop ubuntu services constantly checking that cd rom.  I thought removing it from /etc/fstab might help, but that had no effect.

It seems that since I install feisty I am receiving more or these error messages, while in earlier versions of ubuntu the process seemed to die/stop after only a few checks of the cdrom. 

I dont want to disable all cdrom devices as I am using an external one now (as it was the cheaper option), for my cd/dvd access. Its also difficult to remove the internal cdrom from to laptop. 

Any ideas??

---

### Post by umarvlie on 2007-05-10
I am not sure if there is an easy way to do this in Ubuntu but did you try and disabe the CDRom drive in the Bios of the Laptop?

---

### Post by mbradlcu on 2007-05-10
what about commenting out the device in the /etc/fstab?

---

### Post by jadedjay on 2007-05-10
I tried commented out the entries in /etc/fstab (which I thought would work) but it had no effect.  I think the error is due to a hardware test and not an attempt to mount it.

I'll have a look again at the bios, however I havent found anything in the past that allow me to disable it.  That certainly would be the easiest option.

---

### Post by Austin_KW on 2007-05-10
You could blacklist the driver for your cdrom in /etc/modprobe.d/blacklist

Try adding the line 'blacklist cdrom'

Ah, just reread your post, you have an external drive so you will want to be a bit more specific about which driver you blacklist.
lsmod or 'lsmod | grep cd' may help identify the offending driver.

Or open up your laptop an pull the ide cable/power connector

---

