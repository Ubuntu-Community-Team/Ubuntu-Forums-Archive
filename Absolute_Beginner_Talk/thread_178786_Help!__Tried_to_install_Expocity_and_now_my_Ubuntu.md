---
title: "Help!  Tried to install Expocity and now my Ubuntu is broken!"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by ThrobbingBrain66 on 2006-05-18
As stated in the title, I attempted to install Expocity using these directions:

[https://wiki.ubuntu.com/Expocity](https://wiki.ubuntu.com/Expocity)

there was some error about a conflict with another program and how I needed to find it and report the bug.  Anyway, now when I boot into Ubuntu, it stops loading at "Metacity Window Manager".  I am able to get to the command-line recovery mode, but can't seem to remove Expocity to use Metacity again, any ideas?

EDIT:  It loads up, but just takes a REALLY long time.

---

### Post by NoUse on 2006-05-18
Did you install expocity via "make install" or "checkinstall"?

**1a) Check Install:**
Run:
```
dpkg -l | grep -i expocity
```
you should see the exact name of the expocity package. It make include a version number.

then run:
```
sudo apt-get remove <packagename>
```

**1b) Make Install**
Go back to the directory with the expocity source and run:
```
sudo make uninstall
```

**2) After uninstalling expocity **
Once thats done run:
```
sudo apt-get install ubuntu-desktop
```

That should install all packages needed for ubuntu.

---

### Post by ThrobbingBrain66 on 2006-05-18
thanks, ill have to see if i can find where expocity was installed.

---

### Post by ThrobbingBrain66 on 2006-05-18
so that kinda worked...

now i have no window border so i cant minimize, maximize or close windows!  and the windows don't show up in the task bar

---

### Post by NoUse on 2006-05-18
did you run the last command I posted?  You need to have metacity reinstalled.

If its already installed I'm not sure how to reenable it.  I'm not a gnome guy.

---

### Post by joshrobinson on 2006-05-18
[QUOTE=NoUse]did you run the last command I posted?  You need to have metacity reinstalled.

If its already installed I'm not sure how to reenable it.  I'm not a gnome guy.[/QUOTE]

try installing metacity again

```
sudo apt-get install metacity
```
or
```
 metacity --replace
```

metacity is what gives you those window bars to minimize and close

---

### Post by ThrobbingBrain66 on 2006-05-18
Ah yes, all is well now.  Thank you gentlemen for your assistance.  It is most appreciated.

---

### Post by joshrobinson on 2006-05-18
[QUOTE=ThrobbingBrain66]Ah yes, all is well now.  Thank you gentlemen for your assistance.  It is most appreciated.[/QUOTE]

no problem
give it a reboot and make sure it comes back on fine and metacity loads.. if not you can always add metacity into your sessions by going to system > preferences > sessions, clicking the far right tab and adding

metacity --replace

but thats only if you have problems after a reboot, i doubt you will tho

---

