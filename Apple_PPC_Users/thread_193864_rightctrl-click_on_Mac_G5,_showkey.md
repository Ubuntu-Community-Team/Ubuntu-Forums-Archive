---
title: "right/ctrl-click on Mac G5, showkey"
date: 2006-06-10
forum: Apple PPC Users
---

### Post by swartzfeger on 2006-06-10
All,

Still having no luck getting right-click/ctrl-click to work. For instance, I love using Remote It Permanently with Firefox, but it's almost impossible to use without a right-click. I know people will say get a 3 button mouse (and I probably will, eventually), but I *really* want to make this work and see what I'm doing wrong (or see what bug there is in the system).

My default sysctl.conf is

# Emulate the middle mouse button with F11 and the right with F12.
dev/mac_hid/mouse_button_emulation = 1
dev/mac_hid/mouse_button2_keycode = 87
dev/mac_hid/mouse_button3_keycode = 88

This is where the confusion comes in. I've ran 'sudo showkey' to see the code of the key I'd like to bind to the right/ctrl-click. As you can see in the .conf above, the key codes appear to be numerical. When I run show key it produces codes like

0x1d 0x9d
0x57 0xd7
0x58 0xd8

F11/F12 comes up as  0x57 0xd7 and 0x58 0xd8, not 87 and 88. Is showkey not the command I should be running?

Is there a simpler GUI app I can use to bind keys?

Thanks for all the help the last week... I *am* enjoying my Linux time, and I hope I haven't whined too much! ;)

PS -- this is the default/OEM white Apple Keyboard that ships with the G5 towers.

---

### Post by nkbj on 2006-06-11
I use the mouseemu package from the universe repositories (I think) with this configuration in /etc/default/mouseemu:

# Defaults for mouseemu initscript (/etc/init.d/mouseemu)
# These are the default values on PowerPC. On all other architectures
# middle and right click are disabled by default.
# Key codes can be found in include/linux/input.h in the kernel headers
# or by using `showkey` in a console.


MID_CLICK="-middle 125 272"      # Command key + mouse click
RIGHT_CLICK="-right 29 272"      # Control key + mouse click
SCROLL="-scroll 56"              # Alt key + mouse movement
TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress

Regards,
Niels Kristian

---

### Post by swartzfeger on 2006-06-11
[QUOTE=nkbj]I use the mouseemu package from the universe repositories (I think) with this configuration in /etc/default/mouseemu:

# Defaults for mouseemu initscript (/etc/init.d/mouseemu)
# These are the default values on PowerPC. On all other architectures
# middle and right click are disabled by default.
# Key codes can be found in include/linux/input.h in the kernel headers
# or by using `showkey` in a console.


MID_CLICK="-middle 125 272"      # Command key + mouse click
RIGHT_CLICK="-right 29 272"      # Control key + mouse click
SCROLL="-scroll 56"              # Alt key + mouse movement
TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress
[/QUOTE]

Thanks Niels!

Pardon my ignorance, but how do I launch/invoke mousemu? I installed it via adept, but I don't see it in my Kmenu, /bin, did a search -- can't seem to find it.

Do I do something like 'kdesu mousemu'?

---

### Post by nkbj on 2006-06-11
**kdesu /etc/init.d/mouseemu**

It is startede during boot - at least at Ubuntu (I haven't tried Kubuntu).

Regards,
Niels Kristian

---

### Post by bennyp on 2006-06-15
[QUOTE=swartzfeger]Is there a simpler GUI app I can use to bind keys?[/QUOTE]
You can use an app called xkeycaps to bind keys. I have not had success with it, however, as it does not recognize my keyboard layout. As of right now my Apple keys are essentially useless, and it's a pain. Does anyone know how to enable them?

---

### Post by swartzfeger on 2006-06-15
[QUOTE=bennyp]You can use an app called xkeycaps to bind keys. I have not had success with it, however, as it does not recognize my keyboard layout. As of right now my Apple keys are essentially useless, and it's a pain. Does anyone know how to enable them?[/QUOTE]

I'd like to know too, but I've given up. After spending hours editing my sysctl.conf using the proper keycodes, I still couldn't get right-clicking to work (and the original mapped F11/F12 keys also never worked).

I have 2 mice connected to my keyboard's USB ports -- original Mac mouse for OS X, 2-button for Kubuntu. Seems to work well so far.

---

### Post by barrack on 2006-07-06
[QUOTE=nkbj]I use the mouseemu package from the universe repositories (I think) with this configuration in /etc/default/mouseemu:

# Defaults for mouseemu initscript (/etc/init.d/mouseemu)
# These are the default values on PowerPC. On all other architectures
# middle and right click are disabled by default.
# Key codes can be found in include/linux/input.h in the kernel headers
# or by using `showkey` in a console.


MID_CLICK="-middle 125 272"      # Command key + mouse click
RIGHT_CLICK="-right 29 272"      # Control key + mouse click
SCROLL="-scroll 56"              # Alt key + mouse movement
TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress

Regards,
Niels Kristian[/QUOTE]


I was able to edit the file, but it wouldn't let me save. I am really new to this and am trying to read as much as I can. But how to edit these files and actually have them stay put? I am using gedit, as this is the default that opens up these files. Is there something that I'm missing?

---

### Post by zachws on 2006-07-06
[QUOTE=barrack]I was able to edit the file, but it wouldn't let me save. I am really new to this and am trying to read as much as I can. But how to edit these files and actually have them stay put? I am using gedit, as this is the default that opens up these files. Is there something that I'm missing?[/QUOTE]

I'm guessing that you navigated to the mouseemu folder via the graphical interface. In order to change the contents permanently as you wish to do you need to do so beginning in the terminal.

sudo gedit /etc/...
(I put the ellipsis because I do not know the exact location, but you do.)

Then the save option will not be grayed out.;)

---

