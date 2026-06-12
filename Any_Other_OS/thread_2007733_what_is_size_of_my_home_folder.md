---
title: "what is size of my home folder??"
date: 2012-06-21
forum: Any Other OS
---

### Post by vikash_chandola on 2012-06-21
see attachment showing all drives through disk utility.
I think my home folder is of size 55 GB. if it's true then what is free space ?..consider that  i have not installed any software or not placed any file folder in desktop etc..

---

### Post by philinux on 2012-06-21
What version of ubuntu is this?

---

### Post by mike555 on 2012-06-21
looks like 55 gb is total size of Ubuntu partition , your /home must be inside that and if so it will expand as you use it .. up to filling it up.
  if you want to know the current size of your home folder while in ubuntu rt. click on home and check properties.

---

### Post by 1clue on 2012-06-21
Open a command line.

**du -hs /home/youruser** calculates the amount of space used by your home folder.
**df -h** shows all mounted partitions and the space used and available for those partitions.

I believe these two commands are ANSI, although the options vary from UNIX to UN*X.  These commands with the options shown work exactly the same between Linux and Mac OS X.

---

### Post by Frogs Hair on 2012-06-21
If you want to keep track for an account enable the status bar under edit in Nautilus.

---

### Post by vikash_chandola on 2012-06-21
> **philinux said:**
> What version of ubuntu is this?
My friend It is Linux mint 12.

> **mike555 said:**
> 
looks like 55 gb is total size of Ubuntu partition , your /home must be  inside that and if so it will expand as you use it .. up to filling it  up.
  if you want to know the current size of your home folder while in ubuntu rt. click on home and check properties. 	

thanks **mike** it works..:)
it says 46.8 GB free space. large enough for all of my tasks...
> **1clue said:**
> 
Open a command line.

**du -hs /home/youruser** calculates the amount of space used by your home folder.
**df -h** shows all mounted partitions and the space used and available for those partitions.

I believe these two commands are ANSI, although the options vary from  UNIX to UN*X.  These commands with the options shown work exactly the  same between Linux and Mac OS X. 	

thanks **1clue** for your commands.. However my work is done with **mike**'s answer so i didn't try it..

---

### Post by philinux on 2012-06-21
Moved to other os/distro talk.

---

