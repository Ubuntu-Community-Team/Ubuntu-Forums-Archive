---
title: "Extra mouse buttons working?"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by kubilaycan on 2007-09-15
How many of you actually have successully made all their mouse buttons work?

---

### Post by Fixman on 2007-09-15
How many buttons have your mouse?

>  Screenshot? 

---

### Post by Majorix on 2007-09-15
I have 5 buttons on my mouse. 3 of those standard ones (left, right and middle buttons [a.k.a wheel]) and 2 on the side which allow me to go back and forward on browser pages.

All of the standard buttons work fine I know that. Never tried the buttons on the side as I don't use them much.

On the touchpad, everything works.

If you are unhappy with your mouse driver, you can try to find another open source driver. Maybe that brings you luck.

Have fun.

---

### Post by Tecguy2 on 2007-09-15
i only have a standed usb mouse for my laptop and a touch pad they work fine

or are you talking about a mouse like a logitech g5

---

### Post by kubilaycan on 2007-09-15
i have 5 buttons. that would be 7 in xorg language.

i tried once to fix them, i did what was told in a thread, but didnt work. since then i reinstalled ubuntu (for other various reasons, nothing to do with mouse) and i did not bother about the buttons. 

i dont really need them that much as i use opera and set "hold right and click left" to back and "hold left and click right" to forward.

that will do until one day i get pissed off remembering that i cannot use them in nautilus and throw my mouse out the window.

and by the way, from reading many threads on mice, it seems every third person is using a logitech mx something and the rest an intellimouse...

am i the only one who bought the cheapest 5 button mouse off ebay? all i know about my mouse is that it is made in china. well, at least it has a sticker on it saying so.

i love ubuntu, but expecting the back and forward buttons to work out of the box is not expecting too much.

---

### Post by NilsHG on 2007-09-15
i have 2 standard buttons, mouse wheel (which is another button) and a side button. i had to adjust the config, but now the side button works fine.

---

### Post by Dylock on 2007-09-15
I have a logitech lx5 optical mouse, 7 button mouse according to X

Left and right mouse, Up wheel, down wheel, Wheel push. Left wheel push, right wheel push

got it correctly working

Set it up with evdev and the following xorg.conf entry

Section "InputDevice"
   Identifier "Configured Mouse"
   Driver "evdev"
   Option "CorePointer"
   Option "Name" MYMOUSENAME"
EndSection

There are some guides out there about how to set them up.

---

### Post by kubilaycan on 2007-09-15
"some"? there are a lot!

in fact, too much... too much that i got fed up reading them and started this poll to see if i was the only one raging with fury cuz my mouse dont behave like it used to in windows..

the other day i was bragging about how cool my ubuntu installation is and showing off my compiz fusion effects to my flatmate who uses xp. he wanted to try my ubuntu out so he sat down opened the browser and after a minute he started asking the forbidden question... "why doesnt the back button work?"  

i told him to leave me alone...

---

### Post by Dylock on 2007-09-15
what kind of mouse do you have?

---

### Post by kubilaycan on 2007-09-15
i use a cheapomatic 5 button mouse. left right wheel back and forward.

---

### Post by Dylock on 2007-09-15
which brand?

---

### Post by kubilaycan on 2007-09-15
there is no brand name on it. as i said, its the cheapest 5 button mouse i found on the internet.

---

