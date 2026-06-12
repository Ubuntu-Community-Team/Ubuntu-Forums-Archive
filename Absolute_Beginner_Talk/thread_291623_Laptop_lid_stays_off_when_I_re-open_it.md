---
title: "Laptop lid stays off when I re-open it"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by dolphinsonar on 2006-11-02
I am using a Dell inpsiron B130, and often (not always) when I close the lid it stays off after re-opening it.

It reminds me of the refrigirator light, is it off when the door is closed, REALLY?

Well the screen goes off when I close the lid, but when I open it again it stays off.  Sometimes.

I have tried turning any screensaver locking functions off, to no avail.  The only way I can get it back on again is by hitting F1 then F7.  The commandline login screen shows up when I hit F1, that is enough to jog it back on.

Any ideas how I can get this to happen automagically without hitting F1 and F7 each time this problem occurs?

---

### Post by theicyj on 2006-11-02
You could check out System -> Preferences -> Power Management.  You can change the actions your laptop will take when you close the monitor there.  Not sure if that helps. :)

---

### Post by &#12465;&#12452;&#12488; on 2006-11-02
If it's like that, then it seems like it's an xorg problem, at least. On my Inspiron 6400, it's far worse; the screen turns off, but refuses to go on again before rebooting. I switch to tty1 and press CTRL+ALT+DEL a couple of times. :/

---

### Post by DSn0wMan on 2006-11-02
It is possibly suspending itself. Usually a tap on the power button will bring it back. Previously my Dell Inspiron would not come out of suspend due to problems with the ati card, and or driver. This seems to be fixed with the new opensource radeon, and ati drivers in edgy.

---

### Post by jordanmthomas on 2006-11-02
My computer did the same thing for the longest time, and the only way I could stop it from happening was to disable gnome-power-manager from starting up.  

If your screen isn't locked, you can try pressing Alt + F2 and (blindly) typing ```
xset -display :0 dpms force on
```

I ended up mapping my keyboard's menu button to run that command.

---

### Post by starlily on 2007-02-15
I had this problem too, I tried a lot of things, but the fix was really simple.

/etc/acpi/lid.sh is *BROKEN*

I replaced it with a much shorter version I found here on the forums, and all is well.

There are MANY posts about lid.sh being broken in a lot of ways in Edgy. Will someone who knows how please put a fixed version in the release updates? This was one of the very few things that made my install less than perfect.

Lily

---

