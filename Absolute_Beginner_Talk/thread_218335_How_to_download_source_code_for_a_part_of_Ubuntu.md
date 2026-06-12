---
title: "How to download source code for a part of Ubuntu?"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by netdance on 2006-07-18
OK, a somewhat advanced newbie question, but a newbie question nonetheless.

I need to download the sourcecode for the version of xscreensaver included with Ubuntu for a project I'm working on.

Yes, I'm sure I could search the web and find *some* version of this source, but I'd like to download the actual source.

Google has failed me - 30,000 hits on any given search, and the 200 or so I've looked at don't have the answer.

I know that the Package Manager has source repositories listed, and I've checked them, but none of the packages I've checked seem to have source.

So - what am I missing?  Thanks in advance for any hint at all, I'm willing to work to figure this out, but I'm at a dead end.

---

### Post by Indroth on 2006-07-18
sudo apt-get source *packagename*

(Type this in a terminal)

---

### Post by Arisna on 2006-07-18
```
apt-get source xscreensaver
```

Will drop the source code into the working directory.

---

### Post by rmjb on 2006-07-18
> **Indroth said:**
> sudo apt-get source *packagename*

(Type this in a terminal)

So *that's* how you do it!

- rmjb

---

### Post by netdance on 2006-07-19
Thanks guys!!!  That does it.  I knew it was something obvious.

Wish Syaptic handled source, but I guess that's not the purpose of the program.

---

### Post by mdecler2 on 2007-01-17
This is what happens to me:
```

$ sudo apt-get source pypanel
$ Password:
$ Reading package lists... Done
$ Building dependency tree... Done
$ E: Could not open file 
$ /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_source_Sources - open (2 No such file or directory)

```

Indeed, no such file exists in that folder. However, I do find,
```

archive.ubuntu.com_ubuntu_dists_dapper_restricted_source_Sources
archive.ubuntu.com_ubuntu_dists_dapper_universe_source_Sources

```

How should I go about making such a file? Or what, alternatively, can I do to download source code?

Any help or comment is appreciated.

---

