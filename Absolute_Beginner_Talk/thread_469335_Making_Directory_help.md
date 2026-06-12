---
title: "Making Directory help"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Darth_Maul on 2007-06-09
I know how to make a Directory in my home folder , but how to you make it else where.  LIke a  inside a folder or some place else

I was thinking some thing like mkdir /whatever/whatever

---

### Post by Bohlio on 2007-06-09
i think thats right. Or maybe you "cd" to the directory first then "mkdir blahblah"

---

### Post by RedSquirrel on 2007-06-09
If you want /home/username/foo/bar:

~ is a shortcut for /home/username, so you can do:

```
mdkir ~/foo
```and then

```
mdkir ~/foo/bar
```If you were already in the directory /home/username, you can do

```
mdkir foo
```and then

 ```
mdkir foo/bar
```
If the foo directory exists, you can change directory to foo and then make the bar directory there:

```
cd foo
mkdir bar
```

---

### Post by browndog on 2007-06-09
Also keep in mind that if you want to make a directory (folder) in certain restricted places in your file system, that you'll have to do it as Root.  Let's say you were in the /usr/local folder...to make a folder there you would type:

```
su mkdir directoryname
```

It will ask you for a password, which is your user password.  When you preface the mkdir command with su, your telling Linux you want to switch user to Root.  You can use su before any command to execute it as the Root user.

---

### Post by Bohlio on 2007-06-09
Isnt it "sudo"? or can just typing "su" work the same.

---

