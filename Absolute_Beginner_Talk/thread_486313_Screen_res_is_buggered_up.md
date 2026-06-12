---
title: "Screen res is buggered up"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Gleep on 2007-06-27
I followed the steps in the thread here [http://ubuntuforums.org/showthread.php?t=452596](http://ubuntuforums.org/showthread.php?t=452596)
However I have an ATI card, not nvidia. Anyway I did as visionary posted, except that when I rebooted the first time I only had my house, so I reconfigured my xorg.conf in recovery mode to get the ATI driver.

Great, so now I can see things again, but my screen res is confusing me. I currently have it on 1024x768, because it's the highest that I can clearly read things in. It's absolutely massive though, and things like my gdesklets are off the screen. So I reconfigured the xorg.conf again, and added a few more options for the screen resolution... but when I select them, all text and pictures are horribly distorted, while the size is normal... I'm not sure what to do about this.

All I wanted to do was stop having to log in a million times but it seems I've just created another problem.

Any help would be appreciated.

---

### Post by DSn0wMan on 2007-06-27
Have you tried changing your resolution from system > preferences menu?

---

### Post by Gleep on 2007-06-27
Yeah, The size is right, on the screen but the fonts are really ugly and scrunchy... if that's a way of describing it.

---

### Post by DSn0wMan on 2007-06-27
I have a wide screen monitor, so I have to use 1280 x 800. If I use 1024 x 768 everything looks weird and stretched.

---

### Post by mtbsoft on 2007-06-28
Don't know if it'll help but  I've just installed 7.04 on my new 9400 which has an ATI1400 (1920x1200 widescreen).  I had all sorts of graphics issues but eventually found the following thread which worked perfectly for me.

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

The available resolutions are all the usual 4:3 type (640x480, 800x600, 1024x768...) but it includes my 1940x1200 as well.  Maybe it'll give you the ability to set the res. as you want without the distortion.

---

