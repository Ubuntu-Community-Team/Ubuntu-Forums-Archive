---
title: "Getting my mac parition to mount as root?"
date: 2009-04-03
forum: Apple Hardware Users
---

### Post by mattgaunt on 2009-04-03
Hey everyone

I just decided i wanted to get at my music on my macbook partition, so I started googling and found people suggesting changing the permissions in mac os x and lo and behold I can get at my user folder and see my documents, photos, music etc however when I click on them it says I dont have permission.

So i ran sudo nautilus and this fixed the problem and i could get at my files.

So the question is, can I get the partition to mount as root so any old application can get at it without me having to do anything?

Many thanks for any help and sorry if this is a common problem, I just couldnt see a clear answer anywhere

Matt

---

### Post by cyberdork33 on 2009-04-03
It sounds like you changed access permissions on the folder, but not the contents of the folders.

---

### Post by mattgaunt on 2009-04-03
Well i changed the permission of my home folder and some of the folders within, and at the moment its not even letting me view what inside the folders, only whats inside the home folder.

so Im bit lost with what to do :-S

---

### Post by cyberdork33 on 2009-04-03
> **mattgaunt said:**
> Well i changed the permission of my home folder and some of the folders within, and at the moment its not even letting me view what inside the folders, only whats inside the home folder.

so Im bit lost with what to do :-S
you need to boot up osx, and change the permissions (recursively) to allow read access to all

---

### Post by mattgaunt on 2009-04-04
Cheers cyberdork.

I managed to get it working by doing the following *Dont do this if security is a concern cos its enabling anyone and everyone to have access to your files to read and write*:

Just went to directory /Users/

Right clicked on my home folder and selected Get Info

At the bottom clicked on the padlock and changed the setting for everyone to Read & Write

Then underneath that box there is a cog (Next to the + and - sign) select that and select apply to all enclosed files.

It'll come up with a warning message, ok it and then when you next boot into ubuntu you should be all ok to view your files :-)

---

### Post by cyberdork33 on 2009-04-06
> **mattgaunt said:**
> Cheers cyberdork.

I managed to get it working by doing the following *Dont do this if security is a concern cos its enabling anyone and everyone to have access to your files to read and write*:

Just went to directory /Users/

Right clicked on my home folder and selected Get Info

At the bottom clicked on the padlock and changed the setting for everyone to Read & Write

Then underneath that box there is a cog (Next to the + and - sign) select that and select apply to all enclosed files.

It'll come up with a warning message, ok it and then when you next boot into ubuntu you should be all ok to view your files :-)

Yep, the only real other option is creating a user in Ubuntu with the same uid as your OSX user. They will then appear as the same user in both systems (the uid is the user id number, not your username).

---

