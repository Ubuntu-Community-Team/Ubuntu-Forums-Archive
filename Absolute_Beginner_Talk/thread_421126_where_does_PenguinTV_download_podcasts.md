---
title: "where does PenguinTV download podcasts?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by 1002285 on 2007-04-24
Creator of PenguinTV seems to be proud of the feature "You don't need to know where the podcasts are downloaded", but what if I actually want to know it? May-be it downloads on the root partition where I don't have any extra room? May-be I want to copy them to an external player - where do I find the files then?
I tried Democracy TV, too, by the way, and it just did not start.

---

### Post by spd106 on 2007-04-25
Unless you run the app as root (inadvisable) you will only have write access to two places your /home/user/ directory and /tmp/. It's likely that the files are put into a hidden directory, this means it starts with a ".", such as /home/user/.gnome2/ for example.

Have a look around, if they are given a common file suffix e.g. .mov then they should be too hard to find.

---

### Post by itsdaveperdue on 2007-07-03
~/.penguintv/media/

---

