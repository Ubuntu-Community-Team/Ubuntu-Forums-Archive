---
title: "Only Ubuntu sees my HD"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Tiekyl on 2007-06-30
I'm a decently new linux user, mainly beacuse I've been trying to do installs for the past year and nothing sees my hard drive. Even on windows, I can't partition it, and its always asking me if i want to "safely remove" my hard drive. Magically, when I put in the ubuntu disk that my brother suggested, it partitioned and installed just fine.  I went ahead and ignored it until I started working on building a DSL live CD for my friend. DSL doesn't see my hard drive (or my network card, but thats a different matter). It reminded me that I can't even attempt any other distributions. 

I don't even know where to start in diagnosing this problem. I've attempted a couple clean windows installs in the past, but they just felt weird, like I couldn't just erase the hard drive. I have a HD160JJ from samsung, FWIW. Are there any suggestions out there for where I might be able to start to see whats going on? A way to completely reset it? Or..should I just get a spare HD and use that?

---

### Post by x1a4 on 2007-06-30
Try the [Ultimate Boot CD](http://www.ultimatebootcd.com/).  It's a bootable-CD containing lots of good diagnostic tools.

---

### Post by Tiekyl on 2007-06-30
Thanks, I'm downloading it right now. *crosses fingers*

---

### Post by smoker on 2007-06-30
there are a couple of samsung hard drive apps on the UBCD, which is an excellent recommedation from x1a4, i would also have a look at your bios, and ensure that the hard drive is showing there correctly,

best of luck

---

### Post by Tiekyl on 2007-06-30
Kay...an update on the problem...

I got Ultimate Boot Disk working, booted into it and ran a couple diagnostic checks...nothing found anything wrong with my hard drive. 

I had a suggestion for a low level format, but that sounds very scary. Does anyone have any idea where I could look further to figure out whats going on? Why does ubuntu recognize it and nothing else? *sigh* Should I just take it in to a professional? (Or buy a new drive)\

--Edit-- I have tried to do the research on this, I just really have no idea where to look.

---

### Post by zek725 on 2007-07-01
> **Tiekyl said:**
> Kay...an update on the problem...

I got Ultimate Boot Disk working, booted into it and ran a couple diagnostic checks...nothing found anything wrong with my hard drive. 

I had a suggestion for a low level format, but that sounds very scary. Does anyone have any idea where I could look further to figure out whats going on? Why does ubuntu recognize it and nothing else? *sigh* Should I just take it in to a professional? (Or buy a new drive)\

--Edit-- I have tried to do the research on this, I just really have no idea where to look.

I've had the same experience when I FAT32-partitioned my HDD from Ubuntu. I just repartitioned that FAT32 drive from the Ultimate Boot CD. I do not know much of the EXT3 filesystem Ubuntu uses but I think DSL should read it too.

---

