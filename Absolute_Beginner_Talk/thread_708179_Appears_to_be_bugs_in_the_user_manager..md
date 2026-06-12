---
title: "Appears to be bugs in the user manager."
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2008-02-26
Im using Xubuntu which appears to be the same app as ubuntu uses and have a bit of confusion. Maybe its normal and i just need some advice on how to use it properly.

No1:
Every time i create a user it adds 2 groups of the same name. Shouldnt it only add 1?

No2: 
How do i add users to a group? I created a group called SharesNFS for all who need RW permissions to my network shares. When i check the boxes for the users i want to add and go back into the group they are all unchecked again!!. Also, look looking in other groups, users who should have permissions are not checked :confused:

---

### Post by Crooksey on 2008-02-26
```

$ sudo useradd -m <username> #this creates the new user with a home dir, if you dont want them to have a home dir, then dont use -m
$ sudo gpasswd -a <username> <group> # this adds a user to a certain group
```

I belive other users have posted issues with the user management GUI, so the commands will work, the user management should be hopefully fixed within a few updates.

---

### Post by dgrafix on 2008-02-26
Is there any app replacement for a gui version? 

i dont mind the command line for some stuff, buf for others i prefer a proper visual system to keep tabs on things.

---

