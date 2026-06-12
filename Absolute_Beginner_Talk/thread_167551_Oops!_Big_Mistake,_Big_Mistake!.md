---
title: "Oops! Big Mistake, Big Mistake!"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-04-28
I was reading this thread on samba,  [http://ubuntuforums.org/showthread.php?t=91066]("http://ubuntuforums.org/showthread.php?t=91066"), and on the third post, at the part where it says: " and you should change the write/read privlegies to that folder by running the command:
sudo chmod 777 /multimeda", I accidentally typed in "sudo chmod 777 /" instead of "sudo chmod 777 /multimedia"
Does this mean I just gave my entire filesystem read/write capabilities? How do I undo that?!!

---

### Post by joshrobinson on 2006-04-28
[QUOTE=erik1397]I was reading this thread on samba,  [http://ubuntuforums.org/showthread.php?t=91066]("http://ubuntuforums.org/showthread.php?t=91066"), and on the third post, at the part where it says: " and you should change the write/read privlegies to that folder by running the command:
sudo chmod 777 /multimeda", I accidentally typed in "sudo chmod 777 /" instead of "sudo chmod 777 /multimedia"
Does this mean I just gave my entire filesystem read/write capabilities? How do I undo that?!![/QUOTE]

```
ls -al /
```

to see if it atually changed them.. it should say root in front of the folders

---

### Post by user1397 on 2006-04-28
I guess they don't change that easily because root is in front of the folders.
thanks for the reply

---

### Post by joshrobinson on 2006-04-28
[QUOTE=erik1397]I guess they don't change that easily because root is in front of the folders.
thanks for the reply[/QUOTE]

- chmod 755 myfile : rwxr-xr-x, all rights to the owner, other people only read and execute;
- chmod 644 myfile : rw-r--r--, owner can read and write, other people only read;
- chmod 777 myfile : can be considered bad practice in some cases, full permissions to everybody.

you can always do a chmod 755 / just in case

becuase the files should still be OWNED by root

whats it say when you do

ls -ld /

does it say drwxr-xr-x at the beginning?

---

### Post by transactionlogfiller on 2006-04-28
It will only chmod the top directory level unless you use -r (recursive). Most of the the things under / are directories and need the execute permission anyway. 751 looks right for all execpt the symlinks, which are 777.

---

### Post by user1397 on 2006-04-28
[quote=joshrobinson]- chmod 755 myfile : rwxr-xr-x, all rights to the owner, other people only read and execute;
- chmod 644 myfile : rw-r--r--, owner can read and write, other people only read;
- chmod 777 myfile : can be considered bad practice in some cases, full permissions to everybody.

you can always do a chmod 755 / just in case

becuase the files should still be OWNED by root

whats it say when you do

ls -ld /

does it say drwxr-xr-x at the beginning?[/quote] No it says  drwxrwxrwx.
I did that sudo chmod 755 / and then it said drwxr-xr-x

---

