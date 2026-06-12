---
title: "Cannot detect video hardware"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by Shadowfang36 on 2008-03-12
I just did a clean install of Gusty x64 with the alternate CD. After reboot I got a screen that said "Ubuntu cannot detect your graphical hardware" and I get the option to reconfigure.

So I select LCD Panel 1650x1050 and set the graphics drivers as NVIDIA - GeForce 8 series (I am using an 8800 GTS 512 G92)

After logging in I still cannot get out of low graphics mode.

I tried reconfiguring the xserver with "sudo dpkg-reconfigure xserver-xorg" but after re-doing the whole process I still get no results.

Any help would be greatly appreciated. I am brand new to Ubuntu and Linux.

---

### Post by Rocket2DMn on 2008-03-12
Have you tried setting up the Nvidia restricted drivers for your nvidia card from System->Administration->Restricted Drivers Manager ?

---

### Post by Shadowfang36 on 2008-03-12
Sorry I couldnt respond sooner.

When I open the Driver Manager I get the message "Your hardware does not need any restricted drivers"

Im currently using the vesa drivers, and when I try to switch to the nvidia drivers it doesnt change. Also I set my screen res and still only get 800x600

---

### Post by Furat on 2008-03-12
Check this 

[http://ubuntuforums.org/showthread.php?t=665018](http://ubuntuforums.org/showthread.php?t=665018)

---

### Post by Shadowfang36 on 2008-03-12
After some digging I downloaded Envy and it worked perfectly. Have all the screen effects and I'm at my native res. Thanks for the help.

---

