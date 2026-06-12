---
title: "EMERGENCY for Ubuntu text console"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by dylonium on 2006-04-12
I just hit CTRL+ALT+F1, but I want to get back to my main screen. I haev a job to do and I have to catch a plane real soon. Please respond ASAP!

---

### Post by mrchrisblau on 2006-04-12
So you exited x and, I assume, when you type startx (after logging in) it says its already started.

This actually just happend to me.

Assuming you didnt set init to 3 you should be able to just pull the power on your box and it will reboot with the regular graphical user interface.

There might be a nicer way to go about it, but that should work.

---

### Post by tartarian on 2006-04-12
ctrl + alt + f7

---

### Post by mrchrisblau on 2006-04-12
[QUOTE=tartarian]ctrl + alt + f7[/QUOTE]

Like I said, there is probably a nicer/easier way :-D

---

### Post by tartarian on 2006-04-12
My I.T tech at school showed me that! lol

---

### Post by dylonium on 2006-04-12
Thank You So Much!

---

### Post by pbaehr on 2006-04-12
Just a quick note on virtual terminals so you understand what you're actually doing:

On a normal install there are six virtual terminals accessible by ctrl+alt+F1-6. This lets you log in as different users or spread yourself out across six screens. For example, installing something via apt-get on terminal 1? Hop over to terminal 2 if you need to do something more.

When the X-Windows server is running it is found on the seventh virtual terminal (accessed by ctrl+alt+F7).

So what you did without realizing it was switch to the first terminal (ctrl+alt+F1) and then back to the GUI on the seventh terminal (ctrl+alt+F7).

Just adding this so that you have a better idea of what actually happened.

P.S. - It's a lot like the four (by default) workspaces in xwindows if you've used those at all.

---

### Post by tartarian on 2006-04-12
Ok, you've intrigued me now! I didnt actually know what i was doing when i did that, i jus knew it (one of the few things i do actually know about ubuntu)

So there's 7 screen thingys that you can work on separatley? And log on as different users? Well when I press Ctrl + Alt + F1  i just get a black screen and white text saying Login:
Is there anyway to convert that to a graphical interface instead of the black and white?

---

