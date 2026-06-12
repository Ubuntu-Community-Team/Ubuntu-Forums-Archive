---
title: "Best Terminal for Aptitude?"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by Nunnsby on 2006-09-05
Wondering what is a good, or the best terminal application to use for Ubuntu, specifically Aptitude?

I am using SecureCRT, and have also tried Putty, but both have problems displaying the "Drop-Down" Menus in Aptitude.

Unless of course there are supposed to be "â" and "€" characters all over the place? :-k 

Any help, or advice on how to "tune"/configure the apps I have for the best apearance?

Thanks

---

### Post by taurus on 2006-09-05
Just a standard gome-terminal (Applications -> Accessories -> Terminal) is fine.

---

### Post by Nunnsby on 2006-09-05
Thanks Taurus, forgot to mention that I am coming from a Windows Environment! :( 

Any idea of what the configs are for those settings? eg VT100/etc/etc/etc?

Cheers anyway matey!

:)

---

### Post by Nunnsby on 2006-09-05
Oh, via SSH from an XP box!

---

### Post by Nunnsby on 2006-09-06
Hah Ha! Fixed!

On your Gnome Desktop, use "stty -a". This will show the current settings of your terminal display.

I found that aptitude makes use of the UTF-8 Character Encoding. Set this in your terminal app, and all is good to go.

Enjoy

Nunnsby

---

