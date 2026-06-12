---
title: "What happened to CTRL-F (Control-Find)?"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by H.E. Pennypacker on 2006-10-16
I used to be able to use CTRL-F all the time in web browsers and other applications, but not anymore.  We all know what CTRL-F (Control Find) is used for.

One day, I noticed CTRL-F was bringing up Xterm (though I don't ever recall installing it).  Now that Xterm is uninstalled, CTRL-F does nothing.  This is true for ALL applications, most notably web browsers.

How can I get Control Find (CTRL-F) back?

---

### Post by Tamil on 2006-10-16
> **H.E. Pennypacker said:**
> I used to be able to use CTRL-F all the time in web browsers and other applications, but not anymore.Works fine here. Did you press it after focussing browser?

---

### Post by H.E. Pennypacker on 2006-10-17
I expect CTRL-F to work perfectly fine for you. The problem is not with Ubuntu (or Linux).  The problem, I realize, lies with me.  I believe it has something to do with something I did.  I am not sure, but it may have something to do with Compiz or Beryl, and more likely, Xterm.  

Regardless of a window state (whether it is focused or not), CTRL-F won't work.

---

### Post by seijuro on 2006-10-17
technically ctrl+f should be controlled by each program on it's own the only thing I can think of off hand is perhaps you may have added something to your keyboard short cuts that is overriding it. Check your kb shortcuts in the preferences menu. If anything is using crtl+f remove it.

---

### Post by hoozey on 2008-07-16
I believe this is sometimes caused by xbindkeys. Check your bindings in ~/.xbindkeysrc or use xbindkeys-config if you have it.

---

### Post by okey666 on 2008-07-16
Check compiz/beryl setting. I could not use F-11 for a bit and that was because compiz was using it. See if you have set ctrl f as a key-binding.

---

