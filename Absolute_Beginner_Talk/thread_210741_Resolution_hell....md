---
title: "Resolution hell..."
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by Goone on 2006-07-07
HELP!
SOMEONE!
I have an Acer Travelmate 521iT Laptop. I am running Edubuntu 6. All is cool but for one problem. The resolution is wrong! Everything is displayed too big! Sometimes I cannot get to important buttons located at the bottom of a program because they are'nt visible! I can only display 800+600 or 640+480. I have tried 915resolution,(855resolution) but this does not work with the Acer's ATI hardware. I have followed all the steps found at the FixVideoResolutionHowTo page in the community section. Did'nt help.
I am at a dead end.
........

---

### Post by tseliot on 2006-07-07
sudo dpkg-reconfigure xserver-xorg

then select the right resolution (with your SPACEBAR) when it asks you. Press ENTER whenever you don't know the answer to the other questions.

Then log out and press CTRL+ALT+Backspace and log back in

---

### Post by Goone on 2006-07-07
Thanks for the quick reply!
I have already tried detecting the video hardware as you suggested, but tried again anyway. When i log back in, as directed. it's as if i never did anything!
No changes!
No new resolutions to choose.
I have also tried altering the xorg.conf file, but i get the same response. 
Nothing!

---

### Post by Jagot on 2006-07-07
915/855resolution are for Intel onboard graphics.  Installing your graphics drivers may help.  Assuming from your post that it's an ATI card so have a look here:

[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

---

### Post by richbarna on 2006-07-07
Can you post a copy of your xorg config ?

> gksudo gedit /etc/X11/xorg.conf

---

### Post by Kobalt on 2006-07-07
Did you chose the resolutions you wanted, as tseliot told you, after you tyed sudo dpkg-reconfigure xserver-xorg ? 
After that, dont forget to press CTRL+ALT+Backspace or nothing will happen...

---

