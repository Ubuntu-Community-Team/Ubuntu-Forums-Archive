---
title: "Drop and drag or copy and paste"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by tomansbro on 2008-03-10
Hi,
 I am on my second atempt to install mythbuntu and cant seem to move a file.
I downloaded a bin file for my tv card an now ned to put it in the Firmware folder.
 If I copy it off the desktop and try to paste it into /lib/firmware the option to paste is grayed out. if I open 2 file manager windows and try to drag and drop it into the Firmware folder the file floats back to the desktop ( file manager window)
  Thanks for your help from a real newbie
Tom

---

### Post by NT4usB on 2008-03-10
I'm guessing root owns and has exclusive permissions to .../firmware so your user can't write to it.
Not sure how to get around that with the GUI but from a terminal you can:
```
 sudo cp ~/Desktop/somefilename /lib/firmware/
``` and enter your password when prompted.
(~/ is a shortcut to your home directory... same as typing /home/yourusername/...)
[Tip for using the terminal] when typing paths, filenames, etc., type the first couple letters then hit the Tab key. If you have the first letters correct, the word or path will autocomplete. If not, or you don't remember the word or path, Tab twice (Tab Tab) will list all the words or paths available from the directory you're in.

---

