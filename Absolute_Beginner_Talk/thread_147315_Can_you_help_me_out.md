---
title: "Can you help me out?"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by MintMintMint on 2006-03-19
Req help. I just installed Ubuntu on my other comp, and it's fully installed and all. As soon as i start it though, my screen is full of this.. red and white gibberish. I dont know if its because it doesn't support my video card or something, but does anyone know how to fix it? I tried IRC, but no one will reply. :< For referance, pt800ce-a motherboard, Nvidia Geforce 6600GT video card. 1gig memory pc3200. That's all i remember offhand.

---

### Post by dermotti on 2006-03-19
Can you get to commmand line?

if not try cntrl-alt-f3

once you are logged in type 

sudo dpkg-reconfigure xserver-xorg

when it asks you for  a driver chose "vesa"

---

### Post by Blunts on 2006-03-20
How to load NVIDIA Settings in the background on GNOME Startup

    * Read #General Notes
[http://easylinux.info/wiki/Ubuntu#General_Notes](http://easylinux.info/wiki/Ubuntu#General_Notes)
    * Read #How to install Graphics Driver (NVIDIA) 
[http://easylinux.info/wiki/Ubuntu#How_to_load_NVIDIA_Settings_in_the_background_on_GNOME_Startup](http://easylinux.info/wiki/Ubuntu#How_to_load_NVIDIA_Settings_in_the_background_on_GNOME_Startup)
   
 * System -> Preferences -> Sessions
    * Click on the Startup Programs tab
    * Click on +ADD
    * Enter this line in the Startup Command field 

nvidia-settings --load-config-only

---

### Post by r4ik on 2006-03-20
You could also have a look at this,

[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074),

Its all about Nvidia.

---

