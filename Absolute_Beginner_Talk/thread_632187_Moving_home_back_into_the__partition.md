---
title: "Moving /home back into the / partition"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by tonyr1988 on 2007-12-05
There are lots of tutorials / questions about moving /home to its own partition, but how do you do the opposite? I have it on my external hard drive right now, but it's giving me *tons* of problems (most of them are because I can't unmount it).

What can I do to move /home back to the / partition? If I just remove the entry in my /etc/fstab file, will it automatically make one for me in /? Or do I need to use a LiveCD and go from there?

---

### Post by viking777 on 2007-12-05
I haven't done it myself, but this is how I think it would go:

Go to Users and Groups and create a new account (if you uname is fred you might call it fred1).

When you are sure that works copy the contents of your home folder to /home/fred1.
When you are sure that you have access to all your documents under fred1 go back to Users and Groups and delete user 'fred'

When you are sure that fred1 still works go back to Users and Groups and rename fred1 back to fred.

Only guessing though so 'Caveat Emptor'  as they say!!

---

### Post by philinux on 2007-12-05
How come it wont unmount? Are you getting any messages when you try.

---

### Post by tonyr1988 on 2007-12-05
I always says that it's busy. I assumed that this is because it's my /home, but I wasn't positive. Should you be able to umount your /home?

---

### Post by vikram on 2007-12-05
normally why would you want to unmount your /home ? 

you can use the live disk to make the changes to the /etc/fstab on your disk after creating a new home partition.

---

