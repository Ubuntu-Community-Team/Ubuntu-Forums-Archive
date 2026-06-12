---
title: "Two things in terminal that would make my life easier"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by nikoPSK on 2007-11-16
So two things: 

why doesn't terminal let me ```
Control+V
``` into the window and:
why won't it let me cd into directories that have spaces in them.

If there are any fixes/ workarounds please let me know,
Thanks

---

### Post by jordanmthomas on 2007-11-16
I'm not sure about gnome-terminal, but in konsole, you can change ctrl-v to paste in its settings.
(Odds are you can't on gnome-terminal, because that's how gnome rolls)
By default, shift + insert pastes.

To cd into a directory name with spaces, you need to escape the space character by using a \ character. ie;
```
cd ~/Desktop/some\ folder\ with\ spaces
```
OR you can put quotations around it
```
cd "~/Desktop/some folder with spaces"
```

---

### Post by Inxsible on 2007-11-16
Ctrl + Shift + V does what you want

also if you type in the first few letters of the directory or filename and then hit Tab, it will auto complete it for you, even if it has spaces it will add the appropriate escape sequences

---

### Post by nikoPSK on 2007-11-16
> **jordanmthomas said:**
> I'm not sure about gnome-terminal, but in konsole, you can change ctrl-v to paste in its settings.
(Odds are you can't on gnome-terminal, because that's how gnome rolls)
By default, shift + insert pastes.

To cd into a directory name with spaces, you need to escape the space character by using a \ character. ie;
```
cd ~/Desktop/some\ folder\ with\ spaces
```OR you can put quotations around it
```
cd "~/Desktop/some folder with spaces"
```

Thanks! I'll see if terminal has a keyboard paste option somewhere....:)

---

### Post by nikoPSK on 2007-11-16
> **Inxsible said:**
> Ctrl + Shift + V does what you want

also if you type in the first few letters of the directory or filename and then hit Tab, it will auto complete it for you, even if it has spaces it will add the appropriate escape sequences

Thanks, I edited to just plain control+v :KS

---

### Post by jordanmthomas on 2007-11-16
If you can't find it, I have found out how to change it:
```
gconf-editor /apps/gnome-terminal/keybindings
```
BEHOLD!

I trust you can figure it out from there.  :)

---

### Post by Inxsible on 2007-11-16
Altho Ctrl +Shift + V does it, you can also change the settings by going to 

Edit >>Keyboard Shortcuts. Check the Edit drop down in it and change the shortcut

---

### Post by jordanmthomas on 2007-11-16
Heh, easier than my way.  

I didn't see that menu when I used a gnome-terminal because I have the menu bar turned off and it doesn't show up in the right-click menu for some reason.

---

