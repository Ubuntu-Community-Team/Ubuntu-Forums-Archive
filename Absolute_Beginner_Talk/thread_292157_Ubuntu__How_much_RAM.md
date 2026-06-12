---
title: "Ubuntu:  How much RAM?"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2006-11-03
How much RAM does it take to run Ubuntu?
I have a computer with 128mb of ram, and am kind of cautious about running it.
It's going to become a server, so is there a way I could quit the GUI and just have it come up to a terminal on bootup?

(and how would I start the GUI from the terminal?)

---

### Post by Mimsy on 2006-11-03
You could install the server version. :)

---

### Post by PriceChild on 2006-11-03
I'd go for xubuntu if you're going to be using any kind of gui.

You will DEFNIATELY need to install from the "alternate cd". This is a text based installer.

If you're logged into terminal and have a DM set up, then typing ```
startx
```will get you all logged in and everything.```
sudo /etc/init.d/(g)(k)(x)dm start
```Will also do the job, but bring you to a login screen.


EDIT wooooo 2000th post :D

---

### Post by Anonii on 2006-11-03
PROTIP: Debian Sarge, for great justice.

---

### Post by chris062689 on 2006-11-03
Is there a way to disable the GUI on startup though?  To where it would just boot into the terminal?

---

### Post by CatKiller on 2006-11-03
> **chris062689 said:**
> Is there a way to disable the GUI on startup though?  To where it would just boot into the terminal?

That's exactly what the server install does.

No GUI whatsoever.

---

### Post by chris062689 on 2006-11-03
So if I installed Ubuntu Server, it would be no different than Xubuntu Server (except a few programs and the gui of cource.)
RAM wise I'm talkin about.

---

