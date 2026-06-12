---
title: "basic commands help!!"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-05-22
what are the commands to change a file permission that is set to only root acess from another person when im root what do i type to change to all read+write and whats commands to delete a file in the terminal?

---

### Post by meng on 2006-05-22
I'm not certain I understand the questions completely, but the command:
chmod 666 [filename]
will make a file read+write-able for all users.

chmod a+rw [filename]
will do the same, but preserve executability if it exists.

Also refer to "chown" to change the file owner.

"rm" will delete files.

---

### Post by aysiu on 2006-05-22
Changing the file permission or ownership of a system file is a very bad idea. The permissions are the way they are for a reason.

You can, however, temporarily gain root privileges to modify files.
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by skinnygmg on 2006-05-22
here's a link to a list of bash commands

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by xtacocorex on 2006-05-22
You could also do chmod a=rw filename for changing all the permissions of a file.

Edit: It appears aysiu and skinnygmg and I all posted at the same time. I would heed aysiu's advice about the permission change.

---

### Post by Ben Sprinkle on 2006-05-22
alright heres my situation i got a folder and the permission owner is 'root' the only way im root is through terminal, permitions for folder is can view and modify for all but all the files in folder are locked and im trying to copy 2 files into the folder without terminal i try to copy em into folder says permission denied how do i copy these 2 files into folder through terminal whats commands?](*,)

---

### Post by xtacocorex on 2006-05-22
You need to add sudo before your move command:
sudo mv [filename]

---

### Post by Ben Sprinkle on 2006-05-22
ok ty for everything it worked

---

### Post by S{yndrom}e on 2006-05-22
Goat, if you want a visual way of moving files (i.e: GUI Interface) then type in terminal

sudo nautilus

or for Kubuntu i think

sudo konqueror

This will allow you to browse folders with root permission, meaning you can drag,drop,copy,and paste without getting permission errors.

---

### Post by Ben Sprinkle on 2006-05-22
holy crap didnt know this thanks loads way easier

---

### Post by S{yndrom}e on 2006-05-22
no problem glad to help ;)

---

### Post by xtacocorex on 2006-05-22
I'm glad to have helped also.

---

