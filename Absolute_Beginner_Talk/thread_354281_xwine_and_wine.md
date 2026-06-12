---
title: "xwine and wine"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by HybridTheory on 2007-02-05
Ok this may seem major n00b or w/e but....how do I go about getting into the C: folder and program files? I know you can open terminal and type "winefile" but you can't add files to any thing in C: I also use xwine is there any way I can open C: and drag stuff into it? why you may ask? I have mods for games and I have to get into the game folders lol.

thx :)

---

### Post by machoo02 on 2007-02-05
can't you just use your native file manager to drag and drop your game mods into their respective folders?  Use Ctrl-H to view the hidden files/folders in your home folder, then drag and drop away!

---

### Post by yabbadabbadont on 2007-02-05
C: is just a symbolic link to a directory tree inside of the (hidden) .wine directory in your home directory.  If you change the settings in Nautilus (or whatever filemanager you use) to show hidden files and directories, then you should be able to just navigate down that tree to the correct location.  (~/.wine/drive_c/....)

Edit: too slow!

---

### Post by HybridTheory on 2007-02-05
I should have known that...lol..ANY WAYS thank you both very much!

---

