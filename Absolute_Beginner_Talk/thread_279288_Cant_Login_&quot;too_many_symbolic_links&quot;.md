---
title: "Cant Login &quot;too many symbolic links&quot;"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by proctor on 2006-10-17
Hello

I cannot login to my edgy box, I get this error

> Your session lasted for 10 seconds...would you like to view xsessions.log

> Cannot execute /bin/bash - Too many symbolic links

Ive been running Edgy for a little bit and just did an update a day ago. After doing the update, I did not immidiately reboot but instead went about customing my bash prompt.

I did something to the effect of exportPS1 and my prompt went from 

> proctor@Desktop: to just a $ symbol
Im not sure if that had to do with it. But i am confused with this Symbolic links stuff. Ive been reading up on it & my rpoblem and I cant login. Something is wrong with the GDM or session :/

I tried gnome,failsafe gnome, and failsafe terminal. Not even failsafe terminal seems to work

Sorry if this is long & confusing, not sure how to explain it
Thanks

---

### Post by taurus on 2006-10-17
Try to boot it into recovery mode (from GRUB) and see what /bin/bash is pointing at!  If there is no link to/from it, then may modify your ~/.bashrc to see if that fixes the problem.

---

### Post by proctor on 2006-10-17
Alright, booted in recovery mode & it wouldnt make it to a full terminal. It stopped at a 'init.d' or something near full bootup and said Too many sybolic levels. Still not sure how to see what it is "pointing" at. So if you could guide me a bit more it'd be great

> session_child_run: Could not exec /etc/gdm/Xsession default


Im running off the Kororaa live cd, and managed to mount the linux partition. 
Not sure what to edit / do next

Appreciate the help.

---

### Post by taurus on 2006-10-17
If you mount it off a LiveCD on /mnt/ubuntu, then you can take a quick look at your bash in /mnt/ubuntu/bin/bash!

```
ls -la /mnt/ubuntu/bin/bash
```

---

### Post by proctor on 2006-10-17
to mount, what i did orginally > mount /media/sdb6

So, by doing what you said I got

> kororaa@xgl ~ $ ls -la /media/sdb6/bin/bash

lrwxrwxrwx  1 root root 7 Oct 16 21:25 /media/sdb6/bin/bash -> /bin/sh


*/bin/sh* is what it points at. Im trying to keep up but not sure where to go

---

### Post by taurus on 2006-10-17
That's interesting because on my Dapper, I have

```

lrwxrwxrwx 1 root root 4 2006-06-02 07:01 /bin/sh -> bash

```
May I suggest you change your shell in /media/sdb6/etc/passwd to something else like csh/tcsh.  Then, remove /bin/bash and reinstall it again with

```

sudo rm /bin/bash
sudo aptitude update
sudo aptitude install bash

```

---

### Post by proctor on 2006-10-17
also, Bash points to Sh & Sh points to Bash... :|

Im having trouble changing the shell, i looked at several tutorials and just went into passwd and changed the /bash to /csh  and that didnt seem to do anything

Youve done a lot. Ill try to manage for now

Thanks again

---

### Post by szf on 2006-10-17
Could this have anything to do with [Dash]("https://wiki.ubuntu.com/DashAsBinSh")?

---

### Post by Arndt on 2006-10-18
> **proctor said:**
> Hello

I cannot login to my edgy box, I get this error

Cannot execute /bin/bash - Too many symbolic links


This error message may mean that some file, maybe /bin/bash, is a symbolic link which points to itself, perhaps through other symbolic links:

```
$ ln -s a b
$ ln -s b a
$ cat a
cat: a: Too many levels of symbolic links
```

It rarely means that there are literally too many links. The check is there to prevent loops. I think that the maximum number is 32.

---

### Post by proctor on 2006-10-18
> Could this have anything to do with Dash?
Reply With Quote

mhm, actually the other day I had done something concerning Frostwire where I may have changed from Dash to Bash. Im not sure what I did exactly, I'll search the the forums for what command I used.

Pretty sure you got it right though. I forgot about that

---

### Post by steve.horsley on 2006-10-18
It's bash that's wrong. It should be a real file. sh links to bash.
> steve@StevesPC:~$ ls -l /bin/bash
-rwxr-xr-x 1 root root 664084 2006-04-21 23:51 /bin/bash
steve@StevesPC:~$ ls -l /bin/sh
lrwxrwxrwx 1 root root 4 2006-06-01 21:10 /bin/sh -> bash

If you have a live CD, you could mount your hard disk and replace the missing bash with the one from the live CD (delete the link to sh first). This would of course be safest done with an Ubuntu live CD, but you might get lucky with another distro live CD.

---

### Post by proctor on 2006-10-18
Im back on the box, just moved the bash from the live cd to my hdd and left the sh alone considering i didnt know how to unlink it.

So all is well it seems

Thanks for the help, i learned a bit more :P

---

### Post by taurus on 2006-10-18
Basically, /bin/sh should be linking to /bin/bash, not the other way around.

```

sudo ln -s /bin/bash /bin/sh

```

---

