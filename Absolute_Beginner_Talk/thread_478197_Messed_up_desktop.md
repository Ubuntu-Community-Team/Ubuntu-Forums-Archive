---
title: "Messed up desktop"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by EvilBro on 2007-06-19
I recently switched to ubuntu 7.04 after trying it a while (and liking it a lot). After trying to log in today I got an error (something about closing within 10 seconds). I tried a reboot to see if that solved the problem and I indeed no longer got the error. But all is not well unfortunately. One symptom is dat all the icons in the main menu are gone. Another is that the buttons and icon on the top of windows (close button, etc.) are no longer on the edge of the bar. They are indented like the system expects the window to be smaller or something.

What could be the problem, and more importantly: how do I restore things?

---

### Post by Kobalt on 2007-06-19
First, Ubuntu doesn't usually happen to run into such troubles, you must have installed/removed something, tweaked somthing ?
Then, did you try to boot into recovery mode ?

---

### Post by Rui Pais on 2007-06-19
Hi, in order anyone can help you, you need to clear (crystal ball are expensive this days ;)) 
> **EvilBro said:**
> I recently switched to ubuntu 7.04 after trying it a while (and liking it a lot). After trying to log in today I got an error (something about closing within 10 seconds).
that should be the classic "Your session last less then 10 seconds,..." from gdm.
Do you mind to post the output of:
```
cat .xsession-errors
```
and of;
```
df -h
```

---

### Post by EvilBro on 2007-06-19
> **Kobalt said:**
> First, Ubuntu doesn't usually happen to run into such troubles, you must have installed/removed something, tweaked somthing ?
None of the above. I'm even pretty sure that there weren't updates yesterday (at least, I don't remember installing any).

> Then, did you try to boot into recovery mode ?
I will when I get home.

@Rui Pais: I will look at the session log when I get home. I did try df to see if the disk was full. It wasn't.

---

### Post by Rui Pais on 2007-06-19
ok.

Recovery mode is usefull when your X is crashed, but if i understand it correctly your gdm is working and you can even login. 
Is your gnome that is apparently borked.

Try, with no open gnome sessions, from a console (Ctrl+Alt+F1):
```
mkdir BAKUP
mv .gnome* BACKUP/
mv .gconf* BACKUP/
```
and then back to gdm (CTRL+Alt+F7) and login again.

---

### Post by EvilBro on 2007-06-19
> **Rui Pais said:**
> Try, with no open gnome sessions, from a console (Ctrl+Alt+F1):
```
mkdir BAKUP
mv .gnome* BACKUP/
mv .gconf* BACKUP/
```
and then back to gdm (CTRL+Alt+F7) and login again.
That didn't help. The title bar of a window still looks strange. Icons still missing (Update: got the icons back by going to menus & toolbars and deselecting and reselecting the option icons).

Trying to select 'theme' gets me this message:

"The default theme schemas could not be found on your system.  This means that you probably don't have metacity installed, or that your gconf is configured incorrectly."

---

