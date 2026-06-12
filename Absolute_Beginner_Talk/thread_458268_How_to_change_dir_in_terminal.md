---
title: "How to change dir in terminal"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by dptxp on 2007-05-29
I want to run dosemu from one directory.
How do I change dir in terminal ?
What commands ? Pl help.

---

### Post by LaRoza on 2007-05-29
cd = change directory
```

$ cd Desktop

```
will bring you to a sub-directory
```

$cd ..

```
will bring you up a directory

you can also use absolute paths, no matter where you are,

```

$pwd

```
will show you exactly where you are

-edit The above command move you around, if you want to move a file, use the "mv" command, which is also used for renaming
```

$mv /home/laroza/Desktop/myFile. /home/laroza

```
moves myFile. to my home directory

---

### Post by orange2k on 2007-05-29
The best place to start learning the linux commands is: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

It begins with the simple things like pwd and cd and goes to the other interesting stuff.
Quite interesting and helpful...:D

---

### Post by Falcorian on 2007-05-29
> **LaRoza said:**
> cd = change directory

Some other helpful stuff for cd:

. means the current directroy. So:

```
cd .
```

'Changes' to the current directory, which doesn't really do anything in this case.

.. is the directory one lower in the tree.

If you're in your /home/Falcorian directory, then:

```
cd ..
```

moves you to /home.



I found this guide:[Leanring the Shell](http://linuxcommand.org/learning_the_shell.php) helpful when I got started.

---

### Post by dptxp on 2007-05-29
Thanks everyone, fast job.

Yes, have to learn a few commands, going to buy a Linux guide.

Shall check the sites suggested first.

---

### Post by NickInOz on 2007-05-30
Thankyou also from me too. I am a 3 day old Ubuntu user and have been struggling with terminal. Many many thanks.

---

