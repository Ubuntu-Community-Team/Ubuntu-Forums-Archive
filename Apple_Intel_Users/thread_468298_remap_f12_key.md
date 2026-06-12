---
title: "remap f12 key"
date: 2007-06-08
forum: Apple Intel Users
---

### Post by erkker on 2007-06-08
Hello all

I am trying to remap my f12 /f11 keys to something else.  I have tried to remap them but I cannot find what the keycode is.  When I open xev and press f12 I get a button event not a keystroke.  I saw a script that benanzo wrote and that allowed me to map the lower enter key to Delete but the right click is unresponsive.

Basically how to I unmap the right click of f12 and remap something else in its place


Thanks

---

### Post by ivesjd on 2007-06-08
You need to disable 3button mouse emulation. I can't remember how to do this. But you should be able to find it by searching. I posted about the same thing a few weeks ago. 
```
 xmodmap -e 'keycode 116 = Pointer_Button3' 
```
There is the line for rightclick on the lower Apple/CMD key. Hope that helps some.

---

### Post by erkker on 2007-06-08
Thanks for the reply but thats the code that didnot work for me.  I put that in my rc.local script along with a mapping to convert the lower enter key to the delete key.  The enter key mapping worked but the apple key did not work. and f12 still acts as right click and xev did not give me the keycode for f12 it outputted a mouse click so that was a dead end.


any other ideas?

thanks


-E

---

### Post by ivesjd on 2007-06-09
I think the reason that you can't get right click to work is because it still has F12 mapped. I searched for a way to remove the F12 keymap and couldn't find anything. (The only time these forums have ever let me down) The only thing I can say is to keep searching. I ended up reinstalling and not enableing three mouse button emulation. If you could find a way to disable the mouse button emulation then there would be no need to reinstall. 
I just searched the forums quickly and couldnt seem to find anything. But when you solve it please post back here with how you did so others can benifit. :)

---

### Post by ivesjd on 2007-06-28
I think you can turn off three button mouse emulation in xorg.conf

---

### Post by ~joe~ on 2007-06-29
Yes, you can disable emulate3buttons in the xorg file. Look for your trackpad section, it should say something like "Synaptics". Below it there should be a line that reads
```
	Option		"Emulate3Buttons"	"true"
```
Change that to false, save and exit. Then go back into X11 and hit Control-Option-Backspace to reboot the X server and test out the new setting.

---

### Post by ivesjd on 2007-06-29
> **~joe~ said:**
> Yes, you can disable emulate3buttons in the xorg file. Look for your trackpad section, it should say something like "Synaptics". Below it there should be a line that reads
```
	Option		"Emulate3Buttons"	"true"
```
Change that to false, save and exit. Then go back into X11 and hit Control-Option-Backspace to reboot the X server and test out the new setting.

Odd. I had never actually need to do this, and I reinstalled last night. And it won't disable the F12 right clicking. :/

---

### Post by ivesjd on 2007-06-29
Fixed it. If you uninstall mouseemu "sudo apt-get remove mouseemu" It will disable the F12 and F11 buttons, but I leave the xorg entry on so I can have the right cmd key right click.

---

