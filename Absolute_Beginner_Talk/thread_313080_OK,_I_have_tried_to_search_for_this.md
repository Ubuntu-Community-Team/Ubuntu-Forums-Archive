---
title: "OK, I have tried to search for this"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by HareBall on 2006-12-05
I have searched the forums and can't narrow down what I want.
So here is the question;
I loaded abcde and now I can't locate where it is to be able to run it. It isn't under deb or sound, so where? I did a search of my computer and as usual I didn't get any results. It shows as being loaded in synaptic manager](*,)

---

### Post by Judicata on 2006-12-05
Try opening Synaptic, right clicking on abcde, and then clicking on "installed files" it will give the some directories there.  The executable is probably in /usr/bin.

---

### Post by Shatrat on 2006-12-05
Have you tried just typing abcde in a terminal?
You could also run ```
slocate abcde
``` in a terminal and it will list every file with that in its name.

If installing didn't automatically create a menu entry, it isn't hard to add one.  Just right click your panel menu and select edit.  It's pretty easy to figure out.  If 'abcde' is in fact the correct command then you can just put that in the command field and when you click the menu, abcde will be launched.

---

### Post by bodhi.zazen on 2006-12-05
In a terminal,

which abcde

OR 

whereis abcde

locate will work, but after a fresh install you need to update the database: 

updatedb

then locate abcde

---

### Post by po0f on 2006-12-05
HareBall,

abcde is a command-line tool.  You can create a menu entry that will execute the command in a terminal, which is what you will want in this case.

---

