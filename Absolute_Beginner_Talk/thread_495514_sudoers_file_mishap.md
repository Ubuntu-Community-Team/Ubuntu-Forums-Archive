---
title: "sudoers file mishap"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by desijays on 2007-07-08
i was going throug the man page for sudo and found that it depended on two files

So out of curiosity I wanted to just see the contents of the sudoers file in the /etc folder. 

( absolute path is /etc/sudoers )

When i tried opening it in vi, it said permission denied. So i used

"sudo chmod +r sudoers"

I got read permission for root, root group and others.

after being satisfied looking at the file, i closed it and tried changing the permission back to it original state.

so i did,

"sudo chmod o-r sudoers"

for which it said

"sudo: /etc/sudoers is mode 0444, should be 0440"

so i again tried,

"sudo chmod 0440 sudoers"

and again got 

"sudo: /etc/sudoers is mode 0444, should be 0440"

How do i fix this?

Im not able to use some commands that requiring sudoing. Ex. apt-get

Thanks

---

### Post by waster on 2007-07-08
The best way is probably to boot using the install live CD. You will then be able to sudo as normal, and chmod your sudoers back to the original.

---

### Post by ubuntu.daemon on 2007-07-08
do a
```
user@home: sudo passwd root
```
and set up root if you can before you get yourself into a bigger hole lol.
then nextime you have any troubles you can
```
user@home: su -
password:
root@home:
```
and your set from there for hole burying heh...

Oh and instead of using vi, why dont use use nano??  It all stays in the terminal, and you didnt ever say that you tried to 
```
user@home: sudo vi /etc/sudoers
```

vi is messy to me, nano is so clean and simple.....
:popcorn:

---

### Post by MoxJet on 2007-07-08
Use the command visudo to change sudoers file.

---

