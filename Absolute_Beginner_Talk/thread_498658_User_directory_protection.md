---
title: "User directory protection"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by viniosity on 2007-07-11
I've got a multi-user environment and I'd like a user to be able to see all his directories and I don't care if he can see the other directories either, but I'd like it so that if he enters another user's home folder that he can't see any of their files.  I was thinking this would be done with chmod but can't seem to find the right permissions?

For instance, if user1 is logged in he should be able to see everything in his /home/user1 directory.  If he goes into /home/user2 though, he should not see any files.  Possible?

---

### Post by Ek0nomik on 2007-07-11
This will get you started:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by jmazzarelli on 2007-07-11
> **viniosity said:**
> I've got a multi-user environment and I'd like a user to be able to see all his directories and I don't care if he can see the other directories either, but I'd like it so that if he enters another user's home folder that he can't see any of their files.  I was thinking this would be done with chmod but can't seem to find the right permissions?

For instance, if user1 is logged in he should be able to see everything in his /home/user1 directory.  If he goes into /home/user2 though, he should not see any files.  Possible?

Try changing your umask to something more strict, like 0077. Try adding the line:
```
umask 077
```
to your .bash_profile

Take care of the current files you have by doing something like:
```
chmod -r 700 ~
```

---

### Post by viniosity on 2007-07-11
> **jmazzarelli said:**
> Try changing your umask to something more strict, like 0077. Try adding the line:
```
umask 077
```
to your .bash_profile

Take care of the current files you have by doing something like:
```
chmod -r 700 ~
```

If I do that to a directory I can get in to my own and when I try to get into user2 it gives me a permission denied error.  That's better than nothing but is it possible to have it let me in but just not display any files?

Thanks!

---

### Post by jmazzarelli on 2007-07-11
actually, my last bit of advice was probably bad. Don't do ```
chmod -r 700 ~
```
You should do something more explicit like ```
chmod -r go-rwx ~
``` which will leave your current permissions intact for your user, but remove all permissions for the group and others.

---

### Post by jmazzarelli on 2007-07-11
> **viniosity said:**
> If I do that to a directory I can get in to my own and when I try to get into user2 it gives me a permission denied error.  That's better than nothing but is it possible to have it let me in but just not display any files?

Thanks!

For directories, you can set the 'x' bit and it means 'enter' instead of execute. But you would have to use a more complex command that recursively doing everything like in the previous example.

```
chmod go+x,go-rw ~
```
will let anyone *enter* your home directory, but they shouldn't see anything.

---

### Post by viniosity on 2007-07-11
Very cool! Thanks!

---

