---
title: "Oops! Forgot to backup"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Nolander on 2007-04-22
Hi all,

to keep it short. i stuffed up my pc and didnt backup is there any way i can access the stuffed partion and back up my docs and stuff on to a CD.  i have DSL, Ubuntu, puppy and remote explote all on a live dvd.

Ta,
Nolander.

---

### Post by desheikh on 2007-04-22
Heh :P Thats why I keep a live cd of knoppix handy at all times :)... The ubuntu live cd doesnt have any burning apps installed by default.

You can install apps on the ubuntu live cd as normal so shoudnt have a prob with that  either.. just that you need  to redo that process everytime you boot it.

Just mount your partition... something like..
# sudo mkdir /mnt/hda*

# sudo mount /dev/hda* /mnt/hda*

and you can backup all your data from there on

---

### Post by Nolander on 2007-04-22
Thanks desheikh,

Kubuntu come with k3b pre-install. :) but for some reason i cant read write or do anything to my 8 GB HDD when my 20 GB HDD is connected. i can only access it when its connected by itself. i used gpart to partion my 20GB thats when the problem started. I think.

Ta,
Nolander.

---

