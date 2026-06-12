---
title: "Creating a mountpoint?"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by tigerplug on 2008-01-10
I was just wondering how do I create a mountpoint or is it done automatically?

I was looking at this thread here: [http://ubuntuforums.org/showthread.php?t=611404&highlight=New+Generation+Ipod](http://ubuntuforums.org/showthread.php?t=611404&highlight=New+Generation+Ipod)

The third posts mentions:
```
ipod-read-sysinfo-extended DEVICE MOUNTPOINT
```

e.g. ipod-read-sysinfo-extended /dev/sda /media/ipod

I just want to know how to create this mountpoint... or if it is configured automatically how can I find out what the path to the mountpoint is?


Thanks, 

Tigerplug

---

### Post by Pevichaey5 on 2008-01-10
my ipod is mounted automatically

/media/MyIpod

but it should appear on the desktop as soon as it is mounted

---

### Post by thelatinist on 2008-01-10
> **tigerplug said:**
> I just want to know how to create this mountpoint... or if it is configured automatically how can I find out what the path to the mountpoint is?

If your ipod is connected to your computer and you can browse the contents in Nautilus, a mountpoint has already been created for it.  Look in /media and see what that mountpoint is, then when you type the command in be sure you don't just use /media/*mountpoint* but that you use /dev/*partition_id*/media/*mountpoint*, where partition_id refers to the device id of your root partition (usually something like 'sda1').

---

### Post by tigerplug on 2008-01-10
> **thexero said:**
> my ipod is mounted automatically

/media/MyIpod

but it should appear on the desktop as soon as it is mounted

While I realize it may not be possible... I was reading through the above guide - considering trying it out with my iPod touch (Im at work at the moment with no Ubuntu machine).

.... I think that was one of the main problems with me - my iPod wont mount, altough if I can get it to do so by installing libgpod 0.6 (and creating a mount point if I have to) then it may be worth a try.

I just posted over there to ask does this work with iPod touch, waiting for response.

---

