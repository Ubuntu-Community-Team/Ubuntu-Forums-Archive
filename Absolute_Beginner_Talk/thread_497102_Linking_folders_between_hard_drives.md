---
title: "Linking folders between hard drives"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2007-07-09
Hi, I recently started putting all of my files on an external hard drive to save space. I wanted to make a link on my desktop that brought me to a folder on the external hard drive. I get an error when I try to do this. Is there another way of linking the folders? Thanks.

Oh, and the error message is: "Error "Operation not Permitted" while creating link to "(Location of folder on external hard drive)". Would you like to continue?"

---

### Post by Nekiruhs on 2007-07-09
> **kevindubrow said:**
> Hi, I recently started putting all of my files on an external hard drive to save space. I wanted to make a link on my desktop that brought me to a folder on the external hard drive. I get an error when I try to do this. Is there another way of linking the folders? Thanks.

Oh, and the error message is: "Error "Operation not Permitted" while creating link to "(Location of folder on external hard drive)". Would you like to continue?"
Whats the filesystem on the external drive? Fat32 and NTFS don't support Symlinks which is the default way of making links in Ubuntu.

---

### Post by kevindubrow on 2007-07-09
It is a Fat32. Is there an alternative, or is there a way to reformat the hard drive?

---

### Post by Nekiruhs on 2007-07-09
You could copy the data to your HD and refomat it with GParted ```
sudo apt-get install gparted
``` to install. You'd want to format it to ext3.

---

### Post by kevindubrow on 2007-07-09
Thanks. I'll get working on it.

---

