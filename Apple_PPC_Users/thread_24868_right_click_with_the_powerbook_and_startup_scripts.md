---
title: "right click with the powerbook and startup scripts"
date: 2005-04-08
forum: Apple PPC Users
---

### Post by revolthor on 2005-04-08
i used to use gentoo on my powerbook, and used a little start-up script to get my computer to use "ctrl+alt" to emulate a right click.  to get scripts to autmatically run at boot, you just had to use a command "rc-update add <script name> default" which does not appear to work with ubuntu.

a) does anyone have another way to get right click emulation with ubuntu?
b) does anyone know how to get scripts to run at boot?
thanks a bunch.

---

### Post by revolthor on 2005-04-08
according to micro, this is how you do it:
```

you'll have to add three lines to the file /etc/sysctl.conf to emulate 2nd +3rd mouse button.

# Emulate the middle mouse button with F11 and the right with F12.
dev/mac_hid/mouse_button_emulation = 1
dev/mac_hid/mouse_button2_keycode = 87
dev/mac_hid/mouse_button3_keycode = 88

This will be available after a reboot

```

of course, you can always change the keys, i like to use fn+alt (keycode=100) for right button.

thanks a bunch!

---

### Post by Rxke on 2005-04-08
sudo gedit /etc/sysctl.conf

does this painlessly, those lines are alredy there.

just change the 88 into the code for alt+ctrl, whatever it is. and save the file

Or into 100, which gives you the Fn+Alt, as revolthor suggested.

---

### Post by areitze on 2005-04-08
And Can I add 2 questions to this post???

1.- what would be the combination if I where to change it to be instead of fn+alt, to make it ctrl+the big mouse button from the trackpad (not the tap on the pad, the button)
2.- and is there a way to make a scroll on the track pad like "sidetrack" under osx??? it's an app that you install and makes the extream right part of the track pad a scroll for up and down...  really usefull...

Thx,
Andres.-

---

### Post by Francesco on 2005-04-12
I have changed the /etc/sysctl.conf file on my ibook....

# Emulate the middle mouse button with F11 and the right with F12.
dev/mac_hid/mouse_button_emulation = 1
dev/mac_hid/mouse_button2_keycode = 100
dev/mac_hid/mouse_button3_keycode = 88

the fn+alt does not works at all, and the second button mouse is still f12... 
Why?

---

### Post by callipeo on 2005-04-13
Hi all,

I just want to point out that you can see the keycode of any combination of keys with the "showkey" utility (you have to run it on the console, not the terminal emulator). Of course you have to convert its output in decimal (gcalctool can do it for you).

---

### Post by Rxke on 2005-04-13
[QUOTE=Francesco]I have changed the /etc/sysctl.conf file on my ibook....

# Emulate the middle mouse button with F11 and the right with F12.
dev/mac_hid/mouse_button_emulation = 1
dev/mac_hid/mouse_button2_keycode = 100
dev/mac_hid/mouse_button3_keycode = 88

the fn+alt does not works at all, and the second button mouse is still f12... 
Why?[/QUOTE]
 Francesco, it's the other way round, 

button two 87 and button three 100.

button three is the right button, two is middle button... Anyway it worked that way for me.

---

### Post by rzzt on 2005-04-17
All the scripts that start-up a service on boot are placed in /etc/init.d/. If you want to activate a service, you just have to create a symlink in /etc/rcx.d/ (where x is your default runlevel, 2 in ubuntu) to the apropiate script in /etc/init.d. For example:
[INDENT]ln -s /etc/init.d/script /etc/rc2.d/S59script[/INDENT] 
Its important that the name of the symlink starts with S or K .This indicates that the service will Start (S) or stop (K) when we were entering in the runlevel. The two numbers indicates the priority exec of the script (write any number between 00 and 99). 
You can also create two symlinks in the rc0.d and rc6.d to stop the service at halt or reboot the system
[INDENT]ln -s /etc/init.d/script /etc/rc0.d/K45script[/INDENT]

---

### Post by callipeo on 2005-04-17
Hi,

You can also use update-rc.d; suppose you have a /etc/init.d/<service> script: then do "update-rc.d <service> start 45 2 3 4 . stop 99 0 1 6 .". This will start <service> on runlevel 2, 3 and 4 with priority 45, and will stop it on runlevel 0, 1 and 6 with priority 99. A simpler form is "update-rc.d <service> defaults <NN>", which will start <service> on runlevel 2, 3, 4, 5 and will stop it on runlevel 0, 1, 6, both with priority "NN" (if you omit it, 20 will be used). Of course you can find the details in the man page.

---

### Post by saltydog on 2005-04-27
To do init scritp configuration, there is now Ubuntu Bootup Manager, downloadable here:
[http://www.marzocca.net/linux/ubm.html](http://www.marzocca.net/linux/ubm.html)

---

