---
title: "Installing Logitech Cordless Desktop"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by luckyducky on 2007-06-13
I'm completely lost. I've never actualy installed anything on Ubuntu myself. I'm using Dapper and I need to be able to install my cordless desktop. My mouse is working fine, but my keyboard isn't. I need to be able to install the software. I have Wine. Is that what I should use, and if so, how to you run a program in the terminal using Wine?

---

### Post by jeeves on 2007-06-13
My experience with wireless keyboards is they usually work out of the box in Ubuntu, no driver install needed. I can't be sure if that is the case with your Logotech model, but did you try syncing it? Usually this consists of pressing the button on the external USB dongle then pressing the button on the bottom of the keyboard.  The button on the bottom of the  keyboard is tiny and easily missed. I usually use a pen tip to press it.

---

### Post by bbarcelo on 2007-06-13
> **luckyducky said:**
> I'm completely lost. I've never actualy installed anything on Ubuntu myself. I'm using Dapper and I need to be able to install my cordless desktop. My mouse is working fine, but my keyboard isn't. I need to be able to install the software. I have Wine. Is that what I should use, and if so, how to you run a program in the terminal using Wine?

If you install the drivers within Wine, I don't think they will solve them not working in Ubuntu. I would try installing ndisgtk first. It's a program that allows you to install Windows drivers given that you have the .inf files.
Here's how to install/get it..
From terminal:
```
apt-get install ndisgtk
```

Then find the Logitech drivers off the web, extract them, and run ndisgtk (from a Terminal) and point it to the inf file(s).

---

