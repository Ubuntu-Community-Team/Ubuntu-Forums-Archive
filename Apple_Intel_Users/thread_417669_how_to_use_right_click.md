---
title: "how to use right click?"
date: 2007-04-21
forum: Apple Intel Users
---

### Post by null84 on 2007-04-21
hi.. i just got a macbook and installed ubuntu 7.04 however,  i dont know how to use right click or insert key in Ubuntu... can someone please tell me?

---

### Post by ronocdh on 2007-04-21
> **null84 said:**
> hi.. i just got a macbook and installed ubuntu 7.04 however,  i dont know how to use right click or insert key in Ubuntu... can someone please tell me?
IDK for sure, but I assume Tyrdium's post in my Ndiswrapper thread just below this should apply to your case. My touchpad performance is very shoddy, even with Gsynaptics running, so I've only been using a mouse. Haven't solved the mouse + key press problem yet, either....

---

### Post by miguev on 2007-04-22
By default the second (central) and third (right) mouse buttons are emulated with F11 and F12 keys respectively. I think you get tapping and scrolling working by installing gsynaptics, but I'm not sure if that was what fixed the mouse or if it was just upgrading Feisty Beta on April 16th.
I you get tapping working, the second (central) and third (right) mouse buttons are done by tapping with two and three fingers respectively.
Once you get tapping, you may want to have F11 and F12 do their proper job as keys, so you can use this content for /etc/defaults/mouseemu
```
# same behaviour as in MacOS X
MID_CLICK="-middle 0 0"          # F11 with no modifier
RIGHT_CLICK="-right 29 272"      # Left Ctrl + click
TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress
```

---

### Post by ronocdh on 2007-04-22
> **miguev said:**
> By default the second (central) and third (right) mouse buttons are emulated with F11 and F12 keys respectively. I think you get tapping and scrolling working by installing gsynaptics, but I'm not sure if that was what fixed the mouse or if it was just upgrading Feisty Beta on April 16th.
I you get tapping working, the second (central) and third (right) mouse buttons are done by tapping with two and three fingers respectively.
Once you get tapping, you may want to have F11 and F12 do their proper job as keys, so you can use this content for /etc/defaults/mouseemu
```
# same behaviour as in MacOS X
MID_CLICK="-middle 0 0"          # F11 with no modifier
RIGHT_CLICK="-right 29 272"      # Left Ctrl + click
TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress
```
I can confirm that installing gsynaptics will allow you to use two-finger scroll, and also provides options for tapping (I shut it off, can't stand it). I still don't like the trackpad behavior in Ubuntu, so I've been using a mouse (doesn't help that my wireless isn't up yet and so I have to work beside my router!).

For me the trackpad just stops responding every now and then, most often when I try to move the cursor from one side of the screen to the other, which usually necessitates about two or three finger strokes. And the two-finger scrolling leaves a lot to be desired, as well; it isn't smooth, and your fingers must be placed together, side by side, and both move down on the trackpad parallel to each other. Bleh.

Please let us know your results, and anyone else can chime in with their experiences.

---

### Post by sirrahn on 2007-04-23
Hi I just installed ubuntu (7.04) and right click doesn't seem to work at all!

I know that clicking while pressing F11 and F12 is supposed to work, but it doesn't. The help page ([https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)) says that the file /etc/default/mouseemu controls which keys can be used, but this file does not exist on my laptop.

I don't understand because I did a straight forward install - does anyone know why this might be and how to fix it?

thnaks,

nathan

---

### Post by macron1 on 2007-04-23
hay, cheers everyone for your help with setting up the touchpad on the macbook. 

i too am having trouble getting two and three-fingered clicking going. ive got the touchpad driver all installed, tap-clicking works also

one point i notice immeadiatly is i dont seem to have mouseemu in etc/defaults/, (indeed my etc/ only has "/default", rather than "/defaults"), and cannot for the life of me get F11 or F12 working as right or middle click (f11 toggles between full-screen and normal in firefox...)...


any help would be much appreciated.

---

### Post by sirrahn on 2007-04-24
Just did the obvious and it worked! Went to Synaptic and installed mouseemu: couldn't find the file because it wasn't on the system. Immediate joy.

Don't know why it wasn't installed but who care now.

---

