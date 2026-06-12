---
title: "How to create menu launcher for program in Wine?"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by t2000kw on 2007-05-24
I installed a Windows program using Wine and it didn't appear in the Wine menu. I can open and run it with Winefile but that's not very convenient. 

I tried copying a launcher from the Panel and replacing the directory and filename with the new one but that didn't work.

Any instructions somewhere on how to do this, or how to put one in the "proper" place in the applications/wine menu?

---

### Post by Sparkster185 on 2007-05-24
You should be able to just add a new menu item and enter the command that WINE would execute to get the application running.

---

### Post by t2000kw on 2007-05-24
Up until  now Wine has installed the shortcuts needed to run the few Windows programs I don't want to part with, but not with this one. 

As I mentioned, I copied the same launch information from another Windows program that the shortcut on the Panel works and tried to adapt it to the new one, substituting only the new directlry and executable. 

That didn't work, unfortunately. 

I'm missing something important here.

---

### Post by t2000kw on 2007-05-24
I get a bad or missing system file message when trying to do what I just wrote about, and the message won't go away. It toggles between it and another related message and I have to use Xkill to get rid of the error message. 

But I CAN run it from within Winefile, which means it should be possible to make a menu for it somewhere.

---

### Post by t2000kw on 2007-05-24
I should add that this isn't a showstopper, but it would be nice to learn how to do this as I'm sure there will be a few other programs I'll need to do this with.

---

### Post by Znupi on 2007-05-24
Use this as the command for the launcher:
```

wine /path/to/windows/program.exe

```
or:
```
env WINEPREFIX="/home/<user>/.wine" wine "/path/to/windows/program.exe"
```

---

### Post by t2000kw on 2007-05-24
I had already tried the second one by copying another one that worked and changing the path and executable name, but I just now tried the first one above and I get nothing at all. No errors, either.

---

### Post by Znupi on 2007-05-25
Strange. It works for me.

---

