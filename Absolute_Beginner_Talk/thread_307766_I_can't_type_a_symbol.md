---
title: "I can't type a symbol"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2006-11-27
I can't type "\"! The keyboard type other symbol,"<". I think is the layout problem but I don't know which layout should I use. How to fix it?

---

### Post by junglepeanut on 2006-11-27
I am not sure, but I am interested in figuring out how to fix keyboard (will be using a danish keyboard again soon), obviously when we do 
```
sudo dpkg-reconfigure xserver-xorg
``` it allows us to change keyboard layout, there is probably an easier way. I think we need to first figure out which keyboard you have.

So which do you have? Here is a link with lots of types.

[http://en.wikipedia.org/wiki/International_keyboard_layouts](http://en.wikipedia.org/wiki/International_keyboard_layouts)

---

### Post by junglepeanut on 2006-11-27
In gnome

[http://www.gnome.org/learn/users-guide/latest/prefs-keyboard.html](http://www.gnome.org/learn/users-guide/latest/prefs-keyboard.html)

---

### Post by junglepeanut on 2006-11-27
Copy and paste from dpkg-reconfigure xserver-xorg (note before this it has a autoconfigure, but I am guessing auto already went wrong for you.)

> Package configuration                                                           
                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474; For the X server to handle the keyboard correctly, a keyboard layout      &#9474;  
 &#9474; must be entered.  Available layouts depend on which XKB rule set and      &#9474;  
 &#9474; keyboard model were previously selected.                                  &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Experienced users can use any layout supported by the selected XKB rule   &#9474;  
 &#9474; set.  If the xkeyboard-config package has been unpacked, see the          &#9474;  
 &#9474; /etc/X11/xkb/rules directory for available rule sets.                     &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Users of U.S. English keyboards should enter "us".  Users of keyboards    &#9474;  
 &#9474; localized for other countries should generally enter their ISO 3166       &#9474;  
 &#9474; country code.  E.g., France uses "fr", and Germany uses "de".             &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Keyboard layout:                                                          &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; us_______________________________________________________________________ &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                  <Ok>                                     &#9474;  
 &#9474;                                                                           &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  
                                                                                
                                                                                


---

### Post by oliviacond on 2006-11-27
nevermine. I found the "\" already. The key is at ~#. My keyboard is too freak.

---

