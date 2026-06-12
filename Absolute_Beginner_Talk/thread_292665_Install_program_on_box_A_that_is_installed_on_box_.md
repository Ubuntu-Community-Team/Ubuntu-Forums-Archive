---
title: "Install program on box A that is installed on box b - Both boxes are ubuntu (Dapper)"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by Portable_Jim on 2006-11-04
I was just wondering whether there was any easy way to install a component / program on  my Ubuntu [Dapper] box, when the component / program is installed on another Ubuntu [Dapper] box. 
I do not want to download the software again, and I cannot find the .deb files for the software.

If there is a way to do it using command line (that does not require tons of work) please post it - the command line is my friend.

---

### Post by soc on 2006-11-04
That's quite easy to do:
All packages you have installed are in this directory:
/var/cache/apt/archives
just copy it on a stick or burn it to a cd (you might need root priviledges, because the files are in a system dir)

---

### Post by Portable_Jim on 2006-11-04
> **soc said:**
> That's quite easy to do:
All packages you have installed are in this directory:
/var/cache/apt/archives
just copy it on a stick or burn it to a cd (you might need root priviledges, because the files are in a system dir)

There is not a .deb file there for the program I want to install. It might have been deleted.

---

