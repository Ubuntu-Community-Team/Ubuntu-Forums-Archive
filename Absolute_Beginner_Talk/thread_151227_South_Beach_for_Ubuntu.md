---
title: "South Beach for Ubuntu?"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by therunnyman on 2006-03-27
Hi All,

Ubuntu's a little fat, by necessity, of course.  What I'd like to do is slim my particular Ubuntu down.  Certainly, there are a bunch of drivers I don't need, and other things in other places that can go, but I'd rather start top-side, if that's possible.  

For example, I know I don't need the games.  Can I chuck those with impunity (i.e., does that "desktop" item that gets removed along with the games hurt Gnome)?  And is there anything else I can easily be rid of?

Thanks!

therunnyman

---

### Post by PsychoTrauma on 2006-03-27
The package ubuntu-desktop is only useful for upgrading your system to a newer version so you can remove it with no problems.

You can remove a lot of stuff but i'm not sure what you use and dont use so it's a bit hard for me to suggest some packages. I remove openoffice and install abiword. I remove gnome-media since I use a newer version of rhythmbox that can play cds. I remove things like gnomemeeting since I dont use them.

---

### Post by lordofkhemenu on 2006-03-27
You could do a server install (typing 'server' at the cd boot prompt)..no x, only essentials loaded.
Then you could choose a lightweight window manager (fluxbox, et al) and it will install the needed programs and/or libraries.

"ubuntu-desktop" (and kubuntu-desktop, xubuntu-desktop) is just a metapackage, it won't/shouldnt uninstall things necessary to use gnome (never has in my experience).

---

### Post by Kapre on 2006-03-27
[QUOTE=therunnyman]Hi All,

Ubuntu's a little fat, by necessity, of course.  What I'd like to do is slim my particular Ubuntu down.  Certainly, there are a bunch of drivers I don't need, and other things in other places that can go, but I'd rather start top-side, if that's possible.  

For example, I know I don't need the games.  Can I chuck those with impunity (i.e., does that "desktop" item that gets removed along with the games hurt Gnome)?  And is there anything else I can easily be rid of?

Thanks!

therunnyman[/QUOTE]

runnyman - If you really want a "slim" version of ubuntu, you can try Xubuntu (Ubuntu with XFCE). But if you just want to tone down the default, yes you can remove some of the games (and also the apps) which you think wouldn't apply to you. 

Have fun!

K

---

### Post by tadashi on 2006-03-27
Open up the package manager and just unclick what you do not need.  It should give you a description.  Should something not work you can just recheck it to install it.  Just have anything important backed up.  Worse case if you break it you can just reinstall.  If you really wanted to be in control of everything then maybe you want to play thwith Gentoo or if you wanted it small then try DSL (Damn Small Linux).

---

### Post by therunnyman on 2006-03-27
Thanks guys!

therunnyman

---

### Post by bionnaki on 2006-03-27
ext3 filesystem takes up alot of room. you'll save a few gigs by reformatting to reiserfs.

---

