---
title: "Suddenly lost xserver"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Emma E on 2008-01-01
My daughter booted up her otherwise faithful computer with Ubuntu 6.06. It goes thru the whole boot-up process, but before it gets to the pass word screen it gives an error message "Failed to start X server ( your graphics interface)...". In my glopping around at the command line (can you tell that I'm an old gal from DOS) I get the error message that it cannot find xserver. I realize that there isn't much info here, but I am hoping this is a starting point. Any help would be appreciated

EEN

---

### Post by empthollow on 2008-01-01
try typing 
```
startx
``` 
at the command line and look for an error message.  there should be some info as to why the xserver didn't start.

---

### Post by SOULRiDER on 2008-01-01
If the xserver isnt installed for some reason the easiest thing to do is reinstall the ubuntu-desktop package.

```
sudo aptitude install ubuntu-desktop
```

After that reboot and youre all set. If for some reason the resolution doesnt work correctly or xorg doesnt want to start due to some errors, reconfigure it by using

```
sudo dpkg-reconfigure xserver-xorg
```

Good luck and post if you need more help.

---

