---
title: "Is it feasible to make the numeric pad work in Ubuntu?"
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by Nadiral on 2005-06-27
Hi there, I need to write both in English and Spanish.  In Windows I could resort to the numeric keypad and to deadkeys.  I also need to use the em dash (alt 0151) and the angled quotes (alt 174 and 175).

Where can I map my keyboard, i.e., configure a file like XF86Config?

It seems that Emacs partially supports the alt characters, but not quite exactly as they are needed.

Is there an easy way to switch to and from different keyboard layouts?

Thanks.

---

### Post by bored2k on 2005-06-27
[QUOTE=Nadiral]Hi there, I need to write both in English and Spanish.  In Windows I could resort to the numeric keypad and to deadkeys.  I also need to use the em dash (alt 0151) and the angled quotes (alt 174 and 175).

Where can I map my keyboard, i.e., configure a file like XF86Config?

It seems that Emacs partially supports the alt characters, but not quite exactly as they are needed.

Is there an easy way to switch to and from different keyboard layouts?

Thanks.[/QUOTE]
 a) Set up a panel applet for your keyboard. This would allow you to click on it to change layouts.

or

b) You could use the English INternational layout, wich adds easy support for ñ, "ácèntôs" and stuff ;).

---

### Post by Kvark on 2005-06-27
The numpad works perfectly fine for me when numlock is active. When numlock is not active the keys on it works as arrows, page up, etc.

The following is true for swedish keyboards and ubuntu, but I have no idea if it is different for english keyboards. 

All characters with ', `, ", ^ or ~ above them can be typed by first hitting the sign above the character and then the base letter of the character. So õ is typed as ~o. (As a result it takes 2 keystrokes, ~ followed by space, to get a ~ without anything under it.)

Most other characters can be typed by holding Alt Gr (the right Alt key is called Alt Gr on a swedish keyboard) down while pressing one of the number or letter keys. Just like holding shift down gives a capital letter instead of a small one. Holding both Alt Gr and Shift gives yet another special character. For example Alt Gr+2 = @, Alt Gr+Shift+2 = ², Alt Gr+M = µ and Alt Gr+Shift+M = º.

Thats quite a lot of special characters when most of the keys got 2 of them each, in addition to the keycombo system for stuff above letters. :)

---

### Post by Nadiral on 2005-06-28
I'll try both the applet and the keyboard layout things.  Still, I think that my Linux will still be  missing  the functionality of the alt plus numeric pad combinations.

Best wishes.

---

### Post by Nadiral on 2005-06-28
Happy to hear that everything is fine with your swedish keyboard,  but mine is not faring so well.  You have put me in thinking mode, perhaps I must start by the beginning, i.e., trying to make my ctrl, alt, and meta keys to do their job (alt gr is kind of temperamental, BTW).

Best wishes.

---

### Post by Kvark on 2005-06-28
So it's not the same with english ones :(

There must be some english layout with the same functionality on the right Alt key and the '`"^~ signs. They just can't have forgotten about all the countless english speaking people when adding funny signs to keyboard layouts.

If they did forget all the english speakers then someone really needs to make a layout for it. I'm about to play around with this too. But we should first know if it has already been done.

How to make a keyboard layout: [http://docs.linux.com/documentation/04/06/03/1558258.shtml?tid=26&tid=14&tid=22](http://docs.linux.com/documentation/04/06/03/1558258.shtml?tid=26&tid=14&tid=22)

If/when there is one then it should be default. There is no drawbacks since you still got the left Alt key for normal Alt-usage. It'll be yet another nice feature to amaze newcommers with :)

---

### Post by Nadiral on 2005-06-28
Just bookmarked the link; and yes, I suppose you're right, perhaps I made a wrong turn when setting up the keboard in the installation process.

Best wishes.

---

### Post by doclivingston on 2005-06-28
I've always found the alt+numpad way of typeing characters horrible to use, having to memorise three (or is it four?) digit numbers.

If you do it a bit, but to too much adding  a character palette to the panel could be helpful. If you need to type other characters more (and don't want to use the mouse to do it) setting up a different keyboard layour would be the best bet.

---

### Post by Nadiral on 2005-06-29
Maybe I'm just too used to doing the alt thing, in addition that I know by heart the score or so that I need the most.

Best wishes.

---

### Post by bored2k on 2005-06-29
[QUOTE=Nadiral]Maybe I'm just too used to doing the alt thing, in addition that I know by heart the score or so that I need the most.

Best wishes.[/QUOTE]
 It was really hard for me to get used to **Not** using the numeric pad, but after my dad bought a Spanish Multimedia Keyboard by mistake, I love it more every minute :D

---

### Post by Nadiral on 2005-06-29
...I'm now switching keyboards, but still missing the em-dash.

Thanks again.

---

### Post by Kvark on 2005-06-29
It still really bugs me though that the right Alt shifting doesn't work on english keyboards. It is the best way to handle special characters, by far. It is soo easy and fast there is just no way to beat it. There **must** be an english keyboard layout out there somewhere that uses the right alt key.....

---

### Post by Nadiral on 2005-06-29
I have just typed "ctrl + right alt + F1", and reached the usual display, But when I try to return to the GUI,  right alt doesn't work any more, the command begs for a left alt. This combination works fine from the GUI to F1 through 6.

Right alt also lacks the funcionality of the AltGr key, that comes handy when you need a third character (spanish-keyboard-wise-don't-know-about-a-swedish-one).

I've been implementing some keyboard shortcuts in KDE Control Center, but when I try to open xmodmap a message appears that says it's unable to open the display.

Best wishes.

---

### Post by bored2k on 2005-06-29
[QUOTE=Nadiral]I have just typed "ctrl + right alt + F1", and reached the usual display, But when I try to return to the GUI,  right alt doesn't work any more, the command begs for a left alt. This combination works fine from the GUI to F1 through 6.

Right alt also lacks the funcionality of the AltGr key, that comes handy when you need a third character (spanish-keyboard-wise-don't-know-about-a-swedish-one).

I've been implementing some keyboard shortcuts in KDE Control Center, but when I try to open xmodmap a message appears that says it's unable to open the display.

Best wishes.[/QUOTE]
 You can't really do anything with Alt+Gr (like that ctrl-alt thing). The AltGr IMO is the most functional key on my keyboard, ever. Not only does it serve to have even more key shortcuts, but mixed with the Shift it does even more.

I'm sure the left Alt can't do everything the Altgr does on purpose. That way, programs don't get confused.

---

### Post by Nadiral on 2005-06-30
In KDE control center, vb., there's only Alt_L mapped; along with the Alt, Ctrl, and Shift modifiers.  It looks as if you can't add any input in this tab (Keyboard Shortcuts/Modifier Keys).

Thanks again.

---

### Post by hughh on 2007-08-26
Following the instructions under **Solution 2** on the referenced web page gives access to a ***huge*** number of special characters using the Compose key.  You can set the Compose to any of a number of keys by going selecting System &#8594; Preferences &#8594; Keyboard and going to the *Layout Options* tab and selecting *Compose key position*.

A big advantage over the Windows method is that the key combinations make much more sense, e.g. Compose+RO = ®, Compose+--- = — (the em dash that Nadiral was looking for in the first place) Compose+^2 = ², Compose+Y= = ¥, etc. (of course, I used these key combos to create the special characters shown in this post :)).

As the Debian article points out, you can even add your own multi-key combinations.

---

### Post by Wolki on 2007-08-26
You can also input a character by its unicode number in many applications py using one of the following methods:

1) press and hold ctrl-shift, then press "u", then the hexadecimal unicode number, then release ctrl-shift

or

2) press ctrl-shift-u, then the hexadecimal unicode number, then return

---

### Post by hughh on 2007-08-26
Yes, and all the characters and their hex codes can be found in the Character Map application and are listed in this document: [*[COLOR=Blue]The Unicode Charater Code Charts By Script[/COLOR]*]("http://unicode.org/charts/").

---

### Post by Wolki on 2007-08-26
> **hughh said:**
> Yes, and all the characters and their hex codes are listed in this document: [*[COLOR="Blue"]The Unicode Charater Code Charts By Script[/COLOR]*]("http://unicode.org/charts/").

Exactly. Or you could look it up in the character map.

---

