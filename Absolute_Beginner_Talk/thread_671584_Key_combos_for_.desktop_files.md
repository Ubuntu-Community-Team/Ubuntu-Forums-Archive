---
title: "Key combos for .desktop files?"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by yxrkt on 2008-01-18
in windows, i can open the shortcut and set the hotkey combo. is it possible to do something similar in ubuntu?

---

### Post by yxrkt on 2008-01-18
bump

---

### Post by yxrkt on 2008-01-18
bump

---

### Post by jordanmthomas on 2008-01-18
You can use key combos to run certain executables, but I'm not sure about .desktop files.  You just need to get the executable line out of the desktop file...it's easy.  :)

I use xbindkeys to do this.

However, most window managers have options to allow you to set certain programs for certain keys.  What window manager are you using?  (metacity, compiz, etc)

---

### Post by yxrkt on 2008-01-18
using compiz. i want to be able to set a shortcut for any executable (in this case, frozen throne)

---

### Post by jordanmthomas on 2008-01-18
Ok, compiz works.
First, you'll need to install compizconfig-settings-manager (it's in the universe repository, so make sure it's enabled)

After it's installed, run ccsm and go to the General Options at the top.  Then, put the path to your frozen throne executable in the 'Command line 0' field.

Then, go over to the Actions tab and set the key for 'Run command 0'

Easy enough, right?

Alternatively, you could install xbindkeys and use it.

---

### Post by yxrkt on 2008-01-18
thx very much, will try when i get the chance

---

