---
title: "Can I delete the installed Packages"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by ahickey on 2007-05-09
Hi,

I have 7.04 up and running and I have done a number of updates.
They were all downloaded to my Home Folder.

My question is:
Can I delete all these from my Home Folder or are there config files left behind that would cause the system to fail.

A real Newbie question, but I would prefer to check before messing the whole thing up.

Thanks for any help.
Albert.

---

### Post by Kobalt on 2007-05-09
You don't actually need to clean these files manually, if there are some packages that you don't use any more it will be automatically removed during updates. 
Ubuntu is clean, remember it's not windows :)

PS: updates are never downloaded to your Home directory, all of this is stored in your / directory under root privileges.

---

### Post by viciouslime on 2007-05-09
They shouldn't have been downloaded to your home folder... how did you perform these updates?

---

### Post by ahickey on 2007-05-09
I have attached a screen shot of my Home Folder so you can see what I'm talking about.

I did the installs using the Synaptic Package Manager.

---

### Post by Cypher on 2007-05-09
Hmm, that's strange, those directories shouldn't be in your home directory. The packages are downloaded into /var/lib/apt/cache. And you can use "apt-cache clean" or something to clean them out.

What files are under some of those directories?

---

### Post by ahickey on 2007-05-09
Attached is a screen capture of the .nautilus folder

---

### Post by Kobalt on 2007-05-09
These directories (hidden normally) aren't updates, they are your personal setting directories. Do not delete them or you will loose your bookmarks, plugins and extensions in Firefox for example.

---

### Post by ahickey on 2007-05-09
Ahhh. now I get it.

I have hidden files visible due to my experience with important files being hidden by Windows.

Thanks for that.  I'll just allow them to be hidden and go back to being a dumb user

---

### Post by Cypher on 2007-05-09
..back to informed dumb user..:)

---

