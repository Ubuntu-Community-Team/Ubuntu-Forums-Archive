---
title: "Can't change pointers"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Zero Prime on 2007-10-30
I'm having trouble with pointers.  I have Gutsy installed and I know that I need to go to themes/pointers.  The problem is when I change to a new pointer theme the pointer changes in an application, such as Firefox.  When I go back to the desktop I end up with the stock pointer.  Does anyone have a fix for this?

---

### Post by Zero Prime on 2007-10-31
bump

---

### Post by Zero Prime on 2007-11-02
So....Does no one know how to fix this?

---

### Post by AndrewTheGoose on 2007-11-03
I just experienced this today, and it coincided with installing Advanced Desktop Effects Settings (compizconfig-settings-manager in Synaptic), although I can't be sure this was the issue as I was fiddling around with themes at the same time.

Anyway, I discovered that if you:

1) Go to System > Preferences > Advanced Desktop Effects Settings;
2) Go to the "General Options" section,
3) Under the "General" tab, there is an entry called "Cursor theme", which for me was set to "Human".
4) Clear this box (I actually used the 'X' button to the right of the field), and all should be good.

If you don't have "Advanced Desktop Effects Settings" installed, I think you can do this in gconf-editor (Alt-F2, and run gconf-editor). I think this setting corresponds to the /apps/compiz/general/allscreens/options/cursor_theme key.

Good luck!

P.S. My first post! Woohoo!

---

### Post by Zero Prime on 2007-11-03
Your first post and the right answer!!!!  Thank you so much.

---

### Post by gurth4ng on 2008-01-05
hehe that solved it, thx a lot ;)

---

### Post by darylb on 2008-01-11
Unfortunately this didn't work for me. I permanently have the black pointer and Human isn't an option for me in the theme pointer settings. I removed compizconfig-settings-manager (including config) but that didn't help the situation. I should also note that I'm not actually using compiz,  have effects disabled so I'm using the normal metacity WM.

I found this however which indicates the Human pointer theme is now obsolete :(
[http://ubuntuforums.org/showthread.php?t=525989](http://ubuntuforums.org/showthread.php?t=525989)

---

