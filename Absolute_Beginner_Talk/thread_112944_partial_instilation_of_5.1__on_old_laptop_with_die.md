---
title: "partial instilation of 5.1  on old laptop with dieing cd drive"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by croachus on 2006-01-05
I have a dell inspiron 7000 with a pentium 2 (233) 256 ram and 4G HD.
My problam is that my cd rom is allmost dead.
I have however managed after repeted attempts to install 5.1 with the 2.6 12-9 386 kernal.
I did not however install the remaining packages to hard disk
Now It wanted to reboot and when it does it first boots Grub then ubuntu and the "ok" checklist then goes to a black screen saying login: so I did and now all i get is "carl@ubuntucroachus:*$ _ " so what do I do now to get a desktop?
How can I install the rest and get a useable desktop?

---

### Post by Jimmey on 2006-01-05
Ehrm, is it part, or full way through the install? 
If full, try typing "startx".

---

### Post by croachus on 2006-01-05
I believe it was a full install except for the "remaining packages" I tried "startx" and all i get is
-bash: startx: command not found

---

### Post by az on 2006-01-05
Boot into recovery mode and edit your /etc/apt/sources.list

Comment out the cdrom line and uncomment the other lines which contain the word "main"

Try running 
apt-get update

and then apt-get install ubuntu-desktop

if you get any error run

apt-get -f install


You are connected to the net, aren't you?

---

### Post by croachus on 2006-01-05
no net I'm affraid and no knowledge of the command line
I'll attempt your sugestions. (the best I can).   and report back later for now I'm out of time........   thanks

---

### Post by az on 2006-01-05
Never mind.  It won't work.  What I describe is a way to get the remaining packages you need from the internet instead of from your local cd.

---

