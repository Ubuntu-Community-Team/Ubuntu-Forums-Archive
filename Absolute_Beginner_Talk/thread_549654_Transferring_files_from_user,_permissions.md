---
title: "Transferring files from user, permissions"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by dndrich on 2007-09-12
OK, so I set up Ubuntu Feisty on my brother's computer.  Very nice.  I created one user.  He then wanted a user for his son.  So I made a new user with administrative privileges, and tried to transfer the files to the son's user home folder.  I went into the file system from the brother's user, and cut and pasted them.  When I fired up the son, all the files were read only because the permissions were for the father.  So, I transferred them back.  I then tried to do it from gksudo nautilus, nautilus as root, and then the files were permission root!  So I put them back.  I solved it by sharing the folder, and then just copying them.  That worked.  Now they want to get rid of the son user, because it is too much of a pain to log back and forth.  So I have to copy the files back.  There has got to be an easier way than the way I did it.  Any idea how to easily transfer the files back to the father user, and get the permissions right, and then delete the son?

---

### Post by irishgoth8822 on 2007-09-12
go through the root file system and give the son access to the root?

or perhaps i misunderstand what youve already tried...hmm

---

### Post by nick_h on 2007-09-13
You could always copy the files and then change their ownership.
For example, to change the ownership of all files under the father's home directory type:
```
sudo chown -R father /home/father
```

---

### Post by dndrich on 2007-09-13
Now that's what I'm talking about.  OK, I'll try that.

---

### Post by nick_h on 2007-09-13
You may also wish to change the group.  You can also do this with chown:
```
sudo chown -R owner:group /directory
```
Alternatively look at the command *chgrp*

---

