---
title: "burn iso"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by maineman2 on 2008-01-12
Hi I want to burn an iso to cd. I have k3b How do I get the iso to my home folder and how do i get it to cd Thanks Dan

---

### Post by krendar on 2008-01-12
> **maineman2 said:**
> Hi I want to burn an iso to cd. I have k3b How do I get the iso to my home folder and how do i get it to cd Thanks Dan

Not sure what you mean by getting it to your home folder. If it is somewhere on the filesystem k3b will be able to open it. Look at the menus in k3b, there is a "Burn Image to CD/DVD" menu-item somewhere (sorry, I don't have it installed myself so I can't check the exact spelling or where the menu-item is.

edit: oh by the way, you can "mount" a ISO image as a filesystem if all you need is to get some files and don't necessarily need a disc. Here is how:

1. Open a Terminal Window.
2. Type "mkdir /mnt/iso" and press enter
3. Type "mount -o loop -t iso9660 file.iso /mnt/test" and press enter (replace "file.iso" with the name of your iso).
4. Now you can access the iso files in the /mnt/iso folder.

---

