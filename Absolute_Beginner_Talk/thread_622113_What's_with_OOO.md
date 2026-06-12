---
title: "What's with OOO??"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by InsertNameHere on 2007-11-24
I installed a new theme from gnome-look
[http://www.gnome-look.org/content/show.php/Smoked+Glass+v0.9.5?content=27141](http://www.gnome-look.org/content/show.php/Smoked+Glass+v0.9.5?content=27141)

and everything works well until I opened OOo all the buttons stopped showing, so I went to appearance and checked the settings, they were suppose to show.

Buttons from Gedit and Evolution shows fine

Also on my dock OOo displays a general icon instead of the OOo icon.

Can anyone tell me how to get it back?

Thanks for your time

Edit: Here's a screenshot of my current OOo

---

### Post by andyanderso on 2007-11-24
What docking program are you using -- Kiba? AWN?

on Kiba and in the gnome panel launchers you can right click on the launcher and manually select the path for the correct icon...I just do a search for the icon I want then remember where it is then use that location as the icon path for the launcher...usually it is something like /usr/share/pixmaps/qgis-icon.xpm

good luck.

andy

---

### Post by gvoima on 2007-11-24
OOo buttons doesn't support all the icon themes what you use. So instead of the current, I suggest that you use the OO default ones, or human (only in OO I mean). You can change them in the OO options, view part.

---

### Post by InsertNameHere on 2007-11-24
Thanks, I'm using AWN but I found a similar property, the icon is fine now but what about the other problem regarding the buttons.

---

### Post by InsertNameHere on 2007-11-24
Thanks that solved the buttons as well.

A side question, how can I make the paper in the middle white instead of the greyish color that comes with the theme?

Thanks for all your support.

---

### Post by InsertNameHere on 2007-11-24
And also presentation refused to show the correct layout and the buttons are sortta inverted. here's a screen.

---

### Post by ryanVickers on 2007-11-24
I've found it's just stupid like that - only works with the human default theme... :(

---

### Post by InsertNameHere on 2007-11-24
So......

I'll have to switch themes everytime I use presentation?

---

### Post by Krydahl on 2007-11-24
Not so - but although openoffice shows several themes in its options -> openoffice.org -> view, infact only the default one is installed in ubuntu. If you change your Gnome theme sometimes OOo decides it ought to be using a different theme too - but since it hasn't got it, it falls back to using text. You can download OOo themes and then you'll get icons back.

As for the colours - if you go to tools -> options -> openoffice.org -> Appearance you'll find settings that allow you to override the default colours and set whatever you like.

---

### Post by ryanVickers on 2007-11-24
I've been working on ways to try and run it as different users, but it's not going so well, so just go sudo ooffice -writer to use root, and thus it's default human there :)

**Just a note of caution - it's just a word processor, but your still running as root when you do this!**

---

### Post by InsertNameHere on 2007-11-24
The sudo trick works really well.
The color trick works, but presentation is screwed up.

I'll create an icon on my desktop right now for the rooted OOo.

I hope the devs or someone fixes this so OOo stays human no matter the themes.

Thanks for everything~!

---

### Post by Krydahl on 2007-11-24
It's easy enough to force OOo to stick with a particular icon set - go to tools -> options -> OOo -> and change the icon style from "Automatic" to whatever one you prefer.

---

### Post by InsertNameHere on 2007-11-24
Yes, but if I choose human, the buttons look inverted and presentation still wont work....

---

### Post by ryanVickers on 2007-11-24
it's just something they're going to have to work at.  If I remember correctly, it's written in, or at least very dependent on java, and I think this is the first thing they need to fix :p  Once it's written in C++ and runs on GTK, then it will truly be a quality product, but until then, it's only half-baked... :(

---

