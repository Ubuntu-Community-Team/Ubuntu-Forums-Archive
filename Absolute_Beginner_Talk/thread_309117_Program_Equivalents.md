---
title: "Program Equivalents?"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by Xylar Wasterend on 2006-11-29
Hello,
I'm a future Linux user who's yet to make the switch (will do so once I get an **ASUS A8JS-4S013P Intel Core 2 Duo** notebook).

In the meantime, I've been looking for Linux equivalents of what I use in Windows 2000. Found most, but not all.

Easy Hash and Tiny Text Crypter. With the first, drag a file to the program to see what its hash algorithm is; and with the second, encrypt / decrypt plain text. Not necessary, but handy.

Eraser. Securely deletes data.

Sysinternals Software (don't click link if afraid of visiting the Microsoft.com website...Sysinternals was recently bought out by Microsoft and all source code removed, which infuriated / horrified / disappointed many). My favorites. Process Explorer is priceless in that it shows everything there is to show about what's going on in a computer. As there are no screenshots of it at the site and it can't be run with an emulator, here are a few pictures of it.

1
2
3

I like knowing everything that goes on in a system (unfortunately, such a desire comes from high paranoia...). Ubuntu has the System Monitor, but not only could the usage graphs use more information, but there could be more, IMO.

Also from Sysinternals is the Autorun Monitor, which shows everything loaded at startup.

*Don't quote any of the links, as the pictures are temporary; I'll delete both later.

Thanks in advance.

Ubuntu is nice, btw. I've been playing with it and its brother Kubuntu using Live CDs. :)

FYI, there is a game coming out in 2007 that will run natively on Linux, called [Core Decision]("http://coredecision.highoctane.biz/index.php"), which is based off of Descent 1. I can't wait.

---

### Post by BoneKracker on 2006-11-29
I use shell commands to do these things, but it sounds like you are looking for graphical applications.  Most of these capabilities are built in to gnu/linux.  There are tens of thousands of linux apps, and I'm sure somebody will point you to graphical ones.  However, you might give the cli a chance, you might like it's speed and flexibility.  With tab-completion built-in to shells like bash (default on most gnu/linux systems), it's easy and so much faster than clicking through layer after layer in a hierarchy of folders and switching from one program to another to get things done. 

For example, to see a dynamic list of running processes and their priority, resource consumption, owner, etc., you simply type:
```
top
```

What's got network connections open:
```
netstat --inet -ap
```

What's my disk utilization, by partition:
```
df -hT
```

Has anybody been monkeying with file ownership?
```
sxid -n
```

Is somebody trying to login by guessing passwords?
```
faillog -a
```

To create/check a hash
```
md5sum
```
```
md5sum -c
```

To encrypt/decrypt, sign/verify a text file:
```
gpg -e <filename>
gpd -d <filename>
gpg -s <filename>
gpg --verify <sigfile> <filename>
```

And so on...

---

