---
title: "Choosing Programs to use for .torrent files"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Armaniboy on 2007-08-23
So when I go to download a .torrent file, a box shoots up and asks me to choose a program. The standard program on a gnome desktop is Bittorrent, but I want to use Ktorrent. I have NO IDEA how to scroll through the menus and find it. I know it's on the applications->internet-> Ktorrent, but I don't know how to go through the file folders to find that program like I do on Windows :(. Can anyone help?

-Armaniboy-:popcorn:

---

### Post by chrome307 on 2007-08-23
Are you looking for where your files will be downloaded to?

Other torrent programs you could try are uTorrent and Azureus too

---

### Post by eentonig on 2007-08-23
Open a terminal and type

> whereis  ktorrent


ie.
> whereis btdownloadheadless.bittorrent
btdownloadheadless: **/usr/bin/btdownloadheadless.bittorrent** /usr/bin/btdownloadheadless /usr/bin/btdownloadheadless.bittornado /usr/X11R6/bin/btdownloadheadless.bittorrent /usr/X11R6/bin/btdownloadheadless /usr/X11R6/bin/btdownloadheadless.bittornado /usr/bin/X11/btdownloadheadless.bittorrent /usr/bin/X11/btdownloadheadless /usr/bin/X11/btdownloadheadless.bittornado /usr/share/man/man1/btdownloadheadless.1.gz

I don't use ktorrent, so I used another app to show how it works

---

### Post by wolfen69 on 2007-08-23
go to system>preferences>main menu  to add ktorrent to menus.

---

### Post by zyth on 2007-08-23
Just type:
> 
which ktorrent

This will show you where ktorrent resides - probably /usr/bin

> zyth@linuxbox:~$ which deluge
/usr/bin/deluge

is, for example, what I get when I search for deluge (the gnome bittorrent client I use)

---

### Post by Inxsible on 2007-08-23
zyth, you are right. It is /usr/bin/ktorrent

:)

---

### Post by Armaniboy on 2007-08-23
Thanks the Whereis ktorrent command really helped when I wanted to download thing and got prompted with "Open with...":KS

---

### Post by Aishiko on 2007-08-23
there are many threads already on chossing Torrent programs.

---

### Post by amazingtaters on 2007-08-23
> **chrome307 said:**
> Are you looking for where your files will be downloaded to?

Other torrent programs you could try are uTorrent and Azureus too

Because I have to say every time I see someone recommend it, here I go. /rant

Don't use utorrent. While it is the official BitTorrent client, because of that affiliation on pressures being placed on BitTorrent by various organizations, it is CLOSED SOURCE. It may still be free, but it is no longer open, and so should be avoided. 
/end_rant

---

### Post by likemindead on 2007-08-23
I have to recommend Deluge. Great, simple, & works. I got it via Automatix2, I think.

---

### Post by Hallvor on 2007-08-24
> **amazingtaters said:**
> Because I have to say every time I see someone recommend it, here I go. /rant

Don't use utorrent. While it is the official BitTorrent client, because of that affiliation on pressures being placed on BitTorrent by various organizations, it is CLOSED SOURCE. It may still be free, but it is no longer open, and so should be avoided. 
/end_rant

Agree. uTorrent is closed source and has sold out to the **AA.

---

