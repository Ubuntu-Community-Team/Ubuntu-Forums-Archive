---
title: "update notifier trying to get old stuf"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by x5452 on 2006-04-19
I have firefox 1.5.0.1 installed, but today wehn my update notification popped up it said  a bunch of kernel stuff, abd also fiefox, new version 1.0.8-0ubuntu5.10 and firefox-gnome-support new version 1.0.8-0ubuntu5.10   
what is that stuff, it does not look newer, the numbers look older...do i need to install it?  or how do i make it leave me alone about the stuff i have better of already?

---

### Post by krusbjorn on 2006-04-19
You can select the installed Firefox package in Synaptic, and then do Lock Version from the Package menu.

---

### Post by nalmeth on 2006-04-19
Can't you just deselect the packages you don't want to upgrade?
Or you can go in the terminal, and sudo apt-get install all the packages you want, leave out the ones you don't.
I don't think firefox will be downgraded, but I would guess it is possible that they pulled newer versions of packages for older ones because of bugs or stability probs.
EDIT: krusbjorn's way is even better

---

### Post by x5452 on 2006-04-19
ok heres a weird thing, I went to synatpic and search for firefox. it shows my installed version as 1.0.7 ubuntu2, however if i go to about in my browser its the 1.5 one.  I got the new version of firefox through automatix, so does that change things?

---

### Post by mostwanted on 2006-04-19
[QUOTE=x5452]ok heres a weird thing, I went to synatpic and search for firefox. it shows my installed version as 1.0.7 ubuntu2, however if i go to about in my browser its the 1.5 one.  I got the new version of firefox through automatix, so does that change things?[/QUOTE]

Yes. Automatix fetches Firefox from the Mozilla servers as a binary installer (like an .exe in Windows) and circumvents your existing Firefox installation.

Dpkg and apt-get only keeps track of packages installed through their services (deb packages have versions associated with them, that's part of how dependencies are worked out), there's no way they can read what version of a program is installed otherwise; if they could, it would be pure magic. When you think about that, it makes sense :)

---

### Post by x5452 on 2006-04-19
ok, so my update notifier is sitting in the corner and wont go away, telling me to upgrade to a (lower) version of firefox. if i uncheck them and click close, it comes back when i reboot. is there a way to tell it NOT to try and upgrade firefox?

---

### Post by mostwanted on 2006-04-19
[QUOTE=x5452]ok, so my update notifier is sitting in the corner and wont go away, telling me to upgrade to a (lower) version of firefox. if i uncheck them and click close, it comes back when i reboot. is there a way to tell it NOT to try and upgrade firefox?[/QUOTE]

Did you try doing as was suggested: right-clicking Firefox in Synaptic and selecting "Lock version" (or something like that, I'm on a Danish system).

---

### Post by krusbjorn on 2006-04-19
[QUOTE=mostwanted]Did you try doing as was suggested: right-clicking Firefox in Synaptic and selecting "Lock version" (or something like that, I'm on a Danish system).[/QUOTE]

Lock Version is in the "Package" menu ;)

---

### Post by x5452 on 2006-04-19
i cant, in synaptic the package listed is real old, i installed the new firefox with automatix....

---

### Post by Jagot on 2006-04-19
I just downloaded the update for the sake of it (have 1.5.0.2 installed anyway).  Providing you have set up 1.5 correctly it will have no effect on your current set up - 1.0.8 won't take over or anything.  The only thing that did happen is my Firefox icon got replaced by Ubuntu's default icon for it.  There's no harm in allowing Ubuntu to install this updated version.

---

### Post by 5-HT on 2006-04-19
[quote=x5452]i cant, in synaptic the package listed is real old, i installed the new firefox with automatix....[/quote] 
As was previously mentioned, Firefox 1.5 is not handled through the package manager. 

Your 1.5 installation did not replace 1.0.7, they coexist.

If you really want to prevent the update from 1.0.7 to 1.0.8, you can hold 1.0.7 in synaptic as has been mentioned in this thread.

However, there are some security fixes in 1.0.8 and some programs will still depend on and use some components of the 1.0.x line.

I did not install 1.5 via Automatix, so I am not sure how Automatix performs the installation and could not let you know how to avoid possible problems in the update (if there indeed are any). 

If you want to update 1.0.7 to 1.0.8, I would, at the least, move your profile temporarily during the update (to something like ~/.mozilla_backup).

Hope that helps.

---

### Post by Obor on 2006-04-19
I got FF 1.5.2 (1.5.1 installed with Automatix) and I run the update (to 1.0.8 ) today  - it didn't change anything, even my new icon stayed the same. It seems bit of a waste to download 8MB for no reason but it looks harmless and gets rid of the update notifier

---

### Post by Jagot on 2006-04-19
[QUOTE=Obor]It seems bit of a waste to download 8MB for no reason but it looks harmless and gets rid of the update notifier[/QUOTE]

Remember it's replacing FF 1.0.7 which is already installed on the system, so although it's downloading 8mb it's not actually taking up 8mb more space.

---

