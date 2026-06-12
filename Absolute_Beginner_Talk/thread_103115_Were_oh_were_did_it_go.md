---
title: "Were oh were did it go?"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by Micro Rotors on 2005-12-13
I used Synaptics and got a program along with the goodies for it (gEDA) a CAD program, and it doesnt show up in the Applications window. Were oh were did it go? :confused:

---

### Post by Chayak on 2005-12-13
I had a similar problem when I installed FreeNX, it showed as installed but wasn't in the menu anywhere despite telling me when it was there when I edited the menus.  I got fed up and did a ctrl-alt-backspace.  When I logged back in it was there.  If someone knows a better way to fix this, I'd love to hear it.

---

### Post by kori.mendocino on 2005-12-13
the simpler way to do this is to open up a terminal, and in it, issuing a $killall gnome-panel

---

### Post by Micro Rotors on 2005-12-13
Last night I installed some Linux Gazettes issues and I have yet to find them. I even do a file search in File System and nothing shows up. Even when I restart the computer. 

I think it's the Gate's Gremlins.

---

### Post by kori.mendocino on 2005-12-13
you can find them under /usr/share/doc/lg

---

### Post by maruchan on 2005-12-13
I did the same thing with the Linux Gazette. "Where are they and what format are they in?" Unfortunately I never got past the first question either.

---

### Post by kori.mendocino on 2005-12-13
about the Linux Gazette, i'll second myself - you can find them under /usr/share/doc/lg. they're .html. have fun

---

### Post by Micro Rotors on 2005-12-13
Thanks kori.mendocino

Ok I found the gazettes, but were the heck is the application gEDA that I got and installed with Synaptic?

---

### Post by janrinok on 2005-12-13
Try the command 'which gEDA' or perhaps 'which geda' - if the system knows where it is, it will tell you.  Jan

I've checked - the correct command is 'which geda' (all lower case).  To run it, just try typing 'geda' in a terminal window.  J.

---

### Post by The Mekon on 2005-12-13
I have just checked my gEDA installation using the following command in the terminal:

locate geda

This shows all the files and the geda executable file is in /usr/bin.

I have added gEDA to my Applications menu using smeg (available from Synaptic) but it works from the terminal as stated in a previous post

---

### Post by varunus on 2005-12-13
Also, if you right click a package that you've installed in Synaptic and choose "properties", there's an "installed files" tab.  You can see where the program has been put.

Hopefully there will be more work to integrate with the menuing system as Ubuntu progresses...

---

