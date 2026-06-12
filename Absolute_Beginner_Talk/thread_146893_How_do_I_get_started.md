---
title: "How do I get started?"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Warren3949 on 2006-03-19
Hello, Warren here.
I have downloaded Ubuntu onto my FDD (80G) with auto partitioning 50% Windows XP and 50% Ubuntu - I think.
After auto loading of 'details' and adding my user name and password, Ubuntu is asking for more details - "warren@ubuntuwarren:'tilde'$".
Can someone advise me of what Ubuntu is looking for to start the program running?
Many thanks
Warren.

---

### Post by Ramses de Norre on 2006-03-19
You mean you just get a command prompt after you boot?
Did you do a server install?
Try typing startx and press enter.

---

### Post by az on 2006-03-19
What heppens if you type this:

sudo apt-get -f install

sudo apt-get install ubuntu-desktop

(that will fix a half-installed system)
sudo /etc/init.d/gdm restart (to restart the desktop)


if that works out fine, but does not solve your problem, try:
sudo dpkg-reconfigure xserver-xorg
and reconfigure your graphics system.  Pick the vesa driver, if it is not already picked to see what happens.  If this is still a problem, what kind of video card do you have?

---

