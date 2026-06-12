---
title: "Screen Reso Problem-i searched stuff already"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by mikkko on 2008-03-06
i searched about how to fix my 1024x768 resolution, because when i use that resolution, the screen wiggles upward, i do not know why..

i found this thread since i was using ATI Radeon 7500:
[http://ubuntuforums.org/showthread.php?t=715551](http://ubuntuforums.org/showthread.php?t=715551)

after typing
sudo apt-get install xserver-xgl

i restarted my laptop.. and when it came to the login screen, i typed my username n pass as usual, and after input, the screen went brown, and instead of loading gnome, it came back to the login screen.. so i tried using gnome failsafe, and it loaded gnome successfully... how can i fix this prob?

also, i would like to use the 1024 resolution instead of the 800x600 reso that i am using now.. how can i do this? anyone please help.. thanks

---

### Post by Kevin the Olden on 2008-03-06
I ran sudo dpkg-reconfigure xserver -xorg to get 1280x1024 because I couldn't do it via preferences. Worked for me, and I'm stupid.

---

### Post by kesman on 2008-03-06
there's NO space in xserver-xorg

---

### Post by mikkko on 2008-03-06
i tried that already but its still the same, the screen still wiggles in the 1024 resolution..

and when i login while not using failsafe gnome, after i type m username and pass, it still goes back to the login screen instead of loading gnome.. :(

---

### Post by mikkko on 2008-03-07
i switched to kubuntu feisty coz i cant seem to resolve my ubuntu 1024 resolution.. ^_^

---

### Post by sboden on 2008-03-07
If you have an ATI (as the original poster) or an NVIDEA card, go to [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) , download the .deb file to your desktop. Double click it, install Envy/EnvyNg and run it via the menu. 

It will do its magic and install the drivers, ... for you.

Regards,
Sven

---

