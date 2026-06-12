---
title: "Complete school-boy error"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by cj2008 on 2008-03-15
... am embarrassed to even post this one, such a school-boy error ...

I've just installed Ubuntu and tried to change the screen resolution... You've guessed it - I b&lls'ed it up and can't change it back because the screen is too messed up for me to get back into the menu item...

What should I do?

---

### Post by dokdoom on 2008-03-15
Have you ever made a back up of your xorg.conf? If not you can just dpkg-reconfigure xserver-xorg and it well give you a fresh xorg.conf. But before making changes to it again make sure to back it up.

---

### Post by cj2008 on 2008-03-15
nope - no back-ups (literally installed it today)...

Perhaps I could uninstall and re-install again?

---

### Post by forrestcupp on 2008-03-15
How is it messed up?  Is it too big to fit on your screen?  If so, sometimes you can just move your mouse to the edge of the screen and it will move the screen.

If not, try to reconfigure X, like was already said.  To do that, reboot your computer and at the GRUB menu, choose the one that says Recovery Mode.  When you get to the prompt, type
```
dpkg-reconfigure xserver-xorg
``` 
And follow the on-screen instructions.

Then when it's done, type
```
exit
```
and hopefully you'll be able to start into a good desktop

---

### Post by eragon100 on 2008-03-15
If you move your cursor up to the edge of the screen, it shows the part you can't see because of the small resolution. Find your way to the upper left part of the screen, then system -> preferences -> screen resolution. If ypu can't see that button in preferences, just scroll down across the screen until you see the entire preferences menu. It should open the resolution screen in the middle of the sreen, so scroll down and to the right to find it if you don't see it immediately. Then, select your resolution from the drop-down list and click apply. That's it! :popcorn:

It seems three people have already posted while i was typing this message lol

---

### Post by forrestcupp on 2008-03-15
And sometimes just rebooting will cause the resolution to set correctly.

---

### Post by cj2008 on 2008-03-15
Thanks a lot guys - fixed now.

Chris

---

### Post by prshah on 2008-03-15
> **cj2008 said:**
> ... am embarrassed to even post this one, such a school-boy error ...

I've just installed Ubuntu and tried to change the screen resolution... You've guessed it - I b&lls'ed it up and can't change it back because the screen is too messed up for me to get back into the menu item...

What should I do?

Use Ctrl+Alt+(numpad) "+" and/or ctrl-alt-numpad "-" to cycle through available resolutions until you find your original one.

Or:

Switch to Ctrl+Alt+F1 (tty), login as usual and ```
cd && sudo cp /etc/X11/xorg.conf . && sudo cp -f /etc/X11/xorg.conf~ /etc/X11/xorg.conf
```

Switch back (Ctrl+Alt+F7) and restart X (Ctrl+Alt+Backspace). if it still doesnt work, put back your original xorg.conf with ```
cd && sudo cp -f xorg.conf /etc/X11/xorg.conf
```

---

