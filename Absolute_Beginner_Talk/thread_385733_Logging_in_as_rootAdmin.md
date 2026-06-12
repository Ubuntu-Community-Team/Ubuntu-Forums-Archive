---
title: "Logging in as root/Admin?"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by pdxuser on 2007-03-16
I'm using Xubuntu.  I'm wondering, is there any way I can log in as root or Admin?  When I get to the login screen where I normally enter my username and password, I can try root and the password, but Xubuntu just tells me the Admin can't login from that screen.

The particular reason I'm wanting to do this at this moment is so that I can move a new image into the /usr/share/xfce4/backdrops folder.  If there's a workaround just for this, I'd love to know it, but if there's some sort of general solution for having Admin access in whatever situation, I'd really like to know that.

---

### Post by Kateikyoushi on 2007-03-16
The root account is not enabled by default, use sudo or gksudo instead.

Reasons and more info can be found here. [LINK]("https://help.ubuntu.com/community/RootSudo")

---

### Post by mcduck on 2007-03-16
You don't need root account to do such things. Just run 'gksudo thunar' to open the file manager as root.

---

### Post by pdxuser on 2007-03-16
Is Terminal the only way to use sudo or gksudo?  Because Terminal pretty much requires me to know the command line way to do what I was trying to do the GUI way, which just ensures that this forum will be getting plenty of new "How do I...?" questions from me.

---

### Post by Kateikyoushi on 2007-03-16
You can use gksudo as well, read this what's the difference but I never used it. [LINK]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by v8YKxgHe on 2007-03-16
if you do in terminal:

```
gksudo thunar
```

that will open the file browser as root, so you'll be able to edit/move/delete things all through GUI. Just be careful as you can do a lot of damage using Thunar as root if you're not carful :P

---

### Post by pdxuser on 2007-03-16
Is there a way to tell it to save a backup of anything I change, just in case?

---

### Post by v8YKxgHe on 2007-03-16
not that I know of. By "you can do a lot of damage" I meant you could easily just select any folder and delete it, which will do a lot of damage (espically if it's / or /usr/ for example!)

---

### Post by pdxuser on 2007-03-16
Yuck,  There's no Ctrl-Z Undo in Thunar, I take it?

BTW, is kdesu the KDE analog of GNOME/Xfce's gksudo?

---

### Post by Quillz on 2007-03-16
> **pdxuser said:**
> Yuck,  There's no Ctrl-Z Undo in Thunar, I take it?

BTW, is kdesu the KDE analog of GNOME/Xfce's gksudo?
Yes, it is. And note that if Thunar doesn't work out for you, there are many other file browsers for you to try out.

---

### Post by cje on 2007-03-17
> **AlexC_ said:**
> if you do in terminal:

```
gksudo thunar
```

that will open the file browser as root, so you'll be able to edit/move/delete things all through GUI. Just be careful as you can do a lot of damage using Thunar as root if you're not carful :P

This command doesn't open a file browser ....? What do I do wrong?

---

