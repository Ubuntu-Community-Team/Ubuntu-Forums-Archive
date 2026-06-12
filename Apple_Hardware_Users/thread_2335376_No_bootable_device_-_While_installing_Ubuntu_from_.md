---
title: "No bootable device - While installing Ubuntu from USB stick on Mac"
date: 2016-08-28
forum: Apple Hardware Users
---

### Post by ikon_ on 2016-08-28
I want to dual boot linux and osx on my mac.

I followed [this thread]("https://ubuntuforums.org/showthread.php?t=2174630") to create a bootable USB stick with Ubuntu on it. I've followed the exact instructions and everything worked fine but when I try to select my USB stick to run in rEFind I get this error

```
No bootable device -- insert boot disk and press any key
```

I've done this a bunch of times and I'm at a loss on what to try next. Any help is really appreciated.

---

### Post by howefield on 2016-08-28
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by theethee on 2016-09-09
I mostly create my bootsticks, as well for my macbook, with unetbootin. 
As far as I figured it out, it depends on the capability of the distro you're using of booting on an EFI system. 
So, when I had the same Error as you have now, I made a stick with a Distro where it worked (I think the Mint ISO and the latest Ubuntu ISO just do that automaticly with unetbootin)
and afterwards copied the EFI folder and the Grub.cfg from that stick on the one I wanted to boot. Normaly it worked like that but sometimes you have to adjust the grub.cfg so that everything points at the right directories on your stick.

Good luck!

---

