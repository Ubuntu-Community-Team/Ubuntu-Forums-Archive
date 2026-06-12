---
title: "renaming files"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by pskipper on 2007-02-28
Hi,

I've managed to set up ubuntu and get the webserver running but had forgotten how case sensitive linux is (haven't used it since the 90's and forgotten all I knew)! Alot of my JPEGS transfered over from my old files as .JPG whereas the HTML link is to .jpg, how do I batch rename them?

Thanks

Philip

---

### Post by lukew on 2007-02-28
> **pskipper said:**
> Hi,

I've managed to set up ubuntu and get the webserver running but had forgotten how case sensitive linux is (haven't used it since the 90's and forgotten all I knew)! Alot of my JPEGS transfered over from my old files as .JPG whereas the HTML link is to .jpg, how do I batch rename them?

Thanks

Philip

You can use the mv command from the terminal.

There is also krename in the repos which might do what you are after, though i can not vouch for it as i have not used it. This has a GUI

Luke

---

### Post by finer recliner on 2007-02-28
in a terminal:

mv oldname.JPG newname.jpg

---

### Post by girishv on 2007-02-28
you can use this command to rename all the files in the present directory

rename 's/JPG/jpg/' *.JPG

The first word rename is the command and the next one within quotes is the syntax
typically used in sed/vi editors and the last one *.JPG is the files which has to be 
renamed. This is better than moving individual files

Girish

---

### Post by kittyhawk63 on 2007-02-28
.

---

