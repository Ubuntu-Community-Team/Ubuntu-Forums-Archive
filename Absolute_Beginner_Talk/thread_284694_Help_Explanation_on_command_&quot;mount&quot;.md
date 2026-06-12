---
title: "Help Explanation on command &quot;mount&quot;"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by Abhi Kalyan on 2006-10-26
in the following lines:
sudo mount -t cifs //ipaddressofshare/sharename /mnt/share -o user=usernameofthatcomputer, pass=passwordofshare

Doubts:
1. what does "cifs" mean?
2. what does "-o", "-t" stand for?
2a. in "-o" is "o", alphabet "O" or number "zero"?

Thank you.

---

### Post by hearnden on 2006-10-26
Some of those parameters are logically grouped together.  The "-t cifs" specifies that the type ("-t") of file system being mounted is CIFS.  The "-o user=usernameofthatcomputer,pass=passwordofshare" specifies some extra mount options ("-o"), and I don't think there should be a space after that comma.

---

### Post by Abhi Kalyan on 2006-10-26
Thank you hearnden,
Will wait watch and try things out.
Thank you once again

---

### Post by CatKiller on 2006-10-26
```
man mount
```

---

### Post by Abhi Kalyan on 2006-10-26
Thank you cat killer!!
that was too dumb of me.
Doubts
1. How do i Kill/close a thread started by me?
2. How do i print(for hardcopy) a man file? Ex: man mount,?
Thank you once again

---

### Post by CatKiller on 2006-10-26
> **Abhi Kalyan said:**
> 1. How do i Kill/close a thread started by me?I don't think you can. The forum admins can, but they don't much since all the information is useful.
> 2. How do i print(for hardcopy) a man file? Ex: man mount,?
There are man pages mirrored on the Internet that you could print out with your browser. I'm sure there is some way to print them out directly, but I don't know what it is. I generally just have a terminal with the man page open, and a terminal I'm using for commands.
> Thank you once again

No worries.

---

### Post by Abhi Kalyan on 2006-10-26
Wow CatKiller, Just stumbled on this page, Hope it helps you as it has helped me, Here there are given various methods to print man pages!!!
Cheers
[http://www.brunolinux.com/10-General_Info/Printing_Man_Pages.html](http://www.brunolinux.com/10-General_Info/Printing_Man_Pages.html)

Thank you once again

---

### Post by TitusDalwards on 2006-10-26
in addition you can use ```
 mount --help
```

---

### Post by CatKiller on 2006-10-26
Excellent. Thanks.

---

### Post by Abhi Kalyan on 2006-10-27
Thank you TitusDalwards,
Great command - gives out a short summary , Very Handy
Thank you once again

---

### Post by Abhi Kalyan on 2006-10-27
Thank you CatKiller,
You pointed a question i jys happened to tumble upon an answer.

---

### Post by bodhi.zazen on 2006-10-27
Nice referance for mount: [How to mount](http://www.tuxfiles.org/linuxhelp/mounting.html)

And the man page: [man mount](http://www.die.net/doc/linux/man/man8/mount.8.html)

And since they go hand-in-hand fstab: [How to fstab](http://ubuntuforums.org/showthread.php?t=283131)

Google search man <command>. Bookmark or Print from Firefox.

---

### Post by Abhi Kalyan on 2006-10-27
Thank you bodhi.zazen,
Thats swell, Checking out those links just Now.

---

