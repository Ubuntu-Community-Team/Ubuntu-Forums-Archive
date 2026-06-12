---
title: "[SOLVED] Somehow screwed up main menu"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Jake90 on 2008-01-22
Hi, I just screwed up my main menu editor. The only thing I can think of that may have messed it up is I uninstalled evolution through synaptic. Now the main menu editor disappeared from under system and when I try accessing keyboard shortcuts I get "Error Failed to execute child process "gnome-keybinding-properties" (No such file or directory)
Does anyone know what I screwed up or how to fix it? Thanks, if any more information is asked just tell me and I'll put it up as soon as possible

---

### Post by PeterJS on 2008-01-22
The menu editor is named alacarte, try running it from the run dialog (alt+f2), or a terminal.

---

### Post by Jake90 on 2008-01-22
> **PeterJS said:**
> The menu editor is named alacarte, try running it from the run dialog (alt+f2), or a terminal.
Thanks a lot but I can't use the terminal or the run box right now. Before I logged off I tried going to my home folder and it said it can't be found. Then I logged off and now after I log in all I see is a brown screen and nothing opens at all. I try ctrl-alt-del and nothing happens so I have to push the power button to get out. I am sort of desperate right now.

---

### Post by philinux on 2008-01-22
You might need to reinstall ubuntu-desktop

---

### Post by rosegarden78 on 2008-01-22
If all else fails try adding these packages from a terminal

sudo aptitude install kde
sudo aptitude install xfce

Choose XFCE Session from the menu next time you login.
Press Alt-F2 and type nautilus
Press Alt-F2 and type xgamma -gamma 0.75

Now you're running a Gnomish desktop on Xfce.  Remember to customize your Xfce panel.  If that doesn't work install blackbox or fluxbox and choose a session and run nautilus and also kicker.

---

### Post by Jake90 on 2008-01-22
> **philinux said:**
> You might need to reinstall ubuntu-desktop
how do  I do that?

---

### Post by PeterJS on 2008-01-22
> **Jake90 said:**
> how do  I do that?

From the command line (press ctrl + Alt + F1 to get to a physical console):
```

sudo apt-get install --reinstall ubuntu-desktop

```

---

### Post by Jake90 on 2008-01-22
thanks it worked

---

