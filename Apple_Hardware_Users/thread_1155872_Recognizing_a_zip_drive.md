---
title: "Recognizing a zip drive"
date: 2009-05-11
forum: Apple Hardware Users
---

### Post by Benboom on 2009-05-11
I searched the forum for zip and Iomega and didn't get any hits so I'm assuming this may be problematic. I'd like to know if my old G4 Sawtooth (AGP) internal zip drive (ATA bus) can be seen by Ubuntu. The Synaptic installer app doesn't show me anything in the way of drivers (at least not that I recognize) when I search for Iomega or zip (although that last one gives you a lot of hits for unzip-type things).

The system recognizes USB flash drives and all of my normal hard disk partitions of each OS, so it just seems like it should be possible. It would help in moving stuff from the other Mac to the Ubuntu machine.

Thanks.

---

### Post by stream303 on 2009-05-11
Wow - I'm not sure if zip-drive support is even enabled in the kernel, even as a module these days.  You may have to recompile the kernel to get that.

Check out this for more info:
[http://www.faqs.org/docs/Linux-mini/ZIP-Drive.html](http://www.faqs.org/docs/Linux-mini/ZIP-Drive.html)

I used to use a parallel-port zip drive back in my slackware days. :)

From what I remember back then, I had to treat it as a hard drive - that is when booting, be sure to have the media in the drive first.  And before removing the media, you need to unmount it, or just shut down the system and then remove the media.  Although these days with hotplugging, who knows? :)

You may have to mount it manually, and I don't know if Apple back then used a different filesystem, or the usual msdos format:

```
sudo mount -t msdos /dev/sdf4  /mnt
```

(perhaps try vfat instead of msdos)

(You'll have to look in your dmesg output to see what the device is, if it is recognized by the kernel at all)

The other little trick was that I had to mount at partition #4, rather than assume partition #1 (ie /dev/sdf4 rather than /dev/sdf1), although this may have been specific to the parallel port drive.  Again, the output of dmesg (with media in the drive first!) may indicate something different than /dev/sdf.

Man, what a blast from the past...

---

### Post by Benboom on 2009-05-11
Ay, carumba! I had no idea...

---

