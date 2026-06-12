---
title: "window manger/desktop resolution fragged after lm-sensor install"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by wadesmart on 2007-10-03
Long story short, I totally screwed my desktop.

I decided today that I wanted to know the cpu temp so after some research I installed lm-sensors and ran the detect script. It installed in the /etc/modules i2c-i801, i2c-i810, lm85, and eeprom modules to start up. I installed gdesklets and then started the cpu temp monitor. It said there were no lm-sensors found so I restarted. 

Apparently that was a mistake. 

I went from 1600x1200 resolution to 600 x 400. I tried to restore it but, there are no options. 

I started the terminal and was running fetchmail and then I clicked on the "show-all" button on the bottom left and it said, "no window manger found." 

I really could use some help. 

Wade

---

### Post by wadesmart on 2007-10-03
I found a thread about reconfiguring the xserver so I ran: 
sudo dpkg-reconfigure xserver-xorg 
and that seemed to fix my problem. After reboot the resolution was back to normal. But when I logged in Im presented with a blank white desktop. I waited for a few minutes hoping something was going to happen but, nothing. There is nothing to click on and right clicking does nothing. 

However, if I hold ctl-tab I am presented with a square in the middle of the screen. This doesnt do anything though. You cant click it. 

Im really stuck now.

---

### Post by Hospadar on 2007-10-03
erm, sounds like you xserver got pooped on =|  I really can't say i have the foggiest idea how it happened.  but try taking a look at your x-configuration```
sudo dpkg-reconfigure xserver-xorg
``` and select some extra resolutions when you get to that part of the dialog (you can just default through most of the menus.

also, from the command line try doing a ```
 sudo /etc/init.d/gdm restart
```  that's how the xserver and gnome are started up.

---

### Post by wadesmart on 2007-10-03
How can I do that now that I have no desktop to click on? I read that I could hold ctrl+alt + bk space at boot to get the terminal but that hasnt worked.

---

### Post by wadesmart on 2007-10-03
I found my 7.04 install cd and used it to boot up. It too started with 640x480 and cannot be changed. 

Im looking at the xorg.conf for my hard drive and it has the card data: Intel 82845G/GL card and correctly has my monitor as an Envision EFT monitor. It has all the correct resolutions that my monitor can handle but.....

---

