---
title: "Installing 8.10 on PPC G4 (ive read the known issues)"
date: 2009-02-23
forum: Apple Hardware Users
---

### Post by ForMar on 2009-02-23
So I recently tried to install ubuntu 8.10 PPC on my old iBook G4 but for some reason I just get a blank screen when it should boot. I have looked through the known issues and did what was instructed there. 
```
modify /etc/initramfs-tools/modules

ide-disk

and run

sudo update-initramfs -u

modify /etc/yaboot.conf adding 

video=radeonfb:1024x768"

 run

sudo ybin -v


```

but none of it worked for me. I check and change the clock to something not in the 1900's but still nothing. I'm stumped and have no idea what to do.
Also under video I even change the resolution to "800x600" but that also did nothing for me. 

I appreciate your time and any help you can give!

---

### Post by mkvnmtr on 2009-02-23
I have never tried to install 8.10 on my Ibook but 8.04  goes on pretty easy. I only have to press the tab key and type live-nosplash-powerpc. Then I found that it upgrades to 8.10 with no problems. You might like staying with 8.04 and not upgrading. It seems to be more stable on my Ibook. I have thought about going back to 8.04 but haven't done it. but then I have thought about installing 9.04 also. It would not boot for me. Probably a good thing.

---

