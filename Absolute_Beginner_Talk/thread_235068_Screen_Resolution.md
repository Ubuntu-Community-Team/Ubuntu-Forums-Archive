---
title: "Screen Resolution"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by angelnas on 2006-08-12
Hi Everyone  I am new to unbuntu and am running this operating system in dual mode..ie unbuntu and windows xp.

Anyway the problem I have is the screen resolution is permanently set to 640x480 and no other value is listed under System, Preferences,screen resolution.
 
I have a dell moniter of 15"tft.  I am unable to adjust this as everything apears large on the sceen and means moving the window box to see the bottom of the page.

Any solution to this.  Many thanks

---

### Post by calvinthomas on 2006-08-12
Yes, there is a solution, either go to a terminal or the command prompt (ctrl, alt, F1) and type:

sudo dpkg-reconfigure xserver-xorg

Select the graphics card driver you want to use and then leave everything the same until you get to monitor configuration, in there you'll be able to select any resolutions you want and Ubuntu will use the highest one you choose by default (Use space bar to select them)

HTH

Calv

---

### Post by UltraMathMan on 2006-08-12
Guide I used to fix my resolution / reconfigure xserver

[http://www.ubuntuforums.org/showthread.php?t=83973&highlight=adding+resolutions]("http://www.ubuntuforums.org/showthread.php?t=83973&highlight=adding+resolutions")

-Hope this helps :)

---

### Post by angelnas on 2006-08-12
Great worked a treat and thanks for the 2 posters who responded helped me out alot.

---

### Post by groberts1980 on 2006-08-12
> **calvinthomas said:**
> Yes, there is a solution, either go to a terminal or the command prompt (ctrl, alt, F1) and type:

sudo dpkg-reconfigure xserver-xorg

Select the graphics card driver you want to use and then leave everything the same until you get to monitor configuration, in there you'll be able to select any resolutions you want and Ubuntu will use the highest one you choose by default (Use space bar to select them)

HTH

Calv

I'm having the same problem with screen resolutions. I have a Dell Inspriron E1705 with the Intel integrated graphics chip. Seems like every post I run across references either an nVidia or ATI chipset.

Anyway, I ran the command you mentioned and went through the xserver config. I selected 1440x900 (the resolution I run in XP), but when it exits the config, nothing is changed. I still cannot select a different resolution. Only options it gives me are 1024x786, 800x600, and 640x480.

Also, when its going through the xserver config and asks which driver I want to use, I don't see an option for my chip. I have the Mobile Intel 945GM Express Chipset. I see i128, i740, and i810. Shouldn't i945 be there?

Am I supposed to do anything more once the xserver config exits?

---

### Post by agurk on 2006-08-12
> I have the Mobile Intel 945GM Express Chipset.
I have that one too, you should use the i810 driver. Don't ask me why or how to configure xorg though, those are just two of them infinite number of Linux mysteries...

---

### Post by groberts1980 on 2006-08-12
After rebooting, it gives me 1440x900 as an option for screen resolution. Thanks to the above posters!

I just installed Ubuntu on my laptop today, and it'll take me a while to learn the ropes!

---

