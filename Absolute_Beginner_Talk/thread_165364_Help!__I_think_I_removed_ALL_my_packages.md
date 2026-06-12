---
title: "Help!  I think I removed ALL my packages"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by Boatswain on 2006-04-24
First off, I'd like to say thanks to everyone out here for all the great responses.  I installed Ubuntu a couple of months ago and haven't had a problem that I couldn't figure out the answer to by delving through all the helpful answers on the forums until now.  So thanks for all the past help.

Now, the business at hand:  So I was tinkering about with the true transparent terminal howto, thinking it might be fun, but I found it was really slowing my system down a lot, so I decided to get rid of it.  In doing so, I decided I would just apt-get remove everything I'd installed.  When I typed in:

sudo apt-get remove xcompmgr libxcomposite1 libxcomposite-dev libxfixes3 libxfixes-dev libxdamage1 libxdamage-dev libxrender1 libxrender-dev

I apparently removed all my packages, even the GUI.  So, the question is what can I do about this?  Is there any kind of restore that I can do to get all my stuff back, or will I have to do it all over again the hard way.  And speaking of, how exactly do I do it the hard way?

Many, many, many thanks indeed.

---

### Post by Ensnared on 2006-04-24
If you're using Gnome, a simple```
sudo apt-get install ubuntu-desktop
```...should do the trick. If you're using KDE (Kubuntu), do```
sudo apt-get install kubuntu-desktop
```...instead, or```
sudo apt-get install xubuntu-desktop
```...if you're using Xfce (Xubuntu).

With all the dependencies and whatnot I'm _fairly_ certain that this will install all the necessary packages to get your GUI back up and running :)

---

### Post by Boatswain on 2006-04-24
Hey thanks, that's got me up and running, with most of the packages back, even with all my preferences and all that retained.  Now I just need to go pick up everything that didn't show up on its own.  What a way to spend a day off.

I guess this shows why there's a  --dry-run tag for apt-get remove, huh?

---

### Post by Rinzwind on 2006-04-24
Never delete the libs* unless you are sure you don't need them anymore.

Instead install **orphan**
It's a command line tool that tells you what libs are no longer used and can delete them for you.

---

### Post by Ensnared on 2006-04-24
Good to hear you got it working again :)

[QUOTE=Rinzwind]Instead install **orphan**
It's a command line tool that tells you what libs are no longer used and can delete them for you.[/QUOTE]Just to avoid any confusion, it's called **deborphan** - and yes, it's an invaluable tool for keeping the system clean :) Just be aware that it will tell you it's ok to remove things like non-free plugins for your mediaplayers and the like, since nothing actually depends on those except for your own media-format needs ;)

---

### Post by Melhisedek on 2006-04-24
If I install kubunu ontop of my Dapper, will I get access to all KDE programs but still have my Gnome desktop? Can I change at will between managers (Gnome/KDE) ?

---

### Post by Ensnared on 2006-04-24
[QUOTE=Melhisedek]If I install kubunu ontop of my Dapper, will I get access to all KDE programs but still have my Gnome desktop? Can I change at will between managers (Gnome/KDE) ?[/QUOTE]
In a word, yes.

Your applications-menu might become a bit messy since you'll have lots and lots of applicatons, but there are ways of moving the KDE-apps into their own menu - do a forum search if you want to know how, I don't remember but I know I've seen threads about it.

If you have KDE and Gnome (and Xfce and Window Maker and just about any window-manager/desktop environment out there) installed you can choose which one you want to use from the Session-menu when you log in.

---

