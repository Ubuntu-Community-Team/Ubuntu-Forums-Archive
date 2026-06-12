---
title: "I need to pause my screen during boot"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by cforput on 2008-01-26
I am getting an error on my video driver when I boot but it scrolls by too fast to read the entire error. How do I pause the screen during boot so I can read it. I have tried the pause key but that doesn't work.

---

### Post by mortsahl on 2008-01-26
I haven't tried it but this should work (it works in bash) ...

ctrl-s to pause, ctrl-q to resume

---

### Post by James_mtl on 2008-01-26
Are you able to use the computer anyway or does the error completly block you from using it ?

also you can try using one of the tty ( press ctrl-alt-F1 ) it should bring you to tty1

input you username and password 

use the dmesg comand to look at the booting messages:

dmesg | less

use the up and down arrows to navigate through the messages list and press q to exit

ctrl-alt-F7 will bring you back to the graphical interface

if you are able to boot you can do the same in a terminal window.

Hope  this helps.

---

### Post by cforput on 2008-01-26
Thanks for the replys. Funny, the control-s doesn't pause when I need it. It pauses other places though. The dmesg command gives me a bunch of stuff but I don't see the error message in it. Originally I thought the error message had something to do with my video card because I couldn't get it working but that is fixed now. Maybe I just won't worry about it.

Appreciate the help.

---

### Post by Pevichaey5 on 2008-01-26
there is a button called 'Pause' press that for when the bios screen is up to pause the screen, but if it is while linux is running, just the print screen button should work

---

