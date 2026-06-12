---
title: "ubuntu will not start up.. (again)"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by xecure on 2008-02-29
I have had this problem before where i turned on the computer and it gave me an error message. I have gotten this exact same message before and I had posted about it here: [http://ubuntuforums.org/showthread.php?t=692731]("http://ubuntuforums.org/showthread.php?t=692731") I get the exact same error message, but the only difference is that this time it is not because I pulled out a connected LCD screen but i put my laptop to hibernate  (also pulled out the charger) When I came back and hit the on button on my laptop, it started up my computer like it does when i reboot and after the Ubuntu logo screen it gave me the error message

---

### Post by Locutus_of_Borg on 2008-02-29
Did you somehow change any xorg.conf settings?



I encountered this same error ode on my wife's laptop and was able to circumvent it by setting the video driver to "vesa" in xorg.conf


boot to safe mode, if you can, and run "sudo dpkg-reconfigure -phigh xserver-xorg" and choose Vesa when the option comes up, leave everything else as is/accept proposed setting.

---

### Post by xecure on 2008-03-02
alright, i changed my back up xorg.conf file to my main one and i booted and it ran fine for 2 days. then today again i am having this smae problem. 

Why does this problem persist? Is it because i modifed the xorg.conf file?

---

