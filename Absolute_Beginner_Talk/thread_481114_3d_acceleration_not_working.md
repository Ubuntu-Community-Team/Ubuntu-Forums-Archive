---
title: "3d acceleration not working"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Exershio on 2007-06-22
Okay, here's the deal. I'm trying to play WoW through Wine (I'm able to play WoW just fine on my windows partition), but when I start it up in Linux, it says "3d acceleration not found" or something like that. I'm using onboard intel graphics with the Intel (not i810) driver installed.

How do I get 3d acceleration working?

---

### Post by dimis2410 on 2007-06-22
i would tell you to install the  game with wine or better with CEDEGA or Crossover. 
to find out if your 3d acceleration is ok ....open the Terminal and type "glxgears"

And finally search ! Google it!

---

### Post by overdrank on 2007-06-22
> **Exershio said:**
> Okay, here's the deal. I'm trying to play WoW through Wine (I'm able to play WoW just fine on my windows partition), but when I start it up in Linux, it says "3d acceleration not found" or something like that. I'm using onboard intel graphics with the Intel (not i810) driver installed.

How do I get 3d acceleration working?

Hi if you are not using the 810 driver then which one are you using. I have the onboard 945 chipset with the 810 driver and 3d works great.:KS

---

### Post by Exershio on 2007-06-22
> **overdrank said:**
> Hi if you are not using the 810 driver then which one are you using. I have the onboard 945 chipset with the 810 driver and 3d works great.:KS

I'm using the driver that came with running this command:

sudo apt-get install xserver-xorg-video-intel

---

### Post by overdrank on 2007-06-22
> **Exershio said:**
> I'm using the driver that came with running this command:

sudo apt-get install xserver-xorg-video-intel

Ok I understand that you tried to install the driver with that command but that does not mean that it was install and configure in the xorg. If you can run the command
 gksudo gedit /etc/X11/xorg.conf  it will open the xorg and you can verify which drive is under device.

---

### Post by Exershio on 2007-06-22
i ran dpkg-reconfigure xserver-xorg to make it my device.

and I tried installing the i810 driver and it works fine and I can play the game, however, now my resolution settings aren't working anymore. I like to use 1152x864, but it only works with that Intel driver I had before

---

