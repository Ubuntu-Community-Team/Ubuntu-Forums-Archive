---
title: "[SOLVED] I've changed my login window but I'm still getting a sandy brown screen"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-11-10
Been into admin login window and changed the login window to a nice blue theme but...

I get a full sandy brown screen before and after login.

Not sure where to change this.

---

### Post by NilsE on 2007-11-10
The same place on the local tab there is a background color option.

If that does not work you can do a quick fix by editing the hard coded BACKCOLOR in /etc/gdm/PreSession/Default. Look for #dab082 @ bottom.

Here is another way with the same file

[http://ubuntuforums.org/showthread.php?t=597282](http://ubuntuforums.org/showthread.php?t=597282)

---

### Post by philinux on 2007-11-10
Cheers, did the local tab thing and that changes the screen colour before the login, then you get back the full screen of sand before my dektop wallpaper shows up. :(

---

### Post by philinux on 2007-11-10
Ok - followed the link did the edit -marvellous.

Shame to have to resort to terminal to fix something like that though. :confused:

---

### Post by Tux.Ice on 2007-11-10
You cannot do everything in gui like windows (i leraned that in my first days of ubuntu)

---

### Post by gsiliceo on 2007-11-10
but this is a bug, because in feisty if you changed the color with the admin login window tool it would actually change and now in gutsy is not working.

---

