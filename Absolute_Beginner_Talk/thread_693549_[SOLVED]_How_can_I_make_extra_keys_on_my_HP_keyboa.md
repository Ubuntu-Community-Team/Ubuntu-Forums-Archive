---
title: "[SOLVED] How can I make extra keys on my HP keyboard work"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by snuffy on 2008-02-11
I have a HP Internet keyboard part #5185-2038 that i would like the buttons to work on.

I don't know what PC it originally came from, but it has the following buttons along the top in order from left to right:

Sleep/shutdown?(moon symbol), help, HP, Print, Camera, Shopping, Sports, Finance, Connect, Search, Chat, Email, stop, rewind, play/pause, eject?, vol up and down, mute, music

some of the buttons work... but does anyone know how i can get all the buttons to work?

I would ideally like to be able to 'map' the buttons to my own choice of actions.

many thanks

tim.

---

### Post by benfindlay on 2008-02-11
First of all I'd take a look in System>>Preferences>>Keyboard SHortcuts. You can set up manual shortcuts here, so it may simply be an issue of assigning the relevlant buttons to the relevant functions

Hope this helps!

---

### Post by djbsteart1 on 2008-02-11
you can try to do it by reconfiguring the xserver. 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

but make a back up first, 

```
sudo dpkg-reconfigure xserver-xorg
```

just leave everything as id until you get to the setup of keys, you should get them working there.

---

### Post by snuffy on 2008-02-11
thanks, but that didn't work.  the volume buttons work and mute, search works, email brings up evolution, the moon logs me out, but that's about it.


> **benfindlay said:**
> First of all I'd take a look in System>>Preferences>>Keyboard SHortcuts. You can set up manual shortcuts here, so it may simply be an issue of assigning the relevlant buttons to the relevant functions

Hope this helps!

---

### Post by snuffy on 2008-02-11
sorry, i don't know what you mean.   can you explain further please. i have looked a the xorg.conf file before but i wouldn't know where to start with altering it.



> **djbsteart1 said:**
> you can try to do it by reconfiguring the xserver. 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

but make a back up first, 

```
sudo dpkg-reconfigure xserver-xorg
```

just leave everything as id until you get to the setup of keys, you should get them working there.

---

### Post by djbsteart1 on 2008-02-11
the first command opens up the xserver configuration wizard, i think you need to do this from safe mode. i can just remember the last time i used that it let me change what keys did on keyboard, i used it to use the window key to open a menu. so i imagine that you can use it for whatever you want it to do. although, i would advise only altering the keyboard settings as the xserver is important. i hope that that clears it up a little for you.

---

### Post by djbsteart1 on 2008-02-11
sorry the second command opens the config wizard.

---

### Post by snuffy on 2008-02-11
thanks, that helped.  but as far as could see (i spent quite a while reading through each screen), it doesn't do what i'm looking for.

i have found a program called Keytouch which might do the job, am just taking a look now.

thanks for your advice though, i appreciate it.

tim.



> **djbsteart1 said:**
> the first command opens up the xserver configuration wizard, i think you need to do this from safe mode. i can just remember the last time i used that it let me change what keys did on keyboard, i used it to use the window key to open a menu. so i imagine that you can use it for whatever you want it to do. although, i would advise only altering the keyboard settings as the xserver is important. i hope that that clears it up a little for you.

---

### Post by djbsteart1 on 2008-02-11
Thats good about the program, orry it wasnt helpful to you, and i hope you get the keys working.

---

### Post by snuffy on 2008-02-13
Yep, Keytouch did the job. had to use keytouch-editor to make a custom file for my keyboard, but that wasn't too difficult to figure out.

thanks for your speedy replies.

tim.

---

