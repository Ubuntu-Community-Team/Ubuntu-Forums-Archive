---
title: "USB optical mouse"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by luzdegas on 2007-05-01
Hi.
I have recently installed Ubuntu 7.04 in a Dell XPS M1210 notebook, and I have the following problem. When I plug in my USB Microsoft Mouse nothing happens, the mouse does not respond. 
Im quite a linux newbie on this. Should I have to select somewhere if I want to use the USB mouse or the touchpad? Should I have to install some driver?
I would appreciate any help!

---

### Post by Najand on 2007-05-01
There is a kernel bug filed concerning mouse/keyboard problems in Feisty. I think you pribably have the same problem.

---

### Post by luzdegas on 2007-05-01
Thanks for the answer, Do you know any workaround for this  bug? Can you give me the bug reference?
Thanks again!

---

### Post by StarscreamD on 2007-12-31
I'm having the same problem with my XPS m1330 and a Microsoft Optical Notebook mouse 3000 running Kubuntu Gutsy. My touchpad works like a champ, but when I plugin my mouse device, NO DICE. What gives, anyone got some sort of input here? Thanks!

EDIT: I have fixed the issue by rebooting with the device connected. Both devices work, and I am using something from the repositories called Touch Pad to disable the touchpad when I'm using my mouse. Sweet!

---

### Post by bryncoles on 2008-01-16
im having a similar issue with 7:10, gutsy gibbon.... if i plug in a USB mouse, it knocks out my touchpad. they only way i have found so far to fix the touchpad is to power down, wait a second and power up again. 

its not crippling, as long as i dont plug in a usb mouse i can use the touchpad. and as long as i cant use the touchpad, i can use the usb mouse. 

but it is mildly annoying! is there a setting i need to change?

---

### Post by Arthur Archnix on 2008-01-21
So you're saying that when you plug in a usb mouse your touchpad stops working? That's actually pretty good, usually you have to configure it to do that. But I suppose the problem is that when you unplug the mouse the touchpad isn't working? After unplugging the mouse, and with touchpad not working, try hitting <alt>F2 and then typing 
```
synclient touchpadoff=0
```
Does that turn the touchpad back on?

---

### Post by bryncoles on 2008-01-23
ha! thats genius, working a treat now! thank you for that post. i think im (slowly) getting more comfortable with this command line thing too :-D

---

### Post by Arthur Archnix on 2008-01-23
No problem. You'll probably want to create a shortcut to do that, like Control F10 or something. Go here, [http://ubuntuforums.org/showthread.php?p=4177125#post4177125](http://ubuntuforums.org/showthread.php?p=4177125#post4177125)

Scroll down to my post at the bottom and just do step number 3.

---

