---
title: "Screwed Gnome pannels up"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by sebz2005 on 2006-07-26
Hey, I've screwed my Gnome pannels up.
How do I restore them?
Thanks

---

### Post by DiscoKiller on 2006-07-26
how do you mean 'screwed them up?'

can u give details?

DK

---

### Post by sebz2005 on 2006-07-26
Each time I open a new program, I cant bring it forward. Also I moved some of the things around and I cant get them back into their propper positions.

---

### Post by richardward101 on 2006-07-26
However you've screwed them up, this'll get your defaults back:
Open a terminal and enter the following commands:

cd ~
cd .gconf
cd apps
rm -rf panel

Now if you log out and log back in again straight away the panels will be restored. 

If you can't open a terminal then press Ctrl+Alt+F1 to get a terminal, when you've finished using the commands use Ctrl+Alt+F7 to get back to gnome.

bear in mind this will destroy you're current panel settings, the rm -rf command deletes the directory and all subdirectorys. make sure you don't make a mistake here.

Hope that works.

Edit:correct the mistake pointed out below.

---

### Post by DiscoKiller on 2006-07-26
and this is why i should just keep quiet ;)

---

### Post by sebz2005 on 2006-07-26
Works perfictly, except it's not .apps, just apps. ;)
Thanks!

---

### Post by richardward101 on 2006-07-26
> it's not .apps, just apps

ah silly me, so it is.

Its a good general tip for if you screw anything up (unless you were messing around with it with sudo), just delete/rename its settings folder, most apps create one if they can't find it and revert to default settings.

---

