---
title: "Mouse help, please"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by pipedreambomb on 2006-11-28
Hi, I've just finished installing Ubuntu for the first time, have very little experience with Linux, and my immediate issue is configuring my mouse. See, the left mouse button is physcially broken. In Windows I have the mouse set up so that my right button = a 'left click', and the middle button = a 'right click'. Can someone please tell me how I can do this, especially bearing in mind that... well, I can currently only 'right click' stuff with my hardware at least.

Thanks in advance.

---

### Post by pipedreambomb on 2006-11-28
Please? Anyone? I can't do anything with just a right mouse button, including browsing for an answer! Just a way to left click would do.

---

### Post by verby on 2006-11-28
not sure if this would work but... did you try
system-preferences-mouse and mark left hand mouse.
option #2
maybe its a time to buy a new mouse

---

### Post by drkkbn on 2006-11-28
You may try changing your mouse settings (System-->Preferences-->Mouse) to left-handed so the right mouse button will be the left-click and left mouse button will be the right-click. At least you will have the left-click. Sorry I was late....

---

### Post by pipedreambomb on 2006-11-28
> **verby said:**
> not sure if this would work but... did you try
system-preferences-mouse and mark left hand mouse.
option #2
maybe its a time to buy a new mouse

I don't understand what you mean, but thanks for replying :-) If you're suggesting I click where it says System at the top of the screen, it doesn't do much when I right click it.

---

### Post by pipedreambomb on 2006-11-28
Is there perhaps a way to launch system preferences from a terminal? That's the only thing I seem to be able to open (along with Firefox) just by right clicking things.

---

### Post by squidward_tentacels on 2006-11-28
You could go really hardcore and do without the GUI interface altogether, just "sudo apt-get remove --purge gnome-desktop" , and run EVERYTHING from the terminal, or I think I would go with, 

option #2
maybe its a time to buy a new mouse....
:D

---

### Post by adam.tropics on 2006-11-28
> **squidward_tentacels said:**
> You could go really hardcore ...

Well to just have left click on right click, do <Alt><F2> to open a run dialog, and enter

```
gnome-mouse-properties
```This allows you to set your mouse as left handed, giving you at least left click, but if your feeling a tad more adventurous, you could always...

Long way round small problem! I am sure it's not ideal, and is straight from a Gentoo guide, so not so simple as I'd have liked for you either! Still, here goes...

Press <Alt><F2>, this should open a run dialog. enter

```
gnome-terminal
``` press return, which will open a terminal,type

```
xev
```press return, as you move your mouse over the small opened window, click the mouse buttons, and see what button numbers your mouse returns for each click by running through the output in terminal. Make a note of those, and close the xev window.Back in terminal, enter

```
gksu gedit /etc/X11/xorg.conf
```enter your password when asked, and a text editor will open with your xorg.conf file open. Scroll down to the section relating to Mouse, looking something like
```

Section "InputDevice"
      Identifier  "Mouse"
      Driver      "mouse"
      Option      "Device" "/dev/input/mice"
      Option      "Protocol" "auto"
EndSection
```before EndSection add the line

```
      Option      "ButtonMapping" "1 2"
```where the numbers relate to the button numbers you noted earlier, in your case, the first number will probably be 2 (your new back to front Left click), and the second I am not sure of, but whatever number you got for middle click. 

Then restart your xserver or computer and log back in and see how it went!
 If it worked at all, you may have to tweak the last bit until it's how you want.....good luck :D

---

