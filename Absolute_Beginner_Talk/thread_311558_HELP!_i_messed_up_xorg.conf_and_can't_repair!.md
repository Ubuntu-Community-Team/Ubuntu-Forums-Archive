---
title: "HELP! i messed up xorg.conf and can't repair!"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Sonic Reducer on 2006-12-03
i was trying to 
[make my MX100 mouse work](http://tinyurl.com/y6mvp3), and i guess i messed up xog.conf. i copied the code exactly as shown to make a backup, and i copied the code exactly as shown to revert to it, but it didn't work.

can i repair my installation with the install CD?  got the official 64-Bit one that i am booting with it as i type this (typing on my laptop). i really hope i don't lose everything, even though i don't have much on it.

please help me!

---

### Post by aysiu on 2006-12-03
Press Control-Alt-F1 to get to a terminal

Log in

Then type ```
sudo dpkg-reconfigure xserver-xorg
``` Answer the questions as best you can. If you don't know the answer, just press **Enter** to go with the defaults.

Finally press Control-Alt-F7 to get back to the GUI and then Control-Alt-Backspace to reset the X server.

---

### Post by tiptip on 2006-12-03
I dont think 
```
sudo dpkg-reconfigure xserver-xorg
```
is needed here since it will change all his xorg.conf

He said he works on his mouse so i guess he need to use
```
sudo pico /etc/X11/xorg.conf
```
and rewrite the mouse section again, this is a working one :
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection
```
just be sure that the **Identifier "Configured Mouse"** is matching to the one in the **Section "ServerLayout"**.

P.S.
- _[COLOR="Red"]**ALWAYS MAKE A BACKUP BEFORE YOU CHANGE XORG.CONF !!!!!!!!!!111ONEONE**[/COLOR]_

---

### Post by Sonic Reducer on 2006-12-03
I'm looking right now, but do you know of a guide to setting this up? i don't know which video drivers to try, etc.

---

### Post by Sonic Reducer on 2006-12-03
oh hey, by the way, should there be text in the file already when i type ```
sudo pico /etc/X11/xorg.conf
```? because there isn't. did that happen when i tried the first suggestion?

---

### Post by CatKiller on 2006-12-03
> **Sonic Reducer said:**
> oh hey, by the way, should there be text in the file already when i type? 

Case is significant. That's **X**, not **x**. Possibly that's why your backup didn't work?

---

### Post by tiptip on 2006-12-03
> **Sonic Reducer said:**
> oh hey, by the way, should there be text in the file already when i type ```
sudo pico /etc/X11/xorg.conf
```? because there isn't. did that happen when i tried the first suggestion?
There must be a text when you write that, make sure you write BIG 'X' and not just 'x'.

---

### Post by Sonic Reducer on 2006-12-03
```
sudo pico /etc/X11/Xorg.conf
```

didn't work either. should i just reinstall? i don't have anything life or death on the rig, ad it will give me a fresh start to try the mouse trick FIRST THING so i don't lose anything again

---

### Post by aysiu on 2006-12-03
> **Sonic Reducer said:**
> ```
sudo pico /etc/X11/Xorg.conf
```

didn't work either. should i just reinstall? i don't have anything life or death on the rig, ad it will give me a fresh start to try the mouse trick FIRST THING so i don't lose anything again Please at least try ```
sudo dpkg-reconfigure xserver-xorg
``` before you reinstall!

It will re-create your /etc/X11/xorg.conf file afresh.

---

### Post by tiptip on 2006-12-03
As aysiu said , go for the
```
sudo dpkg-reconfigure xserver-xorg
```
but this time backup your xorg.conf before you start messing it

---

### Post by lou1967 on 2006-12-03
Aysiu, I have a generic (inland) mouse, 5 button including the scroll wheel. help...I just want to get the back and forward option installed for my mouse. Every time I ask I get you have to look it up or search for an answer but there is no fix I can find. I cant be the only user with a generic mouse.

---

### Post by Johan! on 2006-12-03
I don't know what's in your xorg.conf file now, but these are my mouse settings:

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option	   "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

```

I think you need to change all buttons settings.
NB: Linux sees the scroll-wheel as 2 separate buttons, so a mouse with 3 normal buttons, a scroll wheel and 2 side buttons is a 7 button mouse.

---

### Post by tiptip on 2006-12-03
THX Johan!
that worked great for me 

you are a :KS

edit :
it worked great in **Firefox** but didnt make any change at **Konqueror**.
Anyone knows how to active the back button while working with Konqueror as well ?

---

### Post by Sonic Reducer on 2006-12-03
so i kept on truckin through the **sudo dpkg-reconfigure xserver-xorg** and kept all defaults. it booted to the desktop and i copied my backup file to the original. good as new... or good as old...

wanna hear how nearly completely dependant on a GUI i am? i forgot i saved the backup to the desktop! oh well. i ctrl+alt+backspace'ed and restarted X, everything is honky-dory now.

thanks everybody! i'm going to retry the MX1000 hack now

---

