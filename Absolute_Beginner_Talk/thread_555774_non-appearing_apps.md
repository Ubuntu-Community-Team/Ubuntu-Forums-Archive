---
title: "non-appearing apps"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by miapapia on 2007-09-20
hello! this is my first time posting here and I like the "similar threads" feature. I did look into one of the suggestions, but when I tried to back into the original list, I ended up back to my message, unable to check out the rest of them. So, I apologize in advance if this is a duplicate.

In any case, I just started playing with Ubuntu a few days ago (after I got a working video card for it) , and noticed that certain applications that I installed don't appear anywhere. For example, I installed Kalarm, and it was not in "accessories". A search found the program (I forget where now), I traced it and moved what I perceive to be the equivalent of a Windows shortcut to the desktop so I can use it. 

Next, I installed gparted do I can try to format my slave drive, but it also does not appear anywhere.  a search revealed some components, but I can't get it started.  The closest I got was clicking on an icon similar to what got kalarm started, but it says that only root can run it. ???

Why does this happen? (installing apps that don't appear in the drop down menu?)

How do I access gparted now?

Also, how do you create shortcuts (a la Windows "send to desktop)?


Thank you for dealing with such basic questions

---

### Post by notwen on 2007-09-20
A lot fo your applications in Linux have to be manually run from terminal, hence typing in the application name in a terminal to run said app.  As far as GParted goes, you'll need to run this as root su try "gksudo GParted" and enter your pass.  =]

-PS-
Welcome to ubuntuforums.

---

### Post by miapapia on 2007-09-20
thank you. Now, is this the standard procedure for any app that is root access only?

(gksudo *name of app*)

---

### Post by Steveway on 2007-09-20
If the app has a gui then yes. (Though you can use only gksu to safe time because gksudo is just a symlink to gksu so they are the same commands.)
If it is a CLI app then you need to use sudo.
Like:
sudo apt-get install <programname>
gksu gedit
...

---

### Post by miapapia on 2007-09-20
still, I don't understand why kalarm never appeared in the accessories menu? Is this common?

How do I get it to be included there?

---

### Post by dcstar on 2007-09-20
> **miapapia said:**
> still, I don't understand why kalarm never appeared in the accessories menu? Is this common?

How do I get it to be included there?

Whoever packages the app has to put in the code to add menu entries, sometimes people don't do this.

Just edit the menu with System-Preferences-Main Menu and add in what you like where you like.

---

