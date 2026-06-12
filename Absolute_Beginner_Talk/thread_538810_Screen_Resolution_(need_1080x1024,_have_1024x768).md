---
title: "Screen Resolution (need 1080x1024, have 1024x768)"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by jordan90 on 2007-08-30
I installed Ubuntu for the first time last night, but I haven't been able to adjust the resolution. I'm an absolute noob to Linux, but I'm very familiar with Windows. I have an HP Pavilion a1514n with the stock ATI RADEON Xpress 200 video card.

I've already tried this command: "sudo dpkg-reconfigure xserver-xorg" and then I selected 1280x1024, but when I restarted my monitor came up with an error saying the screen resolution isn't supported. I had to use the recovery mode to get it back to normal.

I really want to use Linux, but I can't live with the 1224x768 resolution. Any help would be greatly appreciated.

Also, on a side note, I can't connect to the internet through my ethernet cable, which is hooked up to a router, so I'm currently using my USB wi-fi. Any ideas on why it isn't working?

Thanks!

---

### Post by JawsThemeSwimming428 on 2007-08-30
What type of graphics card? Did you try using the Screen Resolution manager under System-> Administration? 

Does your Internet connection through Ethernet work on another machine? Fill us in and hopefully we can help you get everything working!

---

### Post by jordan90 on 2007-08-30
ATI RADEON Xpress 200 video card and yes, I've tried the screen resolution manager. I already spent two hours searching the forum and trying to fix it without success.

And yes, the ethernet works on other machines. I'm wondering if I need to install a driver for it.

---

### Post by Majorix on 2007-08-30
Hmm I haven't seen that "screen resolution isn't supported" warning that often. Usually it would say that the refresh rates aren't supported. Are you sure this isn't the case by you too? If it is the case, then I would go to the monitor's website and learn what horizontal and vertical refresh rates are and enter them in advanced mode in sudo dpkg-reconfigure xserver-xorg.

---

### Post by phr0ze on 2007-08-30
The resolution should be 1280x1024. Not 1080. Thats why it isn't supported.

---

### Post by kellemes on 2007-08-30
> **phr0ze said:**
> The resolution should be 1280x1024. Not 1080. Thats why it isn't supported.

Yes, I thought there was something wrong with it.. :popcorn:

---

### Post by jordan90 on 2007-08-30
My bad, that was a typo on the forums. I've been using 1280x1024 when I try to change it. I just tried it again to make sure and I came up with the same error on my monitor.. Change the resolution 1280x1024 and 60hz.

Any other ideas?

---

### Post by jordan90 on 2007-08-30
And I'm really starting to hate Ubuntu already and I haven't even been able to use it yet. How do I get into the terminal now that my screen resolution is screwed up again? The command I was using before in recovery mode (sudo dpkg-reconfigure xserver-xorg) now goes into some kind of advanced configuration. I'm totally stuck right now with a black screen.

---

### Post by Hobo Joe on 2007-08-30
It's supposed to go into a black screen.

You need to set your resolution through that, and your refresh rates if you need too.

---

### Post by jordan90 on 2007-08-30
By blank screen I mean there is no signal to the monitor. How can you adjust settings when there is nothing to see?

And I tried reinstalling Ubuntu already but I have it dual installed with Windows XP and I don't know how to reinstall it without messing up the partitions.

---

