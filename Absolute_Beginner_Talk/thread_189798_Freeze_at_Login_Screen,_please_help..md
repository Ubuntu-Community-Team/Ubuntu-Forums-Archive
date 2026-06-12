---
title: "Freeze at Login Screen, please help."
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by voiceofxile on 2006-06-05
When I am at the Ubuntu login screen the system freezes. I tried a suggestion for a previous post, which was to go into the sudo nano /ect/xll/xorg.conf from the kernal recovery option. This file is empty, and I believe I require drivers for my ATI all in wonder x600 graphics card.   

How can I download the drivers in linux, cause the text versions seem to work, while the graphic interface does not. I have no experiance with linux, as I have not been able to get it to work on my system. Maybe I could request a bit of step by step help?

---

### Post by richbarna on 2006-06-05
Is your post a typo ?
It's actually :-
> sudo nano /etc/X11/xorg.conf
Also, have you tried a console login at the start?
You will just get the black screen with the login prompt.
Type your username and password and then type :-
> startx
This might get your GUI going.

You could also try and reinstall the desktop environment :-
> sudo aptitude update
> sudo aptitude install ubuntu-desktop

---

### Post by edurm on 2006-06-06
Read this too: [http://www.ubuntuforums.org/showthread.php?t=190133](http://www.ubuntuforums.org/showthread.php?t=190133)

---

### Post by voiceofxile on 2006-06-06
I appreciate the help!   I have been reading up on commands, and i've found some help & man files which have helped me learn things.   This is exactly what happens to me.

I start my computer, and the graphical ubuntu loads to the Login screen.  If I login the screen changes as it begins to load, but then locks up.

I use the CTR-ALT-F1  to access a command promt and I can login to a text only system.

Using aptitude I have updated and installed the fglrx driver. How can I be sure the system is actually using this ati driver rather than the nVidia drivers?

Can I explore the cd-rom from the command prompt I am at? I do have the ubuntu install cd...

Any help would be most appreciated, as figuring this out on my own isn't happening. =(

---

