---
title: "HOWTO: Xubuntu Apple keys as LMB and MMB"
date: 2006-09-24
forum: Apple PPC Users
---

### Post by DirtDawg on 2006-09-24
By default, most Apple Computers come with a one-button mouse. Xubuntu uses the F11 as the Middle Mouse Button(MMB) and F12 as the Right Mouse Button(RMB), but there's no GUI to change that default. I, personally, hate this setup. 
The following will show you how to reassign the MMB and RMB to the command keys (aka: the "apple" keys"). Most of this has been compiled from [this thread]("http://ubuntuforums.org/showthread.php?t=9189").

First make a backup of your /etc/sysctl.conf file, then open the original sysctl.conf file in mousepad:
```
 sudo mousepad /etc/sysctl.conf 
```
Find the code on the very bottom that looks like this:
```
# Emulate the middle mouse button with F11 and the right with F12.
dev/mac_hid/mouse_button_emulation = 1
dev/mac_hid/mouse_button2_keycode = 87
dev/mac_hid/mouse_button3_keycode = 88
```
Replace the values 87 and 88 in the last two lines with 126 and 125 respectively so it looks like this:
```
dev/mac_hid/mouse_button_emulation = 1
dev/mac_hid/mouse_button2_keycode = 126
dev/mac_hid/mouse_button3_keycode = 125 
```
Finally save and close mousepad and enter the following command into the terminal:
```
 sudo sysctl -p 
```

Now the Left apple button is the LMB and the Right apple button is the MMB!

---

