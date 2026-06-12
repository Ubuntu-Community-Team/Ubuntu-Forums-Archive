---
title: "Why ubuntu upgrade requires cdrom"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by axnotizes on 2006-03-17
My question is same as title, why when I perform an upgrade in ubuntu, apt-get prompts me for the cdrom?  Can't we just download the image from the repository?

I don't like to keep my cdrom in the drive. Is there a way that I can disable this?

Thanks.

---

### Post by meborc on 2006-03-17
your /etc/apt/sources.list file has a line at the beginning smthg with cd... just delete this line or # it out...

EDIT: the long way:

go to terminal, and insert those lines

**sudo gedit /etc/apt/sources.list**
make the change in the file, save and close
then do[B]
sudo apt-get update
sudo apt-get upgrade[/B]

when you are at it you might want to add some multiverse and universe repositories also... just search the forum for howto :)

---

### Post by aragorn2909 on 2006-03-17
Yes, simply edit the line in your sources.list that refers to your cd.  Add a # at the beginning of that line.

edit:  quick fingers meborc!

---

