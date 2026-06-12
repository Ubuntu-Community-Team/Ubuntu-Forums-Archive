---
title: "Help ~ Black Screen"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by dijar on 2007-09-10
Hi I am absolute beginner & installed Ubuntu 5.10 on my Dell Inspiron 8000 laptop but now when I am prompted to enter username & pass I enter but nothing happens it just appears on black screen 
Ubuntu 5.10 "Breezy Badger" user tty1. What should I do know pleaseeeee help me!!!!!!!

---

### Post by diatribe on 2007-09-10
breezy is no longer supported, perhaps you should consider upgrading?

---

### Post by dijar on 2007-09-11
Ok but how to upgrade once I installed ubuntu 6.04 on a PC the same thing appeared whats that black screen I really don't understand should Ubuntu when startup take you to the logon screen whith a GUI like Windows. I know, that this is really easy for you so help me. And don't give me short answers because I am a newbie in this thing I really want to start using Ubuntu.

---

### Post by jvc26 on 2007-09-11
Are you installing the desktop version or the server version? If the server version then its not that surprising you don't have a GUI.
Il

---

### Post by BrendanM on 2007-09-11
Dijar, welcome aboard. We'll help you get this sorted out. It sounds like (for whatever reason) you might not have the GUI installed.

What you're going to want to do is login at the text prompt (don't worry that you don't see your password when you type, it's invisible instead of *****'d out)

Then, from the text prompt, type **sudo apt-get install ubuntu-desktop** you should see it download and install a ton of stuff. Once it's done installing, type **startx** (X server is the Linux GUI) to start the graphical stuff.

Good luck. If you need more help, post back.

---

