---
title: "Does anyone know how to reinstall Firefox?"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Happy_Man on 2007-01-28
I was messing with my copy of Firefox which came with Edgy, and came with me to Feisty, and is now kind of...bloated. :( It's doing odd things, and I can't fix them. Is there any way to reinstall the Firefox from the repos?

---

### Post by deadgobby on 2007-01-28
go into synatpic and reload FF 2.0 with feisty.

---

### Post by MkfIbK7a on 2007-01-28
well messing with it was a mistake since many other programs will not run if it doesnt

but anyway try reinstalling it in synaptic

---

### Post by GrammatonCleric on 2007-01-28
Is it the version of Firefox or is your Firefox Profile thats bloated?  If it is your Firefox profile...

 - Close Firefox 
- Rename your FireFox Profile.

```
mv .mozilla old_mozilla
```- Launch Firefox and it will create a fresh new profile minus any themes, extensions, etc  that you've installed.

-GC

---

### Post by moshuptrail on 2007-01-28
On my Dapper laptop firefox is installed in two places. (probably something I did)
It's in /usr/lib/firefox, and /usr/lib/mozilla-firefox
Check where it is on your fiesty setup.  The thing I found when installing 2.0 was that it's all in one place.  So if you download 2.0 and install it.  Just make sure it all goes in the right directory.  It doesn't sprinkle files all over the place like windows.  They are all right there.  To completely remove firefox, just sudo rm -r firefox (or mozilla-firefox).  Or better yet, sudo mv firefox firefox.old (rename the directory)

---

