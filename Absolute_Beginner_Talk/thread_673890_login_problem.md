---
title: "login problem?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by bobbilda on 2008-01-21
Hi,

installed server edition 7.1 all seems ok.

on bootup it eventually asks for user/password (which it accepts)

then it goes on to ask...

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ _

has anone any idea what to enter there?

many thanks

---

### Post by banewman on 2008-01-21
That's what you get with the server edition - no gui.
If you want a desktop type - 
sudo apt-get install ubuntu-desktop
for a gnome desktop or choose your own flavour
e.g. fluxbox, xfce etc
:)

---

### Post by zidane2 on 2008-01-21
This is normal you are loged in as the user ubuntu, the sudo thing needs to be used when you want to run a command as the root user.
If you want a gui (windows, mouse, pointer, etc) then run:
sudo apt-get update
Then run either:
sudo apt-get install gnome (to install ubuntus desktop environment)
or:
sudo apt-get install kde (to install kubuntus desktop environment)
or if you are usaing a slightly older machine you might want to use:
sudo apt-get install xfce 
or even less demanding:
sudo apt-get install fluxbox

Hope this helps :)

---

