---
title: "Problem with KDE and my home partition"
date: 2005-10-25
forum: Apple PPC Users
---

### Post by HarryW on 2005-10-25
Hi! 
I recently installed kubuntu on my laptop, however, I have some major problems with it. It all started when my friend helpt me with installing kubuntu over mandreava that I used to use. When he was fixing the partitions he accidently made my /home hard drive to /boot. It didn't went too well, so he thought that I should test reinstalling everything and lended me the latest kubuntu version. Everything works fine when I install I change the former /boot hard drive to home again and fix all the other. But when I log into my user windows start popping up saying that an error occured when KDE:s communication between the process were to start. 

"could not read network connection list.
/home/****/.DCOPserver_*****_0"

Later:
"The following installation problem was detected while trying to start KDE:
   No write access to $HOME directory (/home/****).
KDE is unable to start."

I hope someone can help with this problem.

---

### Post by daller on 2005-12-12
Since the thread is old, and the problem is pretty serious, I assume that you solved this, or abandoned ubuntu?

SHORT: Do you need help with anything?

---

### Post by coffeebaron on 2006-01-07
I now have the same problem. When I try to log in to kde, I get the error message:

No write access to "/home/***". KDE is unable to start.

I'm not sure what has gone wrong.

---

### Post by daller on 2006-01-08
[QUOTE=coffeebaron]I now have the same problem. When I try to log in to kde, I get the error message:

No write access to "/home/***". KDE is unable to start.

I'm not sure what has gone wrong.[/QUOTE]

Well, then play with the CLI!

Enter the home-folder:

```
cd /home
```

Then to check permissions:

```
ls -la
```

My output looks like this:

```
daniel@ubuntu:/home$ ls -la
totalt 16
drwxr-xr-x   4 root   root    4096 2005-12-17 00:22 .
drwxr-xr-x  22 root   root    4096 2005-11-26 16:53 ..
drwxr-xr-x  55 daniel daniel  4096 2006-01-08 13:00 daniel
drwxr-xr-x   2 ftp    nogroup 4096 2005-12-17 00:22 ftp
daniel@ubuntu:/home$
```

Find your user (In my case "daniel"), and check the ownership:

```
drwxr-xr-x  55 daniel daniel  4096 2006-01-08 13:00 daniel
```

In the above case, I own the directory, and it's in my "group"

What about you?

---

