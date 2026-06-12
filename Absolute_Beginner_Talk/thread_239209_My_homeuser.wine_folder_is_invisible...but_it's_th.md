---
title: "My /home/user/.wine/ folder is invisible...but it's there."
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by Frostshock on 2006-08-18
But running find / -type d -name wine\* 2> /dev/null in the terminal reports that it exists.

:-k

EDIT: I just found out it's a hidden folder. How do I unhide it?

---

### Post by scxtt on 2006-08-18
most (if not all) file browsers hide any folder prefaced by a . -- and you can generally (if not always) have them stop doing that ...

unless you're saying **$:> ls -al ~/** doesn't show it ...

---

### Post by foxjwill on 2006-08-18
Go to /home/user and press ctrl+H.

By the way, anything beginning with a '.' is a hidden folder.

---

### Post by goatmale on 2006-08-18
Show hidden files and folders in  Nautilus

   1.

      In Nautilus, use the Ctrl-H shortcut keys to toggle hidden files and folders on and off, or select View->Show Hidden Files.
   2.

      To permanently show all hidden files and folders, choose Edit->Preferences.
   3.

      Click on the Views tab.
   4.

      Select the Show hidden and backup files check box.



this is from the nifty ubuntu desktop tricks:
[https://help.ubuntu.com/ubuntu/desktopguide/C/desktop-tips.html](https://help.ubuntu.com/ubuntu/desktopguide/C/desktop-tips.html)

---

### Post by Frostshock on 2006-08-18
Ok, is there a way to just make *that* folder unhidden? I'd rather not be seeing .vlc and all these other ones, but it isn't a real bother if there isn't a way.

---

### Post by foxjwill on 2006-08-18
not that i know of.

---

### Post by Frostshock on 2006-08-18
Ok then, cheers :D. Thanks to everyone.

---

### Post by kzutter on 2006-08-19
You can make a symbolic link to the hidden folder. The link will be visisble,  giving you an easy way to 'see' the folder.

ln -s /home/user/.wine /home/user/wine

---

### Post by Indras on 2006-08-19
> **kzutter said:**
> You can make a symbolic link to the hidden folder. The link will be visisble,  giving you an easy way to 'see' the folder.

ln -s /home/user/.wine /home/user/wine

Yep, this is the default behavior of Cedega.  It creates a symbolic link to the cedega folder (~/.cedega) as "transgaming_drive".

---

