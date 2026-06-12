---
title: "heres another issue...permissions"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by spin1078 on 2005-12-05
So i have the Java folder and its not installed.  its in my folder, which is (yes 2 d's) /home/bradd/Desktop/files/java2

the folder is fun to type too... jre1.5.0_05

since i unpacked it and made the dir in root i cant delete the folder.  ug this is so frustrating.

---

### Post by spin1078 on 2005-12-05
anyone tell me how to change the permissons.  i have been trying to use chown but i cant get the syntax right nor do i get what the options are saying.  i want to add my account to ownership to delete it.

---

### Post by AndyCooll on 2005-12-05
Open up a terminal, login as root (sudo -s).
Now type:

# Nautilus

This should open up the file browser as root. Navigate to the file and delete it.

:cool:

---

### Post by cwaldbieser on 2005-12-05
[QUOTE=spin1078]anyone tell me how to change the permissons.  i have been trying to use chown but i cant get the syntax right nor do i get what the options are saying.  i want to add my account to ownership to delete it.[/QUOTE]
```

$ sudo chown your-user folder-or-file

```

---

### Post by spin1078 on 2005-12-05
neither worked

root@ubuntu:~/files/java2# # Nautilus
root@ubuntu:~/files/java2# sudo -s
root@ubuntu:~/files/java2# Nautilus
bash: Nautilus: command not found
root@ubuntu:~/files/java2# Nautilus
bash: Nautilus: command not found
root@ubuntu:~/files/java2# #Nautilus
root@ubuntu:~/files/java2# # Nautilus
root@ubuntu:~/files/java2# $ sudo own
bash: $: command not found
root@ubuntu:~/files/java2# $ sudo chown bradd /bradd/home/files/java2/jre1.5.0_05
bash: $: command not found
root@ubuntu:~/files/java2#

---

### Post by spin1078 on 2005-12-05
aight i got that permissions thing.  whats up with the $?  I didnt need it
whats the point of it?  and I cant do the # Nautilus
or nautilus for that matter, with or without the #

---

### Post by kalos on 2005-12-05
There are different commands for permissions. 
**chown** is to change the owner.
```
kalos@ubuntu:~/tmp$ ls -l
total 4
-rw-r--r--  1 root root 6 2005-12-05 20:13 file

kalos@ubuntu:~/tmp$ sudo chown kalos:kalos file

kalos@ubuntu:~/tmp$ ls -l
total 4
-rw-r--r--  1 kalos kalos 6 2005-12-05 20:13 file

```

**chmod** is to change the permissions.
```
kalos@ubuntu:~/tmp$ ls -l
total 4
-rw-r--r--  1 kalos kalos 6 2005-12-05 20:13 file

kalos@ubuntu:~/tmp$ chmod 600 file

kalos@ubuntu:~/tmp$ ls -l
total 4
-rw-------  1 kalos kalos 6 2005-12-05 20:13 file

```

The difference is that if you are the owner of a file you can change the permissions.

-kalos

---

### Post by kalos on 2005-12-05
[QUOTE=spin1078]aight i got that permissions thing.  whats up with the $?  I didnt need it
whats the point of it?  and I cant do the # Nautilus
or nautilus for that matter, with or without the #[/QUOTE]

# indicates that you are at the command line as root.
$ means regular user

-kalos

---

### Post by Sutekh on 2005-12-05
[QUOTE=spin1078]neither worked
root@ubuntu:~/files/java2# $ sudo chown bradd /bradd/home/files/java2/jre1.5.0_05
bash: $: command not found
root@ubuntu:~/files/java2#[/QUOTE]

Careful with the order, should be 
/home/bradd/files/java2/jre1.5.0_05

To make it less painful to type crazy names such as jre1.5.0_05, you can use TAB to auto-complete words at the command line.  

Just start typing all that you can be bothered to and then press TAB, it will either complete the command if there is a unique match or offer possibilities if there are more than one.  If this happens type the next character and try again with TAB.  

It's extremely useful, especially for typing out full paths like /home/bradd/files/etc...


[QUOTE=spin1078] aight i got that permissions thing. whats up with the $? I didnt need it
whats the point of it? and I cant do the # Nautilus
or nautilus for that matter, with or without the # [/QUOTE]

That business with nautilus, was a caps issue.  Linux is caps sensitive, so *Nautilus* would not work, *nautilus* would.  Also kalos was correct about the $ and #.

There is a really good tutorial for coming to grips with the command line [Terminal for Beginners]("http://www.ubuntuforums.org/showthread.php?t=73885").  It might help you make more sense of it all.

---

### Post by Zimmer on 2005-12-05
And this site has some easy to understand tutorials on Ownership and permisions.
[http://www.tuxfiles.org/](http://www.tuxfiles.org/)

Zimm

---

### Post by kalos on 2005-12-05
[QUOTE=Sutekh]...
Just start typing all that you can be bothered to and then press TAB, it will either complete the command if there is a unique match or offer possibilities if there are more than one.  If this happens type the next character and try again with TAB.[/QUOTE]

Just be careful of doing that in a directory with lots of files. (like being in /etc/ and tab completing after only typing 'd'.) You will be warned about there being a lot of files, but if you are hasty (like I sometimes am), your screen will scroll (you can stop it by hitting ctrl-c).

But yeah, tab completion is fantastic.

-kalos

---

