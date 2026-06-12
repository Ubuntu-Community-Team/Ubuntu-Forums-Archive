---
title: "What GUI for giFT should I use for xubuntu? (And other questions)"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2006-10-07
So what gui should I use for the giftd with xubuntu. I used to use apollon with kubuntu. But I like xubuntu much better. And apollon says it is for KDE. I found two GUI's one called giFTtoxix and one called giFTui. They say that there for GTK2. What is GTK2? if there the one's i'm after what would anyone recommend? Is there any others?

Also I want to run the giftd on my ubuntu server and then configure the GUI to connect to that so that all my machines use the same giftd. Also so my sharing and downloading can occur with out my computer that I use being on. (Since the server is always on it makes sences). I have done this before both with kceasy and apollon but from memory I have to install the giftd onto those machines as well. Is this really nessercery since it wont even be using it? or maybe you need giftd to connect to other giftd's?

Any help will be awesome.

---

### Post by jaboua on 2006-10-07
I don't know for sure as I haven't tried, but AFAIK you only need giftd on the server, and if you then have a gift client, you can connect.

Apollon seems to have most features, however it's made for KDE yes - KDE is using the QT toolkit for making graphical user interfaces, while gnome and XFCE is using GTK2. So you're probably looking for a GTK2 client. I used giftoxic before - it's still in it's early stages it seems because in my experience searching is really slow and uses 100% CPU if you get lots of results, and some of the options (for example "browse users files" - not that I needed it, just wanted to test) didn't seem to work. And some things I didn't like: it didn't have any tray icon, in other words you need "alltray" to dock it, and you couldn't download a file by doubleclicking it, you need to right click -> download, and you have to configure gift with CLI utils before starting it (unless ubuntu comes with a default gift configuration).

I wanted to try the other client before, but it wouldn't compile because I had a too new GTK version and no package was available (this wasn't on ubuntu, there might be working ubuntu packages available)

---

### Post by Ayman on 2006-10-07
Back when I used giFT I liked giFTui more, GTK2 is a graphical library used by many programs, such as Gnome and Firefox, chances are that you already have it installed.

By the way, there is also [giFTcurs](http://www.nongnu.org/giftcurs/) which can be run from a terminal.

---

### Post by guysmiley25 on 2006-10-10
Chears for the tips guys. Also giFTcurs is awesome. They need to make more apps for the terminal.

---

### Post by guysmiley25 on 2006-10-10
Hey do any of you guys know how to start the giftd deamon on boot?

---

