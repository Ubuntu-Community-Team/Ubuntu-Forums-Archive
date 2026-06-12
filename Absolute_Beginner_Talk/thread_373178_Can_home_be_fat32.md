---
title: "Can /home be fat32 ?"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by islander_810 on 2007-03-01
Can i mount /home to a fat32 partition during installation itself?

---

### Post by energiya on 2007-03-01
I don't think that could be something good. fat32 doesn't support the linux style permissions or simlinks, and might be other things. My oppinion? DON'T!

---

### Post by islander_810 on 2007-03-01
k, thx. I wanted to mount it to fat32 cos recovering deleted files is easier from fat32 than ext. But i guess permissions are more imp

---

### Post by energiya on 2007-03-01
You could allways backup your home partition and/or make it do this at a given interval.

---

### Post by aysiu on 2007-03-01
You can mount /home/*username*/files as FAT32, but making /home or /home/*username* FAT32 will break your system.

---

### Post by MrHorus on 2007-03-01
> **aysiu said:**
>  making /home or /home/*username* FAT32 will break your system.

How so?

---

### Post by aysiu on 2007-03-01
> **MrHorus said:**
> How so?
Ubuntu expects certain configuration files in your home directory to be set to particular permissions and ownership. FAT32 does not support Linux permissions.

If you want to see an example of how permissions matter, check out [this thread](http://ubuntuforums.org/showthread.php?t=352547), where the user can't log in because the ~/.dmrc file has the wrong permissions set to it.

---

### Post by islander_810 on 2007-03-01
That's true, but i guess i'm lazy. I reduce my work as much as possible :) Anyway, thx for that

The same thing happ to me too. Mine was even worse with even the root user facing probs. Don't remember it so well but the word dmrc sure rang a bell. I just reinstalled Ubuntu. K, so no mounting the home in fat32. Here's what i actually want to do. I want to ensure that certain files in my /home/username folder can be recovered if deleted accidently. What's the best way to do that?

---

### Post by aysiu on 2007-03-01
> **islander_810 said:**
> Here's what i actually want to do. I want to ensure that certain files in my /home/username folder can be recovered if deleted accidently. What's the best way to do that? "Delete" them (i.e., move them to the trash) only through the graphical file browser, and never empty the trash can.

If you ```
rm *filename*
``` in the terminal, your file is pretty much gone.

---

### Post by islander_810 on 2007-03-01
lol, i want to ensure that if they're deleted accidently, i should be able to recover them and u're asking me to delete them on purpose. How's that gonna help?

---

### Post by aysiu on 2007-03-01
> **islander_810 said:**
> lol, i want to ensure that if they're deleted accidently, i should be able to recover them and u're asking me to delete them on purpose. How's that gonna help?
Moving a file to the trash can isn't deleting it. It's just moving it somewhere out of your way. Those trashed files can be easily recovered later.

---

### Post by Tomosaur on 2007-03-01
There are ways to make rm only move your file to the trashcan or some other directory. Essentially, you just make the 'rm' command point to 'cp', and tell it to always move <filename> to ~/.Trash. This can be done by alises, scripts, etc etc etc. There are a few threads floating around on how to do that.

---

