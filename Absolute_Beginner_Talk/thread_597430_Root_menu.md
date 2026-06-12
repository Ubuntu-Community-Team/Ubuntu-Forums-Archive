---
title: "Root menu"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Niniel on 2007-10-30
Hello,

Is there a way to get a root menu in Gnome? It doesn't seem to be built in. (If it is, where can I switch it on?)
I have 7.10, and Compiz as well. 

If Gnome doesn't support that, which desktop a/o WM does?

Thanks.

---

### Post by DSn0wMan on 2007-10-30
I am not sure about a root menu, but if you need to open an application as root you can do so by hitting ctrl+F2 to bring up the run dialog and type in gksu <program-name>. ex. open nautilus as root.
```
gksu nautilus
```

---

### Post by Niniel on 2007-10-30
Sorry, I guess I didn't make myself clear enough, or maybe I used the wrong term.

What I mean with "root menu" has nothing to do with root access (I think). I just want to be able to click on the desktop and get a menu at the mouse pointer. MWM offered that capability, and I think NextStep and its clones/emulations do too.

---

### Post by jonobr on 2007-10-30
When you say root on linux, people will automatically think you want to do things as good or super user,
Assuming when you are on the desktop and right click you get something menu saying create folder , create launcher yadda yadda, are you seeing that?

---

### Post by eapache on 2007-10-30
If you mean a unified menu instead of the default three across the top, just right-click on the panel, 'Add to Panel', and choose 'Main Menu' down near the bottom.

---

### Post by Niniel on 2007-10-30
Sorry, what I mean is something like this:

[http://www.cs.wisc.edu/csl/cs1000/node19.html]("http://www.cs.wisc.edu/csl/cs1000/node19.html")

I'll check out the things you suggested, maybe that's what I'm looking for. 

Sorry about my (lack of correct) terminology.

---

### Post by llamakc on 2007-10-30
The answer is yes, but I don't know if Nautilus offers that. You should be able to install OpenBox and then replace Metacity by running:

```

openbox --replace

```

And get the root menu you're speaking of. You can also install any of the MANY window managers available in the repositories.

---

### Post by eapache on 2007-10-30
For what you mentioned in the link, just right-click on an empty space on the desktop.

---

### Post by Niniel on 2007-10-31
Ok, in that case, how do I edit that pop-up menu so that it shows my applications?

---

### Post by urukrama on 2007-10-31
This is a question that comes up regularly on these forums, and I'm afraid there is no simple answer. You could try another window manager, like Openbox, as has already been suggested. Or you could use a different desktop environment, such as Xfce, which does have a desktop menu.

I have no idea what the person is talking about on the page you linked to. As far as I know, Gnome never had a root-menu of the nature of Xfce's or Openbox'.

There is a way to edit the menu that comes up now (the Nautilus menu); I'll see if I can find some of the previous threads about this.

Compiz-Fusion might have a root menu also. I'm not sure, but it might be worth checking it out.

---

### Post by Niniel on 2007-10-31
All right, thank you.

As for the link, that was not about Gnome, I only put that there to help explain what exactly it was I am looking for.

---

### Post by urukrama on 2007-10-31
> **Niniel said:**
> As for the link, that was not about Gnome, I only put that there to help explain what exactly it was I am looking for.

Oh, I must have misread it then. 

As for those other threads about this, check out the following:

[1. Right Click Menu?]("http://ubuntuforums.org/showthread.php?t=469043&highlight=xfce+menu+desktop")

[2. Is it possible to make the menu...]("http://ubuntuforums.org/showthread.php?t=452175&highlight=xfce+menu+desktop")

[3. Customise Gnome desktop popup menu -- how?]("http://ubuntuforums.org/showthread.php?t=228371")

[4. Is there a way to Fluxbox Menus Without Fluxbox?]("http://ubuntuforums.org/showthread.php?t=452462&highlight=xfce+menu+desktop")

Hope this helps.

---

### Post by Niniel on 2007-11-09
Yes, thanks.
Sorry, I got sidetracked - I ran into Black Box for Windows, and I've been playing around with that for a while now instead of Ubuntu.

Funny how some things make their way to Windows... there's even sudo for Windows. Good thing I knew about it from Ubuntu when I discovered that. :)

---

### Post by Niniel on 2007-11-11
Tried xfde desktop, but compared to Gnome it's awful, no root menu is worth that. Oh well, one to take off the list.

---

### Post by urukrama on 2007-11-11
> **Niniel said:**
> Tried xfde desktop, but compared to Gnome it's awful, no root menu is worth that. Oh well, one to take off the list.

Its defaults are not that great (especially in Xubuntu), but it is pretty customizable. My initial reaction was the same, but I prefer it now over Gnome.

---

