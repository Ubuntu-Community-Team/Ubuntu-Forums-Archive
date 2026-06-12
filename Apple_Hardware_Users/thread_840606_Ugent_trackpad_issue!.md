---
title: "Ugent trackpad issue!"
date: 2008-06-25
forum: Apple Hardware Users
---

### Post by killakyleog on 2008-06-25
Im on a first gen santa rosa intel core duo blackbook

and i installed ubuntu last night the problem was the 2 finger scrolling and such which i fixed and all then i wanted to change f12 to ctrl-click so i did and it works. but now the track pad does not. If anyone can help plz do so 

oh and 2 finger right click did not work for me i had to double tap the track pad which i didnt like i like actually putting to fingers on the track pad and clicking the mouse instead of just double tapping with 2 fingers on it.

is there ne way i could do that?


Here is a copy of my /etc/init.d/gedit

# Defaults for mouseemu initscript (/etc/init.d/mouseemu)
# These are the default values on PowerPC. On all other architectures
# middle and right click are disabled by default.
# Key codes can be found in include/linux/input.h in the kernel headers
# or by using `showkey` in a console.


MID_CLICK="-middle 125 272" # Command key + mouse click
RIGHT_CLICK="-right 29 272" # Control key + mouse click
SCROLL="-scroll 56" # Alt key + mouse movement
TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress

---

### Post by owlgorithm on 2008-06-26
Are you using a driver that is mentioned here?

[http://ubuntuforums.org/showthread.php?t=840040]("http://ubuntuforums.org/showthread.php?t=840040")

---

