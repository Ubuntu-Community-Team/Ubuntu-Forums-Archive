---
title: "How to show hidden files on Desktop?"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by velvetGreen on 2007-02-02
Hello all,

I needed to copy one hidden config file onto my Desktop, but noticed it was hidden there. Pressing ctrl-H didn't help. I can see the file in my nautilus' ~/Desktop folder fine but would like to set up my Desktop to show those hidden files as well. How do I do this?

---

### Post by HereInOz on 2007-02-02
I guess that you don't want to rename the file to remove the dot at the front of the file name?  That is obviously one way to do it but then the file is not hidden any more.

Other than that, I hope someone else has an answer for you.

I guess by definition showing a hidden file means that it is no longer hidden :-) so perhaps the renaming will be good enough.

---

### Post by kerry_s on 2007-02-02
Maybe, create a launcher that opens the hidden file in a editor.

the command> gedit (path to hidden file)

Example:
name> .conkyrc
command> gedit ~/.conkyrc

---

### Post by velvetGreen on 2007-02-02
Thanks for the replies. And you know what, the hidden config file (.conkyrc) I copied onto desktop wasn't hidden after all, it  had gone under the conky window. I noticed this after I terminated conky process, revealing the file. And then noticed that the ctrl-h also works... :rolleyes: 

I'll have to find out some way to prevent conky overlapping files on desktop... Thanks again :)

---

### Post by kerry_s on 2007-02-02
Yeah, that's why i keep conky on the right, all icons are made on the left. That happened to me with my usb drive, i kept wondering why it wasn't showing up on the desktop. :)

---

### Post by drs305 on 2007-02-19
> **kerry_s said:**
> Maybe, create a launcher that opens the hidden file in a editor.

the command> gedit (path to hidden file)

Example:
name> .conkyrc
command> gedit ~/.conkyrc

If I'm using gedit in graphical mode and already have it open, is there a way to display the hidden files when I select "File, open"?  I can't seem to find a way to do it, other than to type in the location or to open nautilus and right click to send to the text editor.

---

### Post by v8YKxgHe on 2007-02-19
> **drs305 said:**
> If I'm using gedit in graphical mode and already have it open, is there a way to display the hidden files when I select "File, open"?  I can't seem to find a way to do it, other than to type in the location or to open nautilus and right click to send to the text editor.

Right Click -> Shown hidden files :)

---

