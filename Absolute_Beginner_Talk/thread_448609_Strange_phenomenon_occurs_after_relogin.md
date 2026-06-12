---
title: "Strange phenomenon occurs after relogin"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by hoydooley on 2007-05-19
I use feisty. 
Everything works fine until I logout.
But after logout and login, icons on the wallpaper disapear and nautilus doesn't work.
When I browse menus on the top panel, menu items are not visually selected when I move a mouse pointer.
I think this strange phenomenon has been started since the last upgrade(security updates and recommended updates)
Any suggestions?

---

### Post by Metacarpal on 2007-05-19
In your System menu > Preferences > Sessions, under the Session Options tab, is "Automatically save changes to session" checked?

---

### Post by hoydooley on 2007-05-19
> **Metacarpal said:**
> In your System menu > Preferences > Sessions, under the Session Options tab, is "Automatically save changes to session" checked?

thanks for the reply. it isn't checked. and i don't want to check it. my problem is not about "saving changes to session".
i can't even use terminal after relogin. terminal doesn't respond at all.
nautilus doesn't respond. firefox sometimes responds sometimes not.

---

### Post by icechen1 on 2007-05-19
> **hoydooley said:**
> thanks for the reply. it isn't checked. and i don't want to check it. my problem is not about "saving changes to session".
i can't even use terminal after relogin. terminal doesn't respond at all.
nautilus doesn't respond. firefox sometimes responds sometimes not.

in login screen go to session->and choose GNOME fallsafe mode,is there still the problem?

---

### Post by hoydooley on 2007-05-19
> **icechen1 said:**
> in login screen go to session->and choose GNOME fallsafe mode,is there still the problem?

yes, it's same. the problem persists..
I included the snapshot of my screen when the problem occurred.
Terminal screen is empty. And home folder shown in the nautilus is empty although it has some files.

---

### Post by icechen1 on 2007-05-19
> **hoydooley said:**
> yes, it's same. the problem persists..
I included the snapshot of my screen when the problem occurred.
Terminal screen is empty. And home folder shown in the nautilus is empty although it has some files.

If desktop effets/beryl is enabled,try disable it

---

### Post by hoydooley on 2007-05-19
> **icechen1 said:**
> If desktop effets/beryl is enabled,try disable it

I disabled the desktop effect and the problem has gone!
But I still want to use the desktop effect. (It's one of the main reasons why I use ubuntu!)
Is there any other way to solve the problem without disabling it?

---

