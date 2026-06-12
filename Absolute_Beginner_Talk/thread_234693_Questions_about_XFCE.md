---
title: "Questions about XFCE"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by lemonsCC on 2006-08-11
I just installed Xubuntu 6.06, this is my first experience so far with XFCE, and has been good thus far.    MY questions are as follows:

1)  I try to right click on the desktop to create shortcuts and nothing happens.  (Right click works in folders)  Is this not possible in XFCE?
--I also cannot right click in the applications menu.

2)  I do not like the applications menu so i switched it with the "XFCE Menu"  there is an option to change the contents and order of the items in this menu but when I do my changes are not reflected in the menu.

---

### Post by goatflyer on 2006-08-11
xfce does not normally go for icons on the desktop, however I have found that if you put symlinks in your ~/Desktop directory, the xfce desktop will show icons next time you restart the window manager.  It will not refresh anything if you make changes during your sesssion.

In terminal, do:

```

cd ~/Desktop
ln -s /whatever/folder/i/want MyFolder
exit

```

(change path to point to something real)

Next time you start, you should see an icon.

---

### Post by lemonsCC on 2006-08-11
I figured that out thank you!

Any way to chage the "XCFE Menu"  and have it keep the changes?

---

### Post by goatflyer on 2006-08-11
According to the release notes, xfce4-menueditor might mangle your menu, depending on how much you try to push it.

Try using simple changes one at a time.
Confirm that your change is actually being saved by peeking at your file:

~/.config/xfce4/desktop/menu.xml

What are you trying to add?

---

### Post by lemonsCC on 2006-08-11
I am trying to get rid of the about XFCE, terminal, and web browser, trying to move run program

---

### Post by lemonsCC on 2006-08-11
There is no trash/recycle bin in XCFE?  all deletions are permenant?

---

