---
title: "apt-get install gnome?"
date: 2005-01-07
forum: Apple PPC Users
---

### Post by j0nheck on 2005-01-07
I am trying to install gnome on a fresh install of ubuntu(warty) i have done on my powerbook. When i sudo apt-get install gnome i recieve a message that says that package is reffered to by another name (or something similiar, i don't have a spair box to mark it down exactly) how can i get gnome install? From what i have been reading, it seems like it was supposed to be installed by default?

---

### Post by tiiim on 2005-01-07
[QUOTE=j0nheck]I am trying to install gnome on a fresh install of ubuntu(warty) i have done on my powerbook. When i sudo apt-get install gnome i recieve a message that says that package is reffered to by another name (or something similiar, i don't have a spair box to mark it down exactly) how can i get gnome install? From what i have been reading, it seems like it was supposed to be installed by default?[/QUOTE]
 then what are you running if your not in gnome...?

---

### Post by tiiim on 2005-01-07
[QUOTE=tiiim]then what are you running if your not in gnome...?[/QUOTE]
 try apt-get install gnome-bin
or maybe

gnome-desktop-date

There many gome packages im assuming if you download one apt will then automatically download others.

also if your not in gnome do you have x running? if not you'll need the x files... your right gnome is meant to be there by default unless its just ur x that not running...?

---

### Post by j0nheck on 2005-01-07
X is installed, i'll gnome-bin. The release i installed was downloaded about 3 weeks ago, so maybe it didn't come with gnome.

oh yeah, and startx doesn't work, shouldn't that work if x is installed?

---

### Post by diabolo on 2005-01-07
[QUOTE=j0nheck]X is installed, i'll gnome-bin. The release i installed was downloaded about 3 weeks ago, so maybe it didn't come with gnome.[/QUOTE]

There should be a dependency package that installs all the Gnome stuff. I'm not sure which one it is but...
gnome
gnome-core
gnome-desktop-environment

But actually it should already be there.

[QUOTE=j0nheck]oh yeah, and startx doesn't work, shouldn't that work if x is installed?[/QUOTE]

Yes but your .xinitrc file might be need to have "exec gnome-session" in it, as the last line.

---

### Post by Ptero-4 on 2005-01-07
[QUOTE=diabolo]There should be a dependency package that installs all the Gnome stuff. I'm not sure which one it is but...
gnome
gnome-core
gnome-desktop-environment

But actually it should already be there.



Yes but your .xinitrc file might be need to have "exec gnome-session" in it, as the last line.[/QUOTE]
 Hi, are you sure that you don't have gnome, 'cause warty comes with gnome 2.8.1 by default.
And about X, ubuntu doesn't use the startx script. They have a custom script called gdm which runs X11, start GDM and then shows your WM / DE.

---

### Post by j0nheck on 2005-01-08
I searched around and found out i needed gdm, so i got that, then i was able to get gnome started, i had a bunch of error messeges so i said "what the hell, i'll just reinstall it" and bang, thangs worked fine. not sure why things didn't work the first time.

---

