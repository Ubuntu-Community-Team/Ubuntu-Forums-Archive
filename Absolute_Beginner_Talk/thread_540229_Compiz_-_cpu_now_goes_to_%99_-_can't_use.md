---
title: "Compiz - cpu now goes to %99 - can't use"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by angelsneverdie on 2007-09-01
So I installed compiz on my laptop and it worked just great for almost a week (long enough for me to get to like it).  Then, all of a sudden, a problem happens.  whenever i run it the cpu usages spikes to 99 percent and stays there until i turn it off.  while it is like this it makes the computer virtually unusable.  

anyone have any ideas?  it had been working just great - i don't know what happened to make it not.

---

### Post by Altarbo on 2007-09-02
> **angelsneverdie said:**
> So I installed compiz on my laptop and it worked just great for almost a week (long enough for me to get to like it).  Then, all of a sudden, a problem happens.  whenever i run it the cpu usages spikes to 99 percent and stays there until i turn it off.  while it is like this it makes the computer virtually unusable.  

anyone have any ideas?  it had been working just great - i don't know what happened to make it not.Compiz normally will put the workload of drawing the screen on your graphics card.  Either your graphics card itself or the driver for it is faulty.  This is causing the workload to fall upon your cpu.  

What card do you have and what driver are you using?

---

### Post by angelsneverdie on 2007-09-03
My graphics card is:

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY (prog-if 00 [VGA])
        Subsystem: Gateway 2000 Unknown device 0400
        Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, laten

---

### Post by Altarbo on 2007-09-10
Hello,

Sorry for taking so long to reply.  I don't have internet access at my place of residence.

ATI does not have good proprietary drivers or open source drivers.  Most of the people  you will hear about running Compiz are doing so with Nvidia boxes.  I haven't used ATI cards much., so if 3D acceleration is important to you, the best advice I can give is to read this thread:
[http://ubuntuforums.org/showthread.php?t=246746](http://ubuntuforums.org/showthread.php?t=246746)

If it doesn't help you actually solve the problem, it should at least give an idea of where something has gone wrong.  If you cannot get the accelerated driver working and no one else responds to this thread, try reposting your problem with your xorg.conf and xorg.log attached.

If the accelerated driver is not important to you or you can't get it to work, try using the fbdev driver in xorg.conf.

If the problem turns out to be with your hardware (fall, heat, water, etc, damage) you can try switching to a session based around a smaller window manager (try openbox, icewm, or something similar; even though XFCE is referred to as light part of this "lightness" comes from offloading work onto the graphics card in the same way as compiz).

Finally, whenever you edit Xorg.conf always make a copy of the working configuration before you edit.  This way you can just go back to the old configuration if the new one crashes your system.  Restores can be done from the command line (no xserver) or from a Livecd.

Hope some part that helps,
Robert

---

