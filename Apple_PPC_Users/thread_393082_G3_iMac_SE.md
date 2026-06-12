---
title: "G3 iMac SE"
date: 2007-03-25
forum: Apple PPC Users
---

### Post by manofsteel on 2007-03-25
I have a G3 iMac running OSX 10.4.9 and would like get Ubuntu LTS running, i can get it to where i can hear the boot up chimes, but then the screen goes black, and nothing. Ive tried all the diff options by hitting tab and thats as far as i can get.

---

### Post by ZoiaGuyver on 2007-03-25
Theres a known problem with the xorg.conf on the G3's not detecting the monitors  for the iMac's.

If you allow it to boot and go to the black screen wait a min or so and hit "ctrl-alt-F1" that should take you to a terminal, from there type "sudo nano /etc/X11/xorg.conf" (without the quotes) and in the file look for the Display section. 

In there look for the Vert sync and Horizontal sync. Change those values to 58-62 for horizsync and 75-117 for the vert sync also up a little from this look in the modules section and put a # infront of DRI. After this exit nano using "ctrl-o" to write the file and "ctrl-x" to exit.

Then at the command prompt type "sudo killall -HUP gdm" (again without the quotes) this should allow you to get to a desktop and log in.

Then if you look through these forums there are plenty of threads about how to enable DRI on the iMac G3's 

Hope this helps and you can enjoy your Ubuntu experience :D

---

### Post by manofsteel on 2007-03-25
:)  thanks a lot! I'll try this when i get home!

---

