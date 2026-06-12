---
title: "Compiz unloads keyboard shortcuts?"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by FuzZy2006 on 2006-07-20
From System -> Preferences -> Keyboard shortcuts   I have assigned Ctrl+T to the terminal. I have the Ctrl+Alt+Del which opened a process manager (I installed it via automatix). Now I installed Compiz (wow, it's great) bot all those keyboard shortcuts are gone. How can I reactivate them?

---

### Post by Flavian on 2006-08-06
Same problem here, would be glad to get some help!
Flo

---

### Post by richbarna on 2006-08-06
Yep!! This is a common problem, I had it when I first used xgl/compiz.
A work-around is to open your terminal and enter this command with your country code ie "**us**", mine is **es** for Spanish keyboard :-

> xmodmap /usr/share/xmodmap/xmodmap.**es** 
Change the last part to your particular country map.

You can also check your keyboard config in xorg like this:-

Open your terminal and type this
> gksudo gedit /etc/X11/xorg.conf

Enter your password and Gedit will open (don't worry about the error message, it's a known bug).

Now look for this section (keyboard) :-
> Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "**es**"
EndSection

And change it to your country map if it is wrong, SAVE and EXIT.

---

