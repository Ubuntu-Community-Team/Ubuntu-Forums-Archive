---
title: "&quot;Make Link&quot; Nulled out"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by alecwh on 2007-06-16
Hey!

I've got a LAMP server setup, and I want to make a shortcut to the www directory on my desktop.

I usually go to "Make Link" after right clicking on the folder, but the option is nulled out for some reason. Can someone explain? And a fix?

---

### Post by gilgongo on 2007-06-16
Sounds like you don't have permissions to do it? I'd drop to a command line and type:

cd ~/Desktop

sudo ln -s /path/to/www

and see what happens. You may also need to make www writable by you with sudo chmod +w

---

