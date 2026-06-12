---
title: "What does this mean: &quot;X System Keyboard settings differ...&quot;?"
date: 2007-11-20
forum: Apple Intel Users
---

### Post by jslmg on 2007-11-20
I am seeing this message every time I boot Ubuntu:

> X system keyboard settings differ from your current GNOME keyboard settings.

Expected was model "pc101", layout "us" and no options, but the following settings were found: model "pc105", layout "us" and no options.

Which set would you like to use?

Two choices are given to click on:

"Use X settings"
"Keep GNOME settings"

Questions:

(1) Why does this message appear?
(2) Which choice is better? (I've tried both, and neither seems to make much difference)
(3) How do I stop it from appearing?

Thanks.

---

### Post by e-tip on 2007-11-20
i0ve had i've had the same message, because my xorg.conf keyboard setting differs from my gnome keyboard settings,
you can proceede in two different ways, change your xorg.conf to have the same options of your gnome settings
change gnome keyboard settings to be the same of xorg.conf settings 
if you'd choose the first way you just need to edit your /etc/X11/xorg.conf file and change 
line ```

Option "XkbModel" "pc101"

```
 into 
[CODE]
 Option      "XkbModel" "pc105"
[CODE]
or you can go in System-->Preferences-->Keyboard and change from pc105 to pc101 option

---

### Post by jslmg on 2007-11-29
Thanks, e-tip! That change did it. It worked in system preferences, no terminal needed.

For the benefit of others looking to fix the same thing:  The thing to do was:

(1) Go to  system-->Preferences-->Keyboard. 

(2) Click the "Layouts" tab, then next to "keyboard Model," you'll see your keyboard type. If it says "Generic 105-key PC [intl]," then that's the culprit. 

(3) Click "Choose...". In that menu, look for "Generic 101-key PC." Select it, then click "OK." Logout and back in to confirm that the change worked.

---

### Post by cyberdork33 on 2007-11-29
> **jslmg said:**
> Thanks, e-tip! That change did it. It worked in system preferences, no terminal needed.

For the benefit of others looking to fix the same thing:  The thing to do was:

(1) Go to  system-->Preferences-->Keyboard. 

(2) Click the "Layouts" tab, then next to "keyboard Model," you'll see your keyboard type. If it says "Generic 105-key PC [intl]," then that's the culprit. 

(3) Click "Choose...". In that menu, look for "Generic 101-key PC." Select it, then click "OK." Logout and back in to confirm that the change worked.
There are also options for Macbook, Apple, Macintosh, etc if you have your keyboard set to use them.

---

