---
title: "I don't understand how to find or run some programs on kubuntu"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by iteyoidar on 2006-02-26
1.  Firefox is supposed to be installed on kubuntu.  It says it is on that Adept program.  Where is it?  I can't find it in any menu or folder, and I went to find files/folders and searched for firefox and it turned up nothing.

2.  I downloaded the .deb file for gaim, right clicked it and selected to install it.  I found the executable file for it in /user/local/bin but I can't figure out how to make it do anything..Adept says that this is installed as well.

---

### Post by vbmaster on 2006-02-26
Did you forgot your ubuntu girlfriend?

Just give a call to console and type firefox or gaim and give feedback of what happened... ;)

stay cool ;)

---

### Post by aysiu on 2006-02-26
First of all Firefox and GAIM are not installed by default on Kubuntu, so you used Adept to install these, correct?

If they are installed, press Alt-F2 and type ```
firefox
``` and see if it pops up or press Alt-F2 and type ```
gaim
``` to see if it pops up.

If either or both applications start, then you simply don't have a menu entry for them. If they don't, they're not really installed.

If they're not really installed, perhaps you might be misconstruing Adept's marking packages for installation as meaning the packages are actually installed. After you mark them, you still need to commit changes.

a .deb on your desktop has nothing to do with Adept.

---

### Post by iteyoidar on 2006-02-26
Firefox:
I press alt+F2, type in firefox, hit enter, it says "could not run the specified command".  I also tried uninstalling firefox in Adept, commit changes, install firefox, commit changes(I presume this will reinstall it :) ) and the same thing.

Gaim:  This is works slightly better.  When I type "gaim" into run window, the gaim logo comes up in place of the K.  However, when I hit run, there's a little gaim logo jumping up and down by my cursor and I see a button for it on the bar at the bottom, like it's working, but nothing ever comes up and it eventually goes away.

---

### Post by PsychoTrauma on 2006-02-26
Try opening a console and typing:

sudo apt-get update
sudo apt-get --purge remove mozilla-firefox gaim
sudo apt-get install mozilla-firefox gaim

---

### Post by iteyoidar on 2006-02-26
I told Adept to uninstall Gaim just before accidentally, btw

first command returns
```
Reading package lists... Done
```

second command:
```
reading package lists... Done
Building dependency tree... Done
Package mozilla-firefox is not installed, so not removed
Package gaim is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
```

Third command:
```
Reading package lists... Done
Building dependency tree... Done
Package mozilla-firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-firefox has no installation candidate
```

---

### Post by PsychoTrauma on 2006-02-26
Could you please post your source list?
open a console and do:
sudo kwrite /etc/apt/sources.list

then paste what is says in that file here.

---

### Post by iteyoidar on 2006-02-26
That worked, thank you!  I didn't know about that file, it had the main download locations(or whatever) commented out, I uncommented them and was able to install everything.

---

