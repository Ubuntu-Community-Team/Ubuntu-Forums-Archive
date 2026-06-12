---
title: "Wrong video drivers - quick fix"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Smaug067 on 2007-01-09
I was customizing my installation using Ubuntu_Demon's [Guide](http://www.ubuntuforums.org/showthread.php?t=186792). Not paying attention, I installed the wrong video driver. Upon reboot, I received the "DOS screen" telling me that X would not work (sorry, I don't remember the exact message). Not wanting to re-install the whole OS, I used the live CD to boot up, which allowed me to get on the Net and find the correct commands. I wrote these down and re-booted. After hitting enter repeatedly to get through all of the "DOS screen" style messages, I was able to get to the command line. I sudo'd the correct commands to get the right drivers, and voila! She's a-working again! Just a lesson I learned to keep in mind that the live CD is always available to help us noob's find solutions without having to do a complete wipe and re-install. Anyway, I hope this benefits somebody else in the future.

---

### Post by Ben Sprinkle on 2007-01-09
```

sudo dpkg-reconfigure xserver-xorg

```
When you get to the video driver screen select VESA for default or find your previous driver. Then reboot.

---

