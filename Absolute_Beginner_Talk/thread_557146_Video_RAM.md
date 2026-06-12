---
title: "Video RAM"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Sarteck on 2007-09-22
Dear Smart People,

Er, how do I know how much Video RAM I have?  I have a nVidia GeForce 6150SE nForce 430 (which was a pain in the neck to get running on Kubuntu, let me tell you), and it's Integrated, if that means anything...

---

### Post by forestpixie on 2007-09-22
nvidia-settings tells me - do this in a terminal

```
nvidia-settings
```

I'm sure there's a way to do it terminal, I don't know it though, shall wait for another answer to see :)

---

### Post by overdrank on 2007-09-22
> **Sarteck said:**
> Dear Smart People,

Er, how do I know how much Video RAM I have?  I have a nVidia GeForce 6150SE nForce 430 (which was a pain in the neck to get running on Kubuntu, let me tell you), and it's Integrated, if that means anything...

HI with it being a onboard graphics it will largely pertain to how much memory is  on the system be cause it shared the memory. In your bios there should be a option to increase the amount of shared memory or it is automatic when more memory is added to the system.

---

### Post by xtknight on 2007-09-22
There's no way for a program to look it up other than a database AFAIK.

So, you have to rely on some specific driver to tell you.  You should be using "nv" or "vesa" for that card, by default.  So, you can look here:

This, from [USALUG]("http://usalug.org/phpBB2/viewtopic.php?p=97189&sid=6a4b3fb05e68d3c6c332e132b12f620a").  "grep -i ram /var/log/Xorg.0.log; grep -i mem /var/log/Xorg.0.log"
(Update: this cmd works with "nvidia" also)

This might give you a hint.  Otherwise, if you're using "nvidia" driver (you would probably know it), simply use "gksu nvidia-settings".  If you installed anything using a "restricted driver manager", you're using nvidia.

Mine says this:
(--) NVIDIA(0): Memory: 262144 kBytes

To get megabytes divide it by 1024, and in this case you get 256 MB.

---

### Post by Sarteck on 2007-09-22
Oh, hey, thank you all! ^_^  I feel sheepish--I was thinking the Video RAM was a set thing, and I didn't even think to look in nvidia-settings.

Mine's set at 256MB, then.  Thanks again.

---

