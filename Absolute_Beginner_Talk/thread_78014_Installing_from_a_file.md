---
title: "Installing from a file"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by Arathorn on 2005-10-17
I have a rather stupid question but I really can't figure it out, so I wonder if anyone can help me?
How do I install a program I've downloaded myself? I know how to install things from the Ubuntu server with Synaptic or Install Applications (is that the correct name, it's called *Installeer toepassingen* in Dutch), but not files I have downloaded myself. For example I have Nero Linux (in a .deb file). I right click on it, and select "open with Install applications". The Install applications program loads, but doesn''t seem to do anything with the .deb file.
Any ideas?

---

### Post by ecobuntu on 2005-10-17
sudo dpkg -i foobar.deb (to install foobar.deb) or
sudo dpkg -i *.deb (to install all .deb files)

To remove:
sudo dpkg -r foobar.deb

Replace "foobar" with the name of your package!

---

