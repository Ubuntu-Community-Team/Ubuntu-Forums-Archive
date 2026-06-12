---
title: "Touchpad problems for 10.10 6,2 MacbookPro"
date: 2010-11-24
forum: Apple Hardware Users
---

### Post by disappearedng on 2010-11-24
Touchpad sucks. 
I don't know whether I am doing it right, 
but I can't seem to be able to do the following:

1) highlight a bunch of text (I can double click and drag, but that's limited to just a certain area).
2) I cannot 'click' and 'drag'. I would like that. As soon as I start clicking, my mouse cannot move. 
3) I cannot do left clicks! I tried ctrl-click or command-click and it doesn't work either.

---

### Post by vsh3r on 2010-11-24
Click on 

System->Preferences->Mouse->Touchpad

Once you do that you you can setup right click and single click selects.

(see attached image)

V$H.

---

### Post by disappearedng on 2010-11-25
> **vsh3r said:**
> Click on 

System->Preferences->Mouse->Touchpad

Once you do that you you can setup right click and single click selects.

(see attached image)

V$H.

Ok so when I apply do this, I realize I can achieve right click with two tab on the touchpad. 

However, I can only achieve select drag when I click, and without letting go, move my finger. I find this to be really limited to how far I can select. Is it possible to left select with one click and another movement to drag (like how typical mouse works).

---

### Post by skullmunky on 2010-11-27
Yes, that's annoying.  You can configure more options using the "synclient" command in the terminal.  
```

synclient -l

```
will list the current settings for the Synaptics touchpad.  To see a description of all the options, read the manual page for "synaptics" (the actual driver)
```

man synaptics

```

the man page describes everything in terms of xorg.conf parameters, but the same descriptions match the options to the synclient program for tweaking.

If you want to get the dragging behavior you're describing, it seems you have to disable the 2-finger-click -> Right-Click mapping, like this:

```

synclient ClickFinger2=0

```

The other thing I've been doing is turning on Palm Detect and disabling Tap to Click, because the pad seems hyper sensitive and it tends to click, drag, right click, and middle click things all over the place while I'm typing.  

```

synclient TapButton1=0
synclient TapButton2=0
synclient TapButton3=0
synclient PalmDetect=1

```

of course the one problem is now there's no way to generate a Right Click.  so I actually turned two finger tap back on

```

synclient TapButton2=3

```

it's still not so great, though, so maybe someone has a better solution ... ? 

there are some options that the driver seems to be missing which would be really helpful, like a way to set a max distance between two fingers for it to count as a two finger tap or click, or a min tap time to filter out accidental touches.

---

### Post by CIement on 2010-11-29
Unfortunately I don't have a fix for you, but at least I think I can explain what the problem is so maybe someone else more knowledgeable can help.

Basically the problem is that the click thing is under the trackpad, so when you click the button, your finger is on the trackpad which registers that you are using it. So, if you use another finger to move it thinks you're using multitouch when you don't want to.

For now though, if you want to highlight or drag, you can just tap twice and hold it on the second tap and drag to highlight or drag something. What's worse though is the fact that you can't click on the bottom right portion of the touchpad anymore to right click, because since the touchpad is so huge it's too easy to accidentally tap it with your palm while typing which gets incredibly annoying.

---

