---
title: "How to make my file run from any director?"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by torx on 2006-06-09
i have a script which i would like to enable it to run from any directory without including the path.

for e..g

i wan to run it by typing:
testscript

instead of:

~/testscript


anyone help?

---

### Post by adwait on 2006-06-09
Put it in /usr/bin

---

### Post by Gustav on 2006-06-09
Or you can put it in /usr/local/bin

I think that directory is better for files that aren't produced by the packagemanager. (files from programs you compile also ends up here)

(but it is of course a matter of taste since both directorys work equally well)

---

### Post by mostwanted on 2006-06-09
[QUOTE=Gustav](files from programs you compile also ends up here)[/QUOTE]

Not in all cases.

---

### Post by Gustav on 2006-06-09
[QUOTE=mostwanted]Not in all cases.[/QUOTE]
OK, you're right. But in most cases :)

(And I hate when they end up in other places so that you can't find them)

---

### Post by DougC on 2006-06-09
Or if you don't want to move it you could add that directory to your path.

---

### Post by mostwanted on 2006-06-09
[QUOTE=Gustav]OK, you're right. But in most cases :)

(And I hate when they end up in other places so that you can't find them)[/QUOTE]

Well, if you installed using checkinstall (which you should) then you'll be able to see what files were installed where if you look up the package in Synaptic.

---

### Post by steve.horsley on 2006-06-09
Putting it in /usr/bin or /usr/local/bin makes it useable by all users. If you want to keep it private to yourself, you can create a ~/bin directory for all your scripts like that, and add it to your path by adding a line something like:
**export PATH=~/bin:$PATH** 
to the file **~/.bashrc**. 
Note that you need to restart gnome before gnome-terminal windows will see the change.

---

### Post by Gustav on 2006-06-10
[QUOTE=mostwanted]Well, if you installed using checkinstall (which you should) then you'll be able to see what files were installed where if you look up the package in Synaptic.[/QUOTE]
You're right again. :)

When handling debs (e.g. using checkinstall) there is no need for knowing where the files went (at least most of the times), you can use synaptic or apt to remove your programs (which is the main purpose (for me at least) of knowing where they went).

---

