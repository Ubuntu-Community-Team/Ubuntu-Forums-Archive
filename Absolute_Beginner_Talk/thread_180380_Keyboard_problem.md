---
title: "Keyboard problem"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by KarmaKing on 2006-05-22
Hello all,

So as you can read I am from the US living in Hungary.  Having said that I have a Hungarian keyboard with many keys mulit-layered (I think is the correct term).

The problem is with some keys I have to press ctrl+alt + key to get certain characters such as the at symbol for e-mail addresses.
everyhing else works fine and there was no problem during install.

my wife is about to beat me over the head becuse she still is resisting the move to Linux and wants everything now:twisted: ...so here I am.:p 

Thanks

kk

---

### Post by meborc on 2006-05-22
can you post your /etc/X11/xorg.conf file (the part with keyboard) so we could get an idea of which layout are you using and which variant... ;)

---

### Post by KarmaKing on 2006-05-22
[QUOTE=meborc]can you post your /etc/X11/xorg.conf file (the part with keyboard) so we could get an idea of which layout are you using and which variant... ;)[/QUOTE]

would be glad to....how?:mrgreen:

---

### Post by richbarna on 2006-05-22
Open your terminal/konsole and type :-
> sudo gedit /etc/X11/xorg.conf
Then copy and paste it.

---

### Post by KarmaKing on 2006-05-22
thanks richbrown here it is

> 
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"hu"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"


---

### Post by richbarna on 2006-05-22
It looks ok to me,
I am having the same problem with a Spanish keyboard. (Alt Gr) doesn't work.
Same as you, problems getting the "at" in email addresses.
Still searching for an answer, if I find something I will post back.

---

### Post by KarmaKing on 2006-05-22
bump

---

### Post by S{yndrom}e on 2006-05-22
have you tried messing around with System-->prefrences-->keyboard?

---

### Post by Sef on 2006-05-22
Have you set your keyboard to US or to Hungarian model?

---

### Post by S{yndrom}e on 2006-05-22
Will it make a difference if he sets his keyboard to umm lets say U.K in his prefrences even if it a hungarian model?

---

### Post by Sef on 2006-05-22
> Will it make a difference if he sets his keyboard to umm lets say U.K in his prefrences even if it a hungarian model?

Yes, it will.  Symbols are set differently in different countries.  For example, on my Korean keyboard, the = sign is set below the + sign.  When I downloaded a version of Knoppix, then only available in German, the = sign was above the 0.

---

### Post by KarmaKing on 2006-05-22
it is most definitely set up as HUngarian.  I have looked through the preferences, but haven't made head-or-tales of most of it.[img]http://img.photobucket.com/albums/v640/vendion/1ptgno.gif[/img]

---

### Post by Sef on 2006-05-23
Try this:

> After all, if you are using the Czech, Croatian, Serbian, Slovenian, or Hungarian keyboard layouts, than CTRL+ALT+V is also ALTGR+V, and that is the keystroke combination you use to get the @

I hope it helps.

[The @ how to]("http://blogs.msdn.com/michkap/archive/2006/04/17/577196.aspx")

---

### Post by KarmaKing on 2006-05-23
@@@@@@@@@@@@@@@@

got it.

went to keyboard preferences and chose third layer choosers and chose one.

---

### Post by Sef on 2006-05-23
Glad you got it!  Always a good feeling.

---

