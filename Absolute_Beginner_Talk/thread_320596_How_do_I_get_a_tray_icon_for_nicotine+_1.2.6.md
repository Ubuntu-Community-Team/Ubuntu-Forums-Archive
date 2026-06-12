---
title: "How do I get a tray icon for nicotine+ 1.2.6?"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by suki on 2006-12-17
I've managed to install nicotine+ 1.2.6, is there any way to make a tray icon for this application? I'd rather not have to run to the terminal each time to run this program.

This did not work when I went to the terminal and typed the following:
sudo apt-get install build-essential python-dev python-gtk2-dev libgtk2.0-dev
cd .nicotine+-1.2.6/trayicon
 ./autogen.py
sudo make install
cd ..
cp trayicon/trayicon.so pynicotine/

I followed this to install Nicotine+ 1.2.6, by replacing 1.2.4.1 with 1.2.6 where needed:
[http://ubuntuforums.org/showthread.php?t=196835&highlight=nicotine]("http://ubuntuforums.org/showthread.php?t=196835&highlight=nicotine")

It's been solved, thank you.

Another way to make an icon on the tray is to
 right click on the top panel click "edit menus"
click which sub menu to add the new icon,
click "new item"
put whatever icon you want, nicotine+ comes with one under the img folder
name "Nicotine"
hit "browse" and click on nicotine

---

### Post by s6dalane on 2006-12-17
Try adding this repository to your sources.list file:

> deb [http://www.nicotine-plus.org/ubuntu](http://www.nicotine-plus.org/ubuntu) edgy main

And then install Nicotine via Terminal or Synaptic. It worked for me.

---

### Post by suki on 2006-12-17
> **s6dalane said:**
> Try adding this repository to your sources.list file:



And then install Nicotine via Terminal or Synaptic. It worked for me.

When it do that, all it finds is the old Nicotine+ 1.2.4.

---

### Post by s6dalane on 2006-12-21
Weird.. I installed version 1.2.6 by using that repository.

---

