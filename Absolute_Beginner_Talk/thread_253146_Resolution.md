---
title: "Resolution"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by Devile on 2006-09-07
Windows crashed (go figure) so i just put ubuntu on it instead...  anyways, how do i get my widscreen resolution back....???  I odn't like this 1024X768 when it should be 1280X800 or something like that... Please help

---

### Post by halitech on 2006-09-07
if you go to

System - Preferences - Screen Resolution

do you have anything higher then 1024x768?

---

### Post by orb9220 on 2006-09-07
Open terminal and copy and paste command below:

sudo dpkg-reconfigure xserver-xorg

And select which res's you want

---

### Post by Devile on 2006-09-07
matt@matt-laptop:~$ sudo 915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.2

ATI chipset detected.  915resolution only works with Intel 800/900 series graphic chipsets.

Oh an no it doesn't go any higher than 1024 x 768

---

### Post by halitech on 2006-09-07
if you run the reconfigure command that orb posted, it should allow you to select higher resolutions and then it should show them in the screen resolution page. I have the same chip but I only wanted 1024x768 so I've never tried to get higher

---

### Post by Devile on 2006-09-07
Ok i did that and it wants all kinds of information on my video card... so what do i do there... i don't know how to get the info...

---

### Post by Devile on 2006-09-07
well apapernlty i'm impation, i just kept hitting enter until it jsut let me change the resolution....  so i'm rebooting now... i'lll et you know

---

### Post by halitech on 2006-09-07
selecting the defaults for everything except resolutions you want should be fine. hopefully this works for you

---

### Post by Devile on 2006-09-08
wel it didn't crashed the graphics module and didn't work, so i reinstalled ubuntu...  i hope someone will read this...  because i want my higher resolution but i can't figure it out...

---

### Post by UltraMathMan on 2006-09-08
take a look at this and see if it helps

[http://www.ubuntuforums.org/showthread.php?t=218610](http://www.ubuntuforums.org/showthread.php?t=218610)

-Hope this helps :)

---

