---
title: "Making a live dvd."
date: 2008-04-30
forum: Arch and derivatives
---

### Post by Barrucadu on 2008-04-30
I've decided, as a learning experience, to make a live dvd for myself. I'll be putting lots of partitioning, recovery, networking, et cetera utilities. Basically, I'll want to end up with a live dvd which gives me the ability to fiddle around with the host computer (and its network) happily.
I'll be using [this guide](http://wiki.archlinux.org/index.php/Building_a_Live_CD), I assume it will work for a dvd as well as a cd? I don't see why not, but thought I would check first.

Can anyone recomend any programs for me to include? I am trying to remain as lightweight as possible:
[list]
[*]Xorg
[*]Fluxbox
[*]NetworkManager
[*]cfdisk (possibly even Gparted?)
[*]nmap
[*]What else? I haven't really made a system like this before.
[/list]

**Edit:** The reason I say live dvd rather than live cd is because I generally end up using several gigabytes for / in a fully configured system. However, that is for a generic system with xfce and other big things installed. I decided to give myself the extra space, though, just in case a cd isn't quite enough.

---

### Post by shearn89 on 2008-04-30
I'd suggest ditching NetworkManager and going with something like wicd, or just scripts (there was a guide in the Tutorial of the Week thread that covered all the manual set up stuff).
I'd also go for gnumeric and abiword instead of OpenOffice, and Thunar instead of Nautilus (or PCManFm). 
Music you might want mpd+ncmpc. 
Browser maybe Opera or something uber-light like Kazehakase?
Maybe try a different WM before you start on the live disc - something like PekWM?

---

### Post by Barrucadu on 2008-04-30
I wasn't planning on having any office programs however Abiword sounds like a good idea, and I would have used Thunar, PCManFM, or XFE as the file manager anyway.
I'll be spending a few days yaourt -Ss'ing to find things I might like and find useful. :)

---

### Post by shearn89 on 2008-04-30
good plan... See how light you can get your install before you try making a disc of it. I also found that trying to make the disc was quite tricky - doesn't seem to be any current support.

---

### Post by finferflu on 2008-04-30
What? Openoffice? Abiword??? Nahhh! Put TeXLive! :D

---

### Post by Barrucadu on 2008-04-30
:lol:
Quite possibly. Not only am I going to make this useful, I'm also going to make it look as difficult and technical as possible - I seem to live for impressing people :P

---

### Post by scragar on 2008-04-30
huh? why specify a seperate browser and file manager, when konqueror is both? and because it's a KDE app it shares resources really well, provided your installing more than it(otherwise the nature of the KDE libs acts against it) from the KDE range.

---

### Post by Barrucadu on 2008-04-30
Because I don't like it, and I won't be installing many (if any) KDE things.

---

### Post by shearn89 on 2008-05-01
Konqueror uses a lot of KDE deps, in the same way that nautilus uses a lot of gnome ones... Thunar uses v. few.

---

