---
title: "making links"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by fontenot_1031 on 2007-07-07
Would anyone know how to manually make links to files?  I have some large .iso files on my Windows partition and I want to make a link to them on my Ubuntu partition.

---

### Post by pbaumgar on 2007-07-07
> **fontenot_1031 said:**
> Would anyone know how to manually make links to files?  I have some large .iso files on my Windows partition and I want to make a link to them on my Ubuntu partition.

Do you mean a symbolic link to the ISO?

---

### Post by fontenot_1031 on 2007-07-07
I guess.  I installed PSX and I don't want to have two copies of the same iso on my computer.

But I'm not sure what you mean by symbolic link.

---

### Post by pbaumgar on 2007-07-07
> **fontenot_1031 said:**
> I guess.  I installed PSX and I don't want to have two copies of the same iso on my computer.

But I'm not sure what you mean by symbolic link.

A symbolic link is a reference to another file.  I'm not sure what PSX is, but do you mean you want to point to the ISO from one of your linux partitions? Or do you want to move the file from a Windows partition to a linux partition?

---

### Post by fontenot_1031 on 2007-07-07
> **pbaumgar said:**
> A symbolic link is a reference to another file.  I'm not sure what PSX is, but do you mean you want to point to the ISO from one of your linux partitions? Or do you want to move the file from a Windows partition to a linux partition?
"do you mean you want to point to the ISO from one of your linux partitions?"Yeah that's it.  PSX is the playstation emulator

---

### Post by Alterax on 2007-07-07
Make sure the windows partition is mounted.  Then use the ln -s command to make a symbolic link:

Let's say your Windows partition is mounted under /media/winpart, and the iso file is file.iso which is in the main directory of that partition.  It would be /media/winpart/file.iso

Let's say you want to put it in /home/yourusername.  Do this command:

ln -s /media/winpart/file.iso /home/yourusername

if it gives you any argument about not being able to make the file, add a sudo to the front of it, though that should not be necessary.

--Alterax

---

### Post by Alterax on 2007-07-07
(Continuing)

Then you should be able to use the symbolic link you just created as if it were the original file, without making an actual copy of it.

---

### Post by Kingsley on 2007-07-07
Alterax's solution works fine. You could also hold your shift and ctrl keys while you drag the .iso file to your desired location. I don't know why Gnome can't make this more obvious.

---

### Post by fontenot_1031 on 2007-07-07
Thank you very much for your replies!  Problem solved

---

