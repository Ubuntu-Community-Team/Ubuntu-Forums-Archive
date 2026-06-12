---
title: "Gutsy laptop resolution haywire after dual monitor"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by readingitsideways on 2007-12-12
I have a Dell Inspiron 1520 with 1440/900 res screen and an Nvidia card.

I tried to plug a projector in to watch a DVD and went to the monitor set up and set the second monitor. Now my resolution is completely messed up, and ubuntu (gutsy) won't autodetect my laptop screen. It usually reverts to a very low res.

How do I set it back?

Thanks

Duncan

---

### Post by pHreaksYcle on 2007-12-12
System->Administration->Screens and Graphics
You can reset your resolution there and also configure a second display correctly. Hope this helps.
EDIT: I just read you said monitor set-up. Are you talking about what I just pointed out or something different?

---

### Post by Valok on 2007-12-12
When you go into your screen resolution options tab is it missing the option that you would like to set it to?  Or is it just not allowing you to actually select and use the option you want.

---

### Post by readingitsideways on 2007-12-12
Hi

I restored my resolution be restoring a backup of xorg.conf.

But, I cant set a second monitor in Preferences>Admin>Monitors without messing up my display.

When I log in again I'm at a low res but can pan around a larger desktop... How does one do this dual monitor stuff?

Thanks


Duncan

---

### Post by readingitsideways on 2007-12-12
I should just be clear, I don't particularly want dual monitors, I just want to be able to use a projector with my laptop. On my HP I just press <fn>+F4, but this Inspiron doesn't have that option. There/s a Fn function on F8 called CRT/LCD, but it doesn't seem to do anything...

Thanks again

Duncan

---

### Post by Ardrias on 2007-12-12
I use the restricted nvidia drivers and run 'nvidia-settings' whenever I need to hook up the laptop to a projector. Not too much of a problem really.

---

### Post by PhonicsMonkey on 2007-12-15
I had a problem just like that with my dell latitude d620 with nvidia driver. I could pan and use the desktop but the resolution was the same. For dual monitor use I found this page to be very informative.
[http://ubuntuforums.org/showthread.php?t=582739&highlight=dual+monitors&page=2](http://ubuntuforums.org/showthread.php?t=582739&highlight=dual+monitors&page=2)
Hope this helps.

---

### Post by BenP116 on 2007-12-16
I was having a similar problem.  I have an acer 5050 laptop with ati radeon 1100.  Also using a restricted driver. I can't get it to give me my 1280 x 800 on my laptop at the same time give a diff resolution for the tv screen or projector. 

Anyway try this, it worked for me

.(I found it also changed the name of the drivers and monitor so maybe check that too...) 

To get my resolution back, go to restricted drivers manager.  
Uncheck the video driver.
Restart.
Check the box for the restricted driver again for vid card.
Restart again. 

After that everything went back to normal.

:guitar:

---

