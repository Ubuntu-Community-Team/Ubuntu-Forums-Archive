---
title: "Grub boot up menu colors"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by ososxe on 2006-07-19
Hi.
I need help with the Grub boot up selection menu, on my laptop (Acer Aspire 3000) I can't barely see what entry on the menu is selected for start up. Text is white over a dark/black background, but the selected entry has a slightly darker/blacker background, wich on the majority of the light conditions i work with, is almost impossible to distinguish.
I've tried editing the grub menu.lst but the only thing i dared to change was to uncooment the color line, with no effect.
I've been looking for more information on this on other forums/FAQ's, HPW.TOs, etc but i couldn't find nothing :(](*,) 
Any suggestions?
Thanks a lot!

---

### Post by Sonic Alpha on 2006-07-19
[This]("http://users.bigpond.net.au/hermanzone/p15.htm") has some information on how to change your GRUB colours, you may find it of some use :)

---

### Post by ososxe on 2006-07-19
Thanks a lot, Sonic Alpha!!!
I'll try it as son as i get home. Too bad it seems i'll have to disable the splashimage to get some colors in the menu..

---

### Post by K0LO on 2006-07-19
You don't need to disable the splash screen to get colors to show up in the GRUB menu.

Just edit the line that you uncommented in your /boot/grub/menu.lst file (the "color" line near the comment "Pretty colors")

I use the following line:
```
color white/blue yellow/blue
```

Here's one for Ubuntu colors:
```
color white/brown yellow/brown
```

For other color choices, here are the details from the GRUB documentation so that you can experiment:
[http://www.gnu.org/software/grub/manual/grub.html#color]("http://www.gnu.org/software/grub/manual/grub.html#color")

---

### Post by ososxe on 2006-07-19
Thanks, Kolo!
That's what I tried, but with the standard colros that come on the line

color cyan/blue white/blue

And it was even worser that before, there was no "darker shade of black" on the menu.
Anyway, I'll try with different colors, i don't need it to be pretty, just to be easy to see what's the highlighted option.
Thanks!

---

### Post by K0LO on 2006-07-19
Good!

By the way, to make it easier to experiment with different colors, you can do the following. It will save you the time and trouble of editing the file, rebooting, looking at the changes, re-editing, rebooting, etc...

When the GRUB menu is displayed, press "ESC" to stop the timer. Then look at the displayed GRUB hints. You can type a "c" to enter the GRUB command line. From there, you can type the desired color command. For example, if you then type:

```
color white/brown yellow/brown

```
followed by "Enter", you can then see how this will look by pressing the "ESC" key to go back to the main GRUB menu. If you don't like these colors, type "c" again for a new command line and try another color combination. Keep trying until you find the combination that you prefer, write it down and then start up into Ubuntu and go edit the /boot/grub/menu.lst file to make your change permanent.

---

### Post by ososxe on 2006-07-19
Thanks everyone for your help, i've managed to get pretty colors on the menu list, but unfortunately i wasn't able to make it work with the splash image.
But at least now i can easily see what i'm going to boot up!:)

---

