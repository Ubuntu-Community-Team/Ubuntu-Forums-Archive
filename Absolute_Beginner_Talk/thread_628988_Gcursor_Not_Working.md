---
title: "Gcursor Not Working"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by prodigalson666 on 2007-12-01
I went ahead and installed gcursor. To my dismay however, it seems to not be working. It worked perfectly in 7.04 and was pretty idiot proof. Now in 7.10 however, I can't do anything with it. Both the install theme and go to theme buttons are inactive, and selecting one of the default mouse themes does nothing. Any ideas? 

I get this error from the terminal when I try to run it from the terminal.

(gcursor:2260): libglade-WARNING **: could not find signal handler 'extract_theme'.

(gcursor:2260): libglade-WARNING **: could not find signal handler 'open_theme_dir'.

(gcursor:2260): libglade-WARNING **: could not find signal handler 'entry_selected'.

(gcursor:2260): libglade-WARNING **: could not find signal handler 'size_changed'.

Thanks

---

### Post by FuturePilot on 2007-12-01
Yeah, it's a bug
[https://bugs.launchpad.net/ubuntu/+source/gcursor/+bug/138491]("https://bugs.launchpad.net/ubuntu/+source/gcursor/+bug/138491")

However you can also change your cursor themes from the Appearance panel. System>Preferences>Appearance. Click the Customize button and then go to the Pointers tab

---

### Post by prodigalson666 on 2007-12-01
Thanks but I cant install anything new though.

---

### Post by prodigalson666 on 2007-12-01
Never mind read the bug fix and everything works fine,cheers!

---

### Post by aelfwyne on 2008-07-14
I guess I'm missing something basic - but I don't seem to see a fix on that bug. Someone claims they got it to work but I don't actually see any directions to fix this.

What I do see:
> I kept researching this and found a solution, First thing I discovered is that under system/preferences/appearance if you press the "customize" button on the "theme" tab, you get a new screen that lets you customize controls, color, window borders, icons and pointers. I pressed pointers and got to choose only among the default pointers -- my aero-drop pointers were not shown. So I downloaded the aero-drop tar and extracted it to my desktop. I then copied the extracted folder to /usr/share/icons. I went back to the appearance panel and now aero-drop was among the pointer options so I selected it and that was that.

is passed off as a fix.

But I'm NOT TRYING TO INSTALL A NEW CURSOR - I'm trying to switch to one of the many cursors that are ALREADY INSTALLED and showing up just fine in gcursor.

Lots of themes are showing up in gcursor - problem is it doesn't respond at all. In fact, none of the buttons except close DO ANYTHING in gcursor.

You'd figure they'd have bothered to fix such an old bug before releasing Hardy, but apparently not.

Anybody have an actual fix for this?

---

