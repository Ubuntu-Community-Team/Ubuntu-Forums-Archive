---
title: "Two Quick Questions"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by Cheese Roller on 2007-09-11
I deleted a user account, and that person's folder is still there. Since I don't have privilages to just delete the folder, how would I do it?

Another thing, can somebody please link me that video that shows you how to do filesharing with Windows on a local network, how to get it set up?

And last, the monitor I have my Ubuntu hooked up to can only go up to 1024x768, but on other computers I've gotten it even higher than 1280x1024. How can I get back the higher resolution?

Edit: Sorry I should have titled this three quick questions.

---

### Post by SOULRiDER on 2007-09-11
1)```
sudo rm -R /home/username
``` That will delete that users home, just replace username with well... the username :P

2) Havnt seen it, sorry!

3) Try ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` in a console.

---

### Post by Cheese Roller on 2007-09-11
okay for #3 can you explain to me what it is that I am configuring so I can understand Linux better?

And #1 worked, thank you.  There's no other directories that user could  have had right?

---

### Post by Cheese Roller on 2007-09-12
bump

---

### Post by ravenwere on 2007-09-12
The file you were reconfiguring was /etc/X11/xorg.conf file (in ubuntu). It supplies configuration parameters to the xwindow server that supports your gnome or kde etc. graphical environment. When you reconfigure it will ask for the driver you wish to use for your graphics card and the resolutions you wish to use for your monitor.

---

### Post by hyper_ch on 2007-09-12
# 2 --> search the tutorial section... there are some howtos in there.

---

### Post by Cheese Roller on 2007-09-12
3rd one didn't work, it gave me some kind of error message, and said "a backup was created."

---

