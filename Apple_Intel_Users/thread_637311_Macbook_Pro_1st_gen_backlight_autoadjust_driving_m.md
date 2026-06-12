---
title: "Macbook Pro 1st gen backlight autoadjust driving me crazy"
date: 2007-12-10
forum: Apple Intel Users
---

### Post by cipher999 on 2007-12-10
I have a quite irritating problem with my MacBook Pro 1st gen running Gutsy.

When the laptop is running with the battery, the backlight luminosity keeps readjusting itself to a too low level, and I have to periodically press the F2 button to have it to one more convenient level for my eyes. It happens around every 30 secs.

It was OK in Feisty. It's perfectly fine when the laptop is charging.

Please, any hint ?

---

### Post by Rog-Mahal on 2007-12-11
You might want to check your power management settings for when you are running on battery power. (Check System->Preferences->Power Management). Adjust the Display settings under On Battery Power to see if that will help.

---

### Post by WaySensei on 2007-12-17
I have this problem too! The display on my Macbook Pro 1st gen also dims to the lowest brightness level after a few seconds of being idle on battery power. I don't believe there is a fix from the Power Management settings. Can anybody help with this please, it is extremely annoying!

---

### Post by Romu on 2007-12-20
Same for me on a Macbook Pro 2G (Core 2 Duo + ATI). I was hoping to find a fix here but it doesn't seem to be one :confused:

---

### Post by Romu on 2007-12-20
I've just created a bug report on launchpad:
[https://bugs.launchpad.net/ubuntu/+bug/177654]("https://bugs.launchpad.net/ubuntu/+bug/177654")

---

### Post by nick_ed on 2008-02-15
As Rog-Mahal said, it's in the Power Settings.(System > Preferences > Power Settings). Go to "On BAttery" tab. Adjust "Dim display to:" as desired, I use about 10%

---

### Post by sjatkins on 2008-05-09
> **nick_ed said:**
> As Rog-Mahal said, it's in the Power Settings.(System > Preferences > Power Settings). Go to "On BAttery" tab. Adjust "Dim display to:" as desired, I use about 10%

No.  This happens to me on a Core Duo Macbook Pro with the power cord plugged in!   It happens and cannot be adjust out of on suspend/resume even while charging.   Very distressing.  Basically not having suspend / resume dependable is a non-starter for me.

---

### Post by sjatkins on 2008-05-09
> **sjatkins said:**
> No.  This happens to me on a Core Duo Macbook Pro with the power cord plugged in!   It happens and cannot be adjust out of on suspend/resume even while charging.   Very distressing.  Basically not having suspend / resume dependable is a non-starter for me.

Interesting.  What is happening is that F1 & F2 stop working after suspend!  So the darkening cannot be adjusted out of without reboot and it eventually goes completely black.

---

### Post by RubyBuntu on 2008-05-10
Hey, iv had the same issue but this entry seems to have solved it:
[http://ubuntuforums.org/showthread.php?t=594086](http://ubuntuforums.org/showthread.php?t=594086)
(disabling backlight via gconf)
In addition id really recommend installing pommed.

---

