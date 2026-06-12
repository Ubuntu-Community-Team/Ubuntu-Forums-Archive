---
title: "error while deleting..."
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Fittersman on 2007-01-14
in my trash can i have a few files that i want to delete, but it gives me an error "Error While Deleting" I think its a leftover from when i wanted to install salvage or some game, then it was too slow on my computer so i deleted it and now its stuck in the trash.

it says "(filename) cannot be deleted because you do not have permissions to modify its parent folder."

sooo.....

---

### Post by mykalreborn on 2007-01-14
you should first make sure you don't need those files. then type this in the terminal:
```
cd .Trash
sudo rm -R *file/foldername*

```
"Trash" must be written with capital letter - linux is case sensitive

---

### Post by faraazs on 2007-01-14
this has to do with the permissions of your home folder...have you tried to delete it using the sudo command?

open a terminal and go to your home folder. Navigate into the .Trash folder using ```
cd .Trash
``` and then ```
sudo rm filename
``` - remember to add the -r flag if its a directory as this will make the rm recursive.

---

### Post by Fittersman on 2007-01-14
thanks, works good

---

