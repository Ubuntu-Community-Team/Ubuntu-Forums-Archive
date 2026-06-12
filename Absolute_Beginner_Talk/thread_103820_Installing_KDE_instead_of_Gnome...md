---
title: "Installing KDE instead of Gnome.."
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by ubunick on 2005-12-14
If you have/had problems with Ubuntu graphically, would installing kde help any? I don't really have any specs to show you, but if you had any different experiences with it post your opinions.

---

### Post by 23meg on 2005-12-14
It can depend. What problems are you having?

---

### Post by aysiu on 2005-12-14
Go ahead and install it and try it out.

If you want to make sure you can *uninstall it* (say, if you later find out you hate KDE, are having the same problems, and are low on disk space), install it this way:

Open a terminal (Applications > Accessories > Terminal). Type: ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
``` Do **not** answer "yes" yet.

Apt-get is going to list a bunch of packages that will be installed. 
Use your mouse to highlight all of those packages and copy and paste them into a text file. 
Save the text file to your desktop.

Then, answer "yes" to installing the packages.
Wait until they install.
Log out.
Click on "Session" and select KDE.
Log in.

P.S. The reason I'm suggesting you highlight the packages to be installed and make a copy of them is that typing ```
sudo apt-get remove kubuntu-desktop
``` does **nothing**. KDE will still be there.

---

### Post by ubunick on 2005-12-14
[QUOTE=23meg]It can depend. What problems are you having?[/QUOTE]

I don't have the links to my other threads, but its just been major GUI issues.. lines across the screen, blotches, etc.  which is probably video card, but there isn't much I can do about it I don't think.  I just reinstalled windows xp and updated a bunch of drivers so hopefully that fixed it something.  I was going to try KDE to see if it has GUI issues or not.

PS -- I'm not in ubuntu at the moment.

---

### Post by aysiu on 2005-12-14
[QUOTE=ubunick]I don't have the links to my other threads, but its just been major GUI issues.. lines across the screen, blotches, etc.  which is probably video card, but there isn't much I can do about it I don't think.  I just reinstalled windows xp and updated a bunch of drivers so hopefully that fixed it something.  I was going to try KDE to see if it has GUI issues or not.[/QUOTE] Well using KDE might be a good test of that theory. Actually, using XFCE would probably be a better test, as it tends to have better stability and fewer crashes/bugs/freeze-ups than KDE or Gnome.

---

