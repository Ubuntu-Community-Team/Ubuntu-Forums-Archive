---
title: "Unable To Install On G5"
date: 2006-09-08
forum: Apple PPC Users
---

### Post by JustinEvil on 2006-09-08
Hello, I am installing the latest version of Ubuntu on an alternate hardrive on my first generation G5 Powermac.  It goes through the long list of checks in orange text, but on the final item on the list, instead ok ok, it says "failed."  Before I can read what it says, it switches to a black screen and stays there.  

Can anyone help me with this?

---

### Post by 3rdalbum on 2006-09-10
When the Ubuntu splash screen appears, try pressing Control-Option-F6. This should bring up a plain text version of the loading sequence, where it might be easier to see what bit has failed.

If it switches to the X server too quickly still, try pressing Control-Option-F6 again; you might be able to see what has failed AFTER it fails.

It might be one of the other F-keys, but I think it's F6.

---

### Post by stmiller on 2006-09-10
Try the alternative CD. That will let you choose a text based installer from the start. Press tab at the boot screen for options on the disc. You want power64.

And for G5 support you must compile your own kernel from kernel.org after installing ubuntu. The current kernel on the ubuntu disc does not support thermal, sound, wireless, etc. on the G5s.

---

