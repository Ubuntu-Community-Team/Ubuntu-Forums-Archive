---
title: "Terminal Service Client"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by SonyJunkie on 2007-08-13
Hi All,

First post so please be gentle!!:)

I've just installed Ubuntu and it's the first time I've ever used Linux and I'm liking it.

However, I have managed to set up a TSC but when I "Save As" it seems to put a text file on the Desktop which when double-clicked just opens as a text document even though the extension is .RDP, my question is how do I save it so that when I double-click it launches the Remote Desktop?

The TSC screen looks almost identical to Windows so I'm confident the settings are correct, actually they are correct because it works, I just want an easy way to run it.

I hope I've explained that OK!

Thanks in advance.

---

### Post by Kobalt on 2007-08-13
Here is what you can do : 

* right click on your .rdp file and select Open With...
* select Custom command and enter *tsclient*
* right click again on your .rdp file and this time go Properties then Open with
* select tsclient as default (just tick it), and here you go.

Now when you double click your file it should open with the Terminal Server Client automatically.

---

### Post by SonyJunkie on 2007-08-13
Thank You.

---

