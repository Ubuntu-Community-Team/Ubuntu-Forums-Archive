---
title: "adding multiple wallpapers, and share them"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by justleen on 2007-04-02
Guys, please help, this is driving me nuts!

I downloaded a few wallpapers and  placed them in /usr/share/backgrounds. I want to add them to the avaible backgrounds, and them "copy" my settings, so the other users have the same wallpapers availble

ive changed ownership and rights so all users can access them.
so far, so good.

But, when i go to the prefs >background, i still have to manually add every wallpaper..

im assuming gnome has a xml config file somewhere which has a list of which wallpaper have been added/are avail...

Q1: is there a way to add a bunch off wallpapers at the same time? (so without adding them one by one in the prefs > backgrounds)

Q2: where are the settings stored, and can i simply copy them to a different users home dir?

Thank in advance, Ubuntus!

---

### Post by laidback on 2007-04-02
Have a look in:-
**/home/your_name/.gnome2**
Note the dot in front of gnome2, it's a hidden file. In your file browser ** View>Show Hidden **files will display them all. (default is to hide them). In there there's a file called** backgrounds.xml**, have a look at it in your browser. Now I'm not saying that this is what you want, I've never looked at it before, but it appears to be hopeful.

---

### Post by justleen on 2007-04-02
I've already looked at that.. didnt think it would be the correct file..

But cheers, ill look at that again, copy it to a user, and see wheter it breaks my X again :0

---

### Post by laidback on 2007-04-02
It would only apply for your use; copy file to same location in anothers /home/my_home/.gnome2 directory as see if they then pick up the offer. But don't forget you may get access/read issues unless you've allowed same on the background files specified, group read etc.
Just by looking at it it seems to me that the backgrounds.xml file controls what's on offer within a user area. As I say I've never done this.

Good luck

---

