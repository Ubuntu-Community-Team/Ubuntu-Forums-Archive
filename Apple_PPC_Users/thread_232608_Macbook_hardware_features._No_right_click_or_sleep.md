---
title: "Macbook hardware features. No right click or sleep."
date: 2006-08-08
forum: Apple PPC Users
---

### Post by asc on 2006-08-08
Dapper is running on a Macbook. Most of the important hardware works (network, video, sound) but there are some lesser HID issues that falsely advertise their own functionality.

First is right click and middle click with the track pad. I added these two lines to $HOME/.xmodmap and logged back into Gnome

```
keycode 116 = Pointer_Button2
keycode 108 = Pointer_Button3
```
xev reports that they are in fact sending those key codes to xorg. But the OS does not recieve a right or middle click. Nothing happens. When I attach an external USB three button mouse with a scroll wheel, all the buttons magically start working on only the external mouse.

Second is suspend and hibernate. After installing the macbook-backlight-hal from [http://ubuntu.desrt.ca/](http://ubuntu.desrt.ca/) both the suspend and hibernate buttons appeared in the quit menu. Both buttons do the same thing. They appear to turn off the power to the screen but the computer is still hot to the touch. After the screen goes dark, there is no way to wake it up. I have to do a hard power cycle to get an image back.

I'd like to hear from other users with the same hardware before I submit a bug report.

Thanks.

---

### Post by hajk on 2006-08-09
A bug eh? You must also use the xkbset package for this to work, and add these commands to the Startup Programs in Sessions.

Make a script,

$ sudo nano -w /usr/local/bin/keyboard

with the following contents:

#!/bin/bash
xmodmap -e "keycode 116 = Pointer_Button2"
xmodmap -e "keycode 108 = Pointer_Button3"
xkbset m

then make this script executable with

$ sudo chmod +x /usr/local/bin/keyboard

and, finally, add it to System - Preferences - Sessions under the Startup Programs tab.

Have fun!

---

### Post by hajk on 2006-08-09
> **asc said:**
> 
...
Second is suspend and hibernate. After installing the macbook-backlight-hal from [http://ubuntu.desrt.ca/](http://ubuntu.desrt.ca/) both the suspend and hibernate buttons appeared in the quit menu. Both buttons do the same thing. They appear to turn off the power to the screen but the computer is still hot to the touch. After the screen goes dark, there is no way to wake it up. I have to do a hard power cycle to get an image back.
...


Mmm, I'm not using those packages, but without them the sleep function on closing the lid seems to work on my MB, requiring a password login when opening the lid again. Even the wireless connection is then available again. I have not yet checked whether this sleep state is similar to that in OS X with the processor cooling to the 25 degrees C range.

Hibernate does not work in that the saved session (in swap?) is not restored. Bugs have already been filed in Malone as far as I can tell.

---

### Post by frenkel on 2006-08-09
> **asc said:**
> Dapper is running on a Macbook. Most of the important hardware works (network, video, sound) but there are some lesser HID issues that falsely advertise their own functionality.

First is right click and middle click with the track pad. I added these two lines to $HOME/.xmodmap and logged back into Gnome

```
keycode 116 = Pointer_Button2
keycode 108 = Pointer_Button3
```
xev reports that they are in fact sending those key codes to xorg. But the OS does not recieve a right or middle click. Nothing happens. When I attach an external USB three button mouse with a scroll wheel, all the buttons magically start working on only the external mouse.


You should save that file as .Xmodmap, not as .xmodmap. Now when you log in and out, Gnome will recognize it.

---

### Post by asc on 2006-08-09
> **hajk said:**
> A bug eh? You must also use the xkbset package for this to work, and add these commands to the Startup Programs in Sessions.

Make a script...with the following contents:

#!/bin/bash
xmodmap -e "keycode 116 = Pointer_Button2"
xmodmap -e "keycode 108 = Pointer_Button3"
xkbset m

then make this script executable.

and, finally, add it to System - Preferences - Sessions under the Startup Programs tab.

I added your three lines to a script and the startup preferences. There is still no right or middle click buttons on the right apple and enter keys. I'm going to file the bug report now.

```
lee@priceless:~$ cat $HOME/bin/keyboard
#!/bin/bash
xmodmap -e "keycode 116 = Pointer_Button2"
xmodmap -e "keycode 108 = Pointer_Button3"
xkbset m

lee@priceless:~$ ls -l $HOME/bin/keyboard
-rwxr-xr-x 1 lee lee 107 2006-08-09 10:21 /home/lee/bin/keyboard

lee@priceless:~$ cat $HOME/.xmodmap
keycode 115 = Alt_L Meta_L
add mod1 = Alt_L Meta_L

keycode 101 = F1
keycode 212 = F2
keycode 160 = F3
keycode 174 = F4
keycode 176 = F5
keycode 214 = F7
keycode 215 = F8
keycode 216 = F9
keycode 217 = F10
```

---

### Post by gavin8or on 2006-10-07
> **hajk said:**
> A bug eh? You must also use the xkbset package for this to work, and add these commands to the Startup Programs in Sessions.

Make a script,

$ sudo nano -w /usr/local/bin/keyboard

with the following contents:

#!/bin/bash
xmodmap -e "keycode 116 = Pointer_Button2"
xmodmap -e "keycode 108 = Pointer_Button3"
xkbset m

then make this script executable with

$ sudo chmod +x /usr/local/bin/keyboard

and, finally, add it to System - Preferences - Sessions under the Startup Programs tab.

Have fun!
Um I got it working late last night... I'm pretty sure it was following these steps that did it.

Thanks! I really need my middle click to work in linux.

---

### Post by benanzo on 2006-10-16
I got this to work in edgy by changing #!/bin/bash to #!/bin/sh   that is the only change I made and it fixed it.

---

### Post by serme on 2006-10-28
I had a similar problem with Dapper; no matter what I put in my xmodmap, with or without xkbset -m, the right and middle mouse buttons wouldn't map, though the fn key, apple->alt, and F1-F10 mapped just fine. I tried upgrading to Edgy but my mac went into hibernation midway through the install and I couldn't wake it up again, and I ended up doing a complete reinstall from an Edgy Live CD.

I haven't tried remapping my keys yet (but it's high on my to-do list). Macbook-backlight-hal worked perfectly for me; what do I add to my sources.list so that I can apt-get it again?

---

