---
title: "synaptic"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by greyash99 on 2006-07-10
I tried to enter new repos in synaptic but I messed up.  Now it says could not download all repository indexes.  None of the other repos I had before will load now.  Help please!

---

### Post by lordlollo on 2006-07-10
If you want a working, fresh sources.list, you can use

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Anyway, remember that before messing up such files, it's always better to back them up... ;)

---

### Post by greyash99 on 2006-07-10
should I clear my current repositories and put those in instead?

---

### Post by lordlollo on 2006-07-10
Well, before clear anything, try this

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

So you have ex exact copy of your messed up repo file.

Then from a terminal

```
gksudo gedit /etc/apt/sources.list
```

and replace all the lines with your brand new sources.list as provided from the site I linked. Save the file and close the editor.

Now

```
sudo apt-get update
```

Now eveything should work. If this is not the case, you can restore your old sources.list (even if it is screwed)...

Cheers

---

### Post by greyash99 on 2006-07-10
thanks helped a lot.

---

### Post by lordlollo on 2006-07-10
you're welcome

---

### Post by Dinerty on 2006-07-17
Brilliant guide here, I am also a newbie and totally messed up my repo's, if it wasnt for this guide i would of been totally stuck.

I did a search and found many people who have this problem, perhaps this could be a sticky or something?

---

