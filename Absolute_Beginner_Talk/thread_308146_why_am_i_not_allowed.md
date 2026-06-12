---
title: "why am i not allowed?"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by Hoborg on 2006-11-27
hey guys!
i'm all new to ubuntu and i have a problem.. ubuntu will not allow me to copy some new skins into my aMSN skin folder, is says that i am not allowed to do so. i have looked in the System > administration > users and groups, but i don't know what all the fancy things mean.. 
can somebody point me in the right direktion? T hanks. ;)

---

### Post by smile_sunshine on 2006-11-27
is your aMSN skin folder in your home directory or somewhere else?
:)

---

### Post by 56phil on 2006-11-27
First of all welcome to Ubuntu.:) I'm not sure what command you are using to install your skins. cp, perhaps? I suspect you are trying to put those files into a folder that you don't own. Prefix your command with sudo (super user do).

**[SIZE="3"]CAUTION:[/SIZE]** improper use of commands prefixed by sudo can ruin your day. Please use vast quantities of caution when doing this. Ubuntu requires that you enter your password for sudo operations as a reminder that you can damage your system. Good luck.

---

### Post by azkehmm on 2006-11-27
Well... if you want to drag-drop files around, you can open the terminal and write:
```
gksudo nautilus
```
This'll open a nautilus (the gnome file manager) that operates as a superuser/root, thus giving you the abilty to change everything and anything. 
For good measure, here's phil's last words again :

CAUTION: improper use of commands prefixed by sudo can ruin your day. Please use vast quantities of caution when doing this. Ubuntu requires that you enter your password for sudo operations as a reminder that you can damage your system. Good luck.

---

### Post by CatKiller on 2006-11-27
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Hoborg on 2006-11-29
thanks guys! the gksudo command solved it.. but isnt there a way to log in ads the administrator? so i don't have to use the  gksudo command?
it seems like ubuntu is very afraid that i wil ruin the system ;)

---

### Post by aysiu on 2006-11-29
> **Hoborg said:**
> thanks guys! the gksudo command solved it.. but isnt there a way to log in ads the administrator? so i don't have to use the  gksudo command?
it seems like ubuntu is very afraid that i wil ruin the system ;)
It's a lot easier to just create a keyboard shortcut or icon launcher for the command *gksudo nautilus* than to log in separately as root.

---

### Post by jrev on 2006-11-29
How do you create this Keybord shortcut ?

---

### Post by aysiu on 2006-11-29
> **jrev said:**
> How do you create this Keybord shortcut ?
1. Press Alt-F2
2. Type ```
gconf-editor
```
3. In the new window that appears, navigate to Apps > Metacity > Global Keybindings and find Command_1
4. Choose your keyboard shortcut (for this, I prefer ```
<Control><Shift>n
```)
5. Then go to Apps > Metacity > Keybinding Commands and find Command_1
6. Choose your command, which, in this case, is ```
gksudo nautilus
```

Now, when you press your key combination, Nautilus should launch as root.

---

### Post by CatKiller on 2006-11-29
Personally, I'd just use Alt-F2 -> gksudo nautilus for the first time, and then Alt-F2 -> up/down keys -> Enter, since it keeps a record of the commands you've used the Run Application dialogue for. Then I wouldn't have to either set, or remember, the keyboard shortcut. But that's just me, really, forgetful.

---

