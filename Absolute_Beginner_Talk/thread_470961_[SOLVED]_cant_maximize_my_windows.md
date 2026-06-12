---
title: "[SOLVED] cant maximize my windows"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Fanin on 2007-06-11
every time i open a program or a folder in Ubuntu i cant see the top of it. i have to right click on the panel every time i need to maximize, minimize or close a window

i don't know how to explain it in any other way, hope you understand
please help :(

---

### Post by starcraft.man on 2007-06-11
> **Fanin said:**
> every time i open a program or a folder in Ubuntu i cant see the top of it. i have to right click on the panel every time i need to maximize, minimize or close a window

i don't know how to explain it in any other way, hope you understand
please help :(

Have installed Beryl/Compiz? Or have you modified Metacity in any way? Do you actually have the title bar for the window and just not the buttons? Or you don't even have the titlebar... please be a bit more specific. The buttons don't disappear unless something modifies them.

---

### Post by limelightos on 2007-06-11
try changing the display size

go system>admin>screen resolution and change it to 1024x768

---

### Post by Fanin on 2007-06-11
> **starcraft.man said:**
> Have installed Beryl/Compiz? Or have you modified Metacity in any way? Do you actually have the title bar for the window and just not the buttons? Or you don't even have the titlebar... please be a bit more specific. The buttons don't disappear unless something modifies them.

there is no title bar at all.. (sorry, forgot what it was called)
and no, i have not installed Beryl\Compiz nor modified Metacity in any way

---

### Post by limelightos on 2007-06-11
have you tried ALT+dragging the main part of the window?

---

### Post by phr0ze on 2007-06-11
THis isn't a sure fix, but you could bring up the theme manager and try applying a new theme to see if it clears up. Then go back to your original theme.

---

### Post by Fanin on 2007-06-11
> **limelightos said:**
> have you tried ALT+dragging the main part of the window?

yes, but i want the title bar back.. its gone
btw thanks for the tip.. didn't know that :D

---

### Post by limelightos on 2007-06-11
can't help you if it's completely gone try reinstalling...

---

### Post by Fanin on 2007-06-11
> **phr0ze said:**
> THis isn't a sure fix, but you could bring up the theme manager and try applying a new theme to see if it clears up. Then go back to your original theme.

tried every theme, but it didn't work:(

---

### Post by Fanin on 2007-06-11
> **limelightos said:**
> can't help you if it's completely gone try reinstalling...

don't want to, if there is another way.:p

---

### Post by starcraft.man on 2007-06-11
This is weird. Usually there's a reason it disappears. I'm gonna assume some service Metacity relies on failed and thus ya lost it. Open any terminal (Applications > Accessories > Terminal) and paste this in:

```
sudo /etc/init.d/gdm restart
```

That will restart the display manager without rebooting. Tell me if it gets fixed when it restarts, be patient for it.

---

### Post by Fanin on 2007-06-11
> **starcraft.man said:**
> This is weird. Usually there's a reason it disappears. I'm gonna assume some service Metacity relies on failed and thus ya lost it. Open any terminal (Applications > Accessories > Terminal) and paste this in:

```
sudo /etc/init.d/gdm restart
```

That will restart the display manager without rebooting. Tell me if it gets fixed when it restarts, be patient for it.

this is weird, terminal wont start.. just a white square with nothing on it
there seems to be something wrong with everything. do you think i should maybe just reinstall feisty?

---

### Post by starcraft.man on 2007-06-11
> **Fanin said:**
> this is weird, terminal wont start.. just a white square with nothing on it
there seems to be something wrong with everything. do you think i should maybe just reinstall feisty?

Did you enable desktop effects? White screen at terminal screen usually means to me that a 3d window manager is being used without proper drivers... if this is the case you need to turn it off from the menu you turned it on with. You must not have installed drivers and thus have problems.

---

### Post by Bluecircle on 2007-06-11
definetly sounds like a dekstop effects problem. I had this happen before.

From a console try:

```

sudo apt-get remove desktop-effects

```

That might work.

---

### Post by Fanin on 2007-06-11
Ubuntu wont even start now.. I'm in Windoze now.
never mind. i think I'll just reinstall Ubuntu, and try not to do anything stupid
don't really care what it takes, i just can't take windoze anymore :mad:

thanks anyways for helping me!

---

