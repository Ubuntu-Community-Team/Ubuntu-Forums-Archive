---
title: "ongoing problems with error messages"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by celticparadox on 2006-09-02
OK, I had to interrupt an install/update and now im getting the error message 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem

so i run the dpkg --configure -a with the sudo prefix and nothing happens...the terminal just shows the message  

Setting up flashplugin-nonfree (7.0.63.3ubuntu3) 

it's been sitting there for about an hour or so now.....not really sure where to go from here

---

### Post by thephantomlinguist on 2006-09-28
You've probably already fixed the problem, but in case someone else finds this and has run into the same problem...

sudo apt-get remove flashplugin-nonfree

sudo apt-get -f install

sudo apt-get install flashplugin-nonfree

This is, of course, assuming that you have the right repository in your list. At any rate, the first command is probably the most important.

Hope this helps!

---

