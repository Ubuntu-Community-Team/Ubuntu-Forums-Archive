---
title: "Caps Lock does not work"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by Tahir on 2007-03-02
I installed ubuntu and my (USB) keyboard worked but the caps lock key on it didn't.  My fix was this:

- open /etc/X11/xorg.conf 

- go to the line  

```
Option		"XkbLayout"	"uk"
```

and replace it with this:

```
Option		"XkbLayout"	"gb"
```

and it is thus fixed!!!

---

### Post by mgmiller on 2007-03-02
The caps lock problem is a little weird.  
You can look in System>Preferences>Keyboard and look in the layouts tab at the keyboard model, to see if your keyboard is listed and change to it, there are a number of different Microsoft keyboards listed.  Also in the Layout Options tab are choices for the caps lock behavior.  

If that fails, try plugging in the keyboard with a USB to PS2 adapter and see if it works.

As far as the Firefox spell check, if you see the red line, it's working.  Just right click the underlined word and you will see a list of possible correct spellings, as well as the language chooser and etc.

---

### Post by Tahir on 2007-03-03
The problem is resolved, read the original post.

---

