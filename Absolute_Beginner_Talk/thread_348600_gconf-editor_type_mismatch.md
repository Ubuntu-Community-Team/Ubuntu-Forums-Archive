---
title: "gconf-editor type mismatch"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by Gill Bates on 2007-01-29
I was perusing the desktop doc when I got to the section that said use this editor, click on apps, natulus, desktop and then click on home_icon_visable to put it on your desktop.  I accidently clicked on home_icon_name and set it to zero which creates the type mismatch error.  It doesn't seem to bother anything but I would like to set it back to <no_value> or even give it some name but it will not let me set it back or change its type from integer.  Could someone show me the way?  Thanks.

---

### Post by riven0 on 2007-01-29
Well, I've just checked my configuration, and when I went to home_icon_name's Edit Key, I see it is also set to **integer** with the value of **0**, so I think you have it set correct. Just make sure it's not checked off.

---

### Post by bapoumba on 2007-01-29
Hi,
this is just for the string that is displayed below your /home icon on the desktop. You can set it to your login for ex, clicking on the space right to the key itself. You should get a box to fill out.

---

### Post by Gill Bates on 2007-01-29
After reading your comments I went back and started clicking again.  Eventually I right clicked and clicked on unset key.  The key went away and would not come back.  So I closed the gconf-editor and then reopened it.  The key was back and set back to <no-value> again.  I clicked on it and it did say zero but when I cancelled it it stayed OK.  So this time I changed it to a string and then typed "home" in the value field and it saved without an error.

So I guess the moral is if you save a key (click on ok) with the wrong datatype causing a type mismatch you need to right click it, exit the editor and then reenter the editor.

---

