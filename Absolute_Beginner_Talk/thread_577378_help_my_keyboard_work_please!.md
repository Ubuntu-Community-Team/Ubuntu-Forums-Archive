---
title: "help my keyboard work please!"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by D_D_T on 2007-10-16
Please help me. 
I'm currently using Kubuntu Feisty with a Toshiba Satellite Pro a-60 and it works well, apart from the fact that I can't get the keyboard layout sorted. Shift keys are left unaccounted for, and things get very frustrating at times. Can anybody help me please? The laptop's keyboard is marketed as having:
keys : 86
Windows keys : 2
number of cursor keys : 4
inlaid numeric keypad : yes
Hot Keys : 2
if that makes any sense. Please help me! :)

---

### Post by Joeb454 on 2007-10-16
Have you check in the settings? not used Kubuntu myself, but I'm guessing the preferernces menu wherever that may be, will hold the keyboard settings.

Check them. I had an issue where all my keys were jumbled because it was set to a different language :p

---

### Post by Anicka on 2007-10-16
Do you know which layout your keyboard has? If you don't, take a look here: [http://en.wikipedia.org/wiki/Keyboard_layout](http://en.wikipedia.org/wiki/Keyboard_layout)

Post what you get from the command: grep Xkb /etc/X11/xorg.conf

I have a standard swedish keyboard and get:
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "se"

---

### Post by D_D_T on 2007-10-16
That command give the following:

Option          "XkbRules"      "xorg"
Option          "XkbModel"      "pc105"
Option          "XkbLayout"     "gb"

Having checked out the keyboard layouts, none are the correct ones as I think that the Laptop I use has changed the key positions to save space.

---

### Post by Anicka on 2007-10-16
Question: How many keys do you have in between the shift-keys and what is the shape of your enter-key?

---

### Post by D_D_T on 2007-10-18
Hi, Sorry for late reply.
There are 10 keys between the shifts and the enter key is a rectangle, occupying the space  of two normal keys horizontally. I hope that helps.
Thank you for your help!
D_D_T

---

### Post by Anicka on 2007-10-19
Sounds that you have some version corresponding to a 104-keyboard and not a105. Try changing that in you xorg.conf. Further than that I don't think I can help you. It is difficult to tell, not knowing where you are or where your computer comes from. And as you said, they might have invented there own system to save space.

---

