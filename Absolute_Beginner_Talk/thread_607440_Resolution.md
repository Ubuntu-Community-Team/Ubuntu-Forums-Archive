---
title: "Resolution"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by rebel146 on 2007-11-08
I have had ubuntu for about a month. I started with fiesty and everything was running great except for my resolution. I have a widescreen envision monitor which i wanted to set to 1360x768. I didnt know how so just put off fixing it. I updated to gusty and found lots of drivers that came with it one of them being for this native resolution. I set it and reset my computer to allow it to fully load. 

My problem now is that the driver didnt work and my screen is completly scrambled. I can kind of tell i am at my log in screen only due to remembering the colors. How do i get back to a working driver/resolution and how can i test settings without comptely crippling myself. 

I dual boot and therefore it shows me prior dates of ubuntu, i have tried the other ones and have the same issue. I am not too terminal friendly yet. I only copy and paste what websites say to install stuff without actually knowing what it means. 

Any ideas for a fix? I did a couple searches on the site and other internet forums but couldnt seem to find a fix. As i said i am new to all of this so maybe there is a simple fix i am missing.

---

### Post by overdrank on 2007-11-08
> **rebel146 said:**
> I have had ubuntu for about a month. I started with fiesty and everything was running great except for my resolution. I have a widescreen envision monitor which i wanted to set to 1360x768. I didnt know how so just put off fixing it. I updated to gusty and found lots of drivers that came with it one of them being for this native resolution. I set it and reset my computer to allow it to fully load. 

My problem now is that the driver didnt work and my screen is completly scrambled. I can kind of tell i am at my log in screen only due to remembering the colors. How do i get back to a working driver/resolution and how can i test settings without comptely crippling myself. 

I dual boot and therefore it shows me prior dates of ubuntu, i have tried the other ones and have the same issue. I am not too terminal friendly yet. I only copy and paste what websites say to install stuff without actually knowing what it means. 

Any ideas for a fix? I did a couple searches on the site and other internet forums but couldnt seem to find a fix. As i said i am new to all of this so maybe there is a simple fix i am missing.

Hi and welcome, have you tried to boot into recovery mode, this is the second on the grub list usually. Login with user name and password, then use this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and then ```
reboot
``` hope this gets you back to the desktop GUI. Good luck.

---

### Post by rebel146 on 2007-11-09
Thanks i dont know what you told me to type means, but it worked perfectly!

---

### Post by overdrank on 2007-11-09
> **rebel146 said:**
> Thanks i dont know what you told me to type means, but it worked perfectly!

Great and that is the command to reconfigure you xorg and that fixed your resolution. Could you mark your thread as solved by using the thread tools. Good luck! :KS

---

### Post by TimMc on 2007-11-11
Sorry to bump this thread...

I've the same problem but to make matters worse my keyboard wont work until Ubuntu 7.10 2.6.22-14 is loaded and by that time the screen is scrambled.

I can't even access the BIOS as the keyboard is unresponsive at that stage. I've tried using different keyboards both on PS2 and USB with no luck.

The motherboard is an ASUS P5S-MX SE [http://au.asus.com/products.aspx?l1=3&l2=11&l3=502&l4=0&model=1682&modelmenu=2](http://au.asus.com/products.aspx?l1=3&l2=11&l3=502&l4=0&model=1682&modelmenu=2)

I think the onboard graphics is set to 128MB in the BIOS (SiS Mirage 3 Integrated Graphics)

I lowered the screen resolution to 1024x768 (refresh rate changed to default 80 something) and it seemed ok. I logged out and the login screen was scrambled. I logged in again and now that screen is scrambled :-(

Tim.

---

### Post by overdrank on 2007-11-11
> **TimMc said:**
> Sorry to bump this thread...

I've the same problem but to make matters worse my keyboard wont work until Ubuntu 7.10 2.6.22-14 is loaded and by that time the screen is scrambled.

I can't even access the BIOS as the keyboard is unresponsive at that stage. I've tried using different keyboards both on PS2 and USB with no luck.

The motherboard is an ASUS P5S-MX SE [http://au.asus.com/products.aspx?l1=3&l2=11&l3=502&l4=0&model=1682&modelmenu=2](http://au.asus.com/products.aspx?l1=3&l2=11&l3=502&l4=0&model=1682&modelmenu=2)

I think the onboard graphics is set to 128MB in the BIOS (SiS Mirage 3 Integrated Graphics)

I lowered the screen resolution to 1024x768 (refresh rate changed to default 80 something) and it seemed ok. I logged out and the login screen was scrambled. I logged in again and now that screen is scrambled :-(

Tim.

Hi and when you reach the login screen ( scrambled) then use the alt, ctrl, F1 and this will bring you to the command prompt. Then login with user name and password and use the command as posted before. Hope this helps. good luck!

---

