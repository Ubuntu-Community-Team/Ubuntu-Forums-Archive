---
title: "No Login Screen Menu Item"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Mramius on 2007-12-07
I would like to add a new Login Screen theme, however there is no menu item under System > Administration.  How do I go about adding this item?

---

### Post by Dr Small on 2007-12-07
Try going to Sytem > Preferences > Main Menu
and finding Login Window or whatever under System > Administration in the main menu, and enabling it.

Dr Small

---

### Post by Mramius on 2007-12-07
It isn't there, anywhere.

---

### Post by Dr Small on 2007-12-07
Hmm. Well add a menu item then that launches this command:
```
gdmsetup
```

That is the actual command to launch it.

Dr Small

---

### Post by Mramius on 2007-12-07
Hmm, it appears gdm wasn't installed. I sudo apt-get install gdm'ed and it kicked back that GDM wasn't running, that I must be running KDE or something.  I assure you I'm not.

---

### Post by Dr Small on 2007-12-07
Maybe you had KDM or XDM installed.

---

### Post by Mramius on 2007-12-07
Neither are installed.  When I log out, though, I go to a command prompt.

---

### Post by Dr Small on 2007-12-07
So, did you install GDM and then run gdmsetup ?

---

### Post by Mramius on 2007-12-07
Yes.  And when I do I get an error box telling me I must be using KDM or XDM, which I'm not.

---

### Post by Dr Small on 2007-12-07
Can you please post that exact error message here?

---

### Post by Mramius on 2007-12-07
**GDM (GNOME Display Manager) is not running.**

You might be using a different display manager, such as KDM (KDE Display Manager), CDE login (dtlogin), or xdm. If you wish to use this feature, then your system will need to be configured to use GDM instead.

---

### Post by Dr Small on 2007-12-07
Ok. Now, try running:
```
sudo dpkg-reconfigure gdm
```

---

### Post by Mramius on 2007-12-07
[I]~$ sudo dpkg-reconfigure gdm
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.
~$ [/I]

---

### Post by Mramius on 2007-12-07
If anyone is interested, I typed 

```
sudo /etc/init.d/gdm restart 
```

to resolve this issue.

---

