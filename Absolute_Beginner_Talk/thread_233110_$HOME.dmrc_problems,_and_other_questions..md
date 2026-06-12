---
title: "$HOME/.dmrc problems, and other questions."
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by Lord Canti on 2006-08-09
Ok. First things first, I'm using 6.06 on a thirty gig drive. I checked free space and I'm using 25% of my drive. My $HOME/.dmrc file is being ignored. It wants 644 permisions, and owned by user. I've searched the forums for two days and ran code for this problem but it has not helped. Then after that error message comes up and I say ok it continues to load, but then I get a message saying my login time was less than ten seconds. It said that it might be caused by a bad installation, or low disk space. I have reinstalled and checked disk space (25%). [/main problem]

Other Questions:
Will I be able to access my other drives (one with no os, one with windows), and will I be able to run preinstalled programs (on the other drives) with something like Wine. If so, then what do you recommend?

Edit: I like the coffee theme with the posts.
Edit2: It's Ubuntu. I never told what I was in. :lol:
Edit3: I'm using 7% of my drive.

---

### Post by Dr. Nick on 2006-08-09
Try this and see if it clears your dmrc problem

sudo chmod 750 /home/<username>/.dmrc

---

### Post by Lord Canti on 2006-08-09
Thank you. But I get the responce "file does not exist" or "file not found" Also I think my /HOME file does not exist.
I can't log in because GNOME tells me that it does not have permision to do anythng.

---

### Post by Dr. Nick on 2006-08-09
weird, have you booted into recovery mode from grub?

That will log you in as root and you can browse the filesystem, once their try cd /home/yourusername and see if it exists

---

### Post by Lord Canti on 2006-08-09
I will. What is CD? (Other than compact disk :))

---

### Post by scxtt on 2006-08-09
you can think of cd as "change directory" ...

and my ~/.dmrc has the following stats:
```
:> ll ~/.dmrc
-rw------- 1 scxtt scxtt 26 2006-08-06 20:53 /home/scxtt/.dmrc
```
```
:> cat ~/.dmrc
[Desktop]
Session=default
```looks like you should boot into recovery mode and see if your user's home directory even exists ...

---

### Post by Lord Canti on 2006-08-09
Guess what. It doesn't. Also would you know why GNOME would have the rights to go anything on login?

---

### Post by scxtt on 2006-08-09
you'll have to be more specific about that last sentence ...

are you sure the user even exists? [ do a **cat /etc/passwd | grep $USER** from recovery mode to see ($USER is the name of the account you created, if it was created) ] ...

---

### Post by Lord Canti on 2006-08-09
I'll edit this with an explanation. I can log in as that user but I'll look any way.

EDIT: I meant wouldn't. Later on that.
cat /etc/passwd|grep daemon
returned
```
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
haldaemon:x:108:108 Hardware abstration layer,,,:/var/run/hal:/bin/false
```
Now want I meant was I can't stay loged in because GNOME can't do something and it logs me off in <10 seconds.

---

### Post by Lord Canti on 2006-08-09
cat /etc/passwd|grep daemon
returned
```

daemon:x:1:1:daemon:/usr/sbin:/bin/sh
haldaemon:x:108:108 Hardware abstration layer,,,:/var/run/hal:/bin/false
```

This is in case the folks here don't look for edits.

---

### Post by Dr. Nick on 2006-08-09
Thier may be other issuses with gnome aswell, have you tried a failsafe gnome session?

Also linux is case sensitive with directories, if you typed /HOME it will not work, must be /home

---

### Post by Lord Canti on 2006-08-09
I think it was lower case. I have tried a failsafe, and get the same error.

---

### Post by scxtt on 2006-08-09
that is a BAD username ... seems those are created no matter what -- i have those exact entries in my /etc/passwd and my ONLY username is scxtt ...

i'd advise booting into recovery mode and doing an **adduser** using a username that doesn't already exist in /etc/passwd -- like LordCanti or something ...

---

### Post by Lord Canti on 2006-08-09
Can you give me the steps?

---

### Post by Dr. Nick on 2006-08-09
reboot the entire system and on the grub screen their is a "recovery mode" should be 2nd in the list.

That will boot you straight into a command line with a root login

Then run 

adduser somename

then you should be able to login with that name, it may need a password, in that case i think its

passwd [I]username from above

[/I]Then you should be able to login with that user, you wont have sudo by default on the new account  though, not sure how to fix that

---

### Post by scxtt on 2006-08-09
> **Lord Canti said:**
> Can you give me the steps?it's not hard, i'd just do a **man useradd** and look up which flags to use ... like -u for uid, -g for group and how to specify your home directory and shell ... it isn't hard, and the man page for useradd is good (i've used it at least 3 times @ work to create users for no-GUI boxes, just don't have it memorized) ...

[center]-------------------------------------------------- EDIT --------------------------------------------------[/center]

here's what i'd do:

$recovery_prompt:> useradd -u 1000 -g users -c "Lord Canti account" -d /home/LordCanti -s /bin/bash LordCanti

then

$recovery_prompt:> passwd LordCanti

so you can actually login ...

and you'll most likely want to add yourself to certain groups so you can sudo by editing /etc/group, as such:
```
:> cat /etc/group | grep scxtt
adm:x:4:scxtt
dialout:x:20:cupsys,scxtt
cdrom:x:24:haldaemon,scxtt
floppy:x:25:haldaemon,scxtt
audio:x:29:scxtt
dip:x:30:scxtt
video:x:44:scxtt
plugdev:x:46:haldaemon,scxtt
lpadmin:x:106:scxtt
scanner:x:110:cupsys,scxtt
scxtt:x:1000:
admin:x:111:scxtt
```so add your username to any place you see **scxtt** ...

---

### Post by Lord Canti on 2006-08-09
I have to leave the interweb (OH MY GOD!) so I'll post what happens tomorrow.

---

### Post by Lord Canti on 2006-08-10
OH MY GOD! THANK YOU! By using a combination of what both of you told me, and some guess work, I got my new login working. I'm even posting from Ubuntu now. I'm going to go see if I can get my drives to mount. I have to learn everything because my friend can't.

---

