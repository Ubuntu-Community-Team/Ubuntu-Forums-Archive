---
title: "Ubuntu Optimizer, maybe ?"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Disparition on 2008-02-01
The 4th day and yet another question. Being used to stupid Windows errors about registry and stuff. I wonder if there is a system optimizer for ubuntu. Like, an utility that removes unnecessary packages that aren't used by a program. Or something that detects errors that occur in the O/S.

Tried Orphan Packages so far. any suggestions ?

---

### Post by TonKi on 2008-02-01
sudo apt-get autoremove
removes packages that are not in use, built in

---

### Post by billgoldberg on 2008-02-01
This should help:

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html) (bookmark that page for future reference)

There is also an program in the repositories (system-administration -synaptic package mangement) call Bootup-Manager (bum).
There you can delete thing that don't need to load on your pc. Like when you are on a destkop, you don't need the laptop thing running, so you can turn those off. Idem for priting, bluetooth, ...

---

### Post by jan quark on 2008-02-01
I would be very very cautious with removing any packages from ubuntu

the ext3 file system which ubuntu uses does not need defragmentation, so it is different than in windows with ntfs and fat32

but coming back to system optimization 
you don't have to do any of that stuff

and do not remove any package before you exactly know what you are doing

many packages depend on each other and removing one can cause an avalanche of errors
I hope I scared you enough :)

---

### Post by Disparition on 2008-02-01
Well, most of them are recoverable through Synaptic manager, so it shouldn't be a major problem

---

