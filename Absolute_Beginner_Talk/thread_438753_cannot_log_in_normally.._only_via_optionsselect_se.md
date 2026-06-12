---
title: "cannot log in normally.. only via options/select sessons"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-05-10
so i tried t lgo in as normal..

login name

pasword

nothing happend.. jsut a nice big coffee brown screen. I waited, I waited, nothing happend.

I turned the  machine off.

I tire dthis route 3 or 4 tiems. then I tried the good old  

F10-options-select sessions

1. last session
2. Default session
3. Gnome
4. Failsafe Gnome

all to no avail

5. Failsafe Terminal to hwich I got a small terminal window, typed in opera - got failed to open device... Then it opened.

so what the heck do I do to get things back to normal...??

robi

---

### Post by Martin on 2007-05-10
did it ever work? Or is this the first time on a newly installed system? If it used to work, what did you do/install/change last?

---

### Post by beanco on 2007-05-10
Martin,

It had been working fine.. I have not changed much recently.

Just tried to rectify some opera issues but the changes were to opera/tools/preferences, not to ubuntu per se.

really annoying because I need the machine at home ASAP 


robi

---

### Post by annda on 2007-05-10
first check if you have free space on your disk - this can cause problems. in the terminal type
```

df -h
```

---

### Post by beanco on 2007-05-10
being the fool that I am i managed to forget the simple code you suggestd....

so i just used mc and deleted several files.... i will reboot and see what happens out of curiousity but what I noticed when I closed opera was this msg:


(process 4785) Glib-*Gobject-Critical ***:gype. c:2215.....

what the heck is that?


and I wanted to delet a few files (films) to free up space and got this

cannot delete /home/robi/ blah blah blah   permission denied (13)

why is permission denied?

robi

---

### Post by beanco on 2007-05-10
so running df -h

i saw that there is 41% usage!!!! that ain't much!


robi

---

### Post by annda on 2007-05-10
no idea about the opera problem, but it might be related.

something is definitely wrong with permissions in your home directory. please use the

```
ls -l
```

command while you are in /home and see if you own your directory. if you do, cd to robi and see if the subdirectories have OK ownership/permissions.

**UPDATE:** better yet, use the -al switch to check hidden files too. nothing there should be owned by root.

more info here:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

and in case you need it:
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by beanco on 2007-05-10
noob alert, noob alert.

i ran ls -l and got a very long list...very long.

how do you go up and down in teh list to see what is what?

---

### Post by annda on 2007-05-10
if you can't scroll with the mouse, you can save the output of any command and then read it with nano or less:

```
ls -al > some_filename
```

```
nano some_filename
```

will display the file. ctrl+x to quit.

---

### Post by beanco on 2007-05-10
ok, ok, thanks

but will this help me get the damn comuter running?

robi

---

### Post by annda on 2007-05-10
> **beanco said:**
> ok, ok, thanks

but will this help me get the damn comuter running?

robi

i hope so. since i don't see your machine, i can't help you without getting some information. the best hypothesis now (based on your other post, too) is that there are some very important system files in your home directory (/home/robi) that are owned by root, when you try to boot normally into GNOME, they can't be accessed, because you as user don't have the permission.

please check it. you should have nothing like:
```

-rw-------  1 root   root        5087 2007-04-16 20:35 .dummy_filename

```

if you do, that is most probably the problem and it needs to be fixed.

i know it's tedious, but that way you will learn more and feel more comfortable with linux than if you just reinstalled.

---

### Post by beanco on 2007-05-10
OK, I know you are helping and I do not mind the tediousness, I know it is a great way to learn, I mena plugging through all this...

but if I want to get back to terminal I have to shut down the computer, reboot, hit  F10, options, fialsafe terminal ... time consuming...

but I will keep trying and I have decided to come back to this post of yours, to sort of start again.

[QUOTE]> **annda said:**
> no idea about the opera problem, but it might be related.

something is definitely wrong with permissions in your home directory. please use the

```
ls -l
```

command while you are in /home and see if you own your directory. if you do, cd to robi and see if the subdirectories have OK ownership/permissions.

**UPDATE:** better yet, use the -al switch to check hidden files too. nothing there should be owned by root.

so what should i do once I have run ls -l? of all the files that show up... which ones should I be looking for? any one without anr, w, or x in the second slot?

how do i know i am in home? i get robi@robi or sg like that when I go into terminall... 

how do I know I own my directory?


cd means change directory right?  


or if I do the ls -al option how do I know what is owned by root?


thanks and sorry for being so tiring!

robi

---

### Post by beanco on 2007-05-10
annda,

me again!

> **annda said:**
> 
```

-rw-------  1 root   root        5087 2007-04-16 20:35 .dummy_filename

```

if you do, that is most probably the problem and it needs to be fixed.

i know it's tedious, but that way you will learn more and feel more comfortable with linux than if you just reinstalled.


so i tried both ls -l and ls -al at robi@robi and there were many files

rw--- --blah blah blah robi root

or

rw----- blah, blah, blah  robi robi

but no root root....

what is next?

---

### Post by annda on 2007-05-10
```
pwd
```

will show you where you are at (print working directory).

when you are in your dir, go

```
ls -l**a**
```

'a' is extremely important, because those are system/configuration files and directories. everything should be like
```

drwx------  7 **robi robi**      4096 2007-03-23 23:31 .config
drwxr-xr-x  2 **robi robi**      4096 2007-05-10 21:21 Desktop
-rw-------  1 **robi robi**        26 2007-02-10 19:56 .dmrc
```

the letters drwx are not so important at the moment. if you spot anything saying root - or anything other than robi - post the line here.

---

### Post by annda on 2007-05-10
you can start with claiming everything including subdirs in your home dir:

```
sudo chown -R robi:robi
```

UPDATE: after that, check if there are any root permissions left with this search command:

```
ls -**R**al | grep root
```

if all is fine (no results), try rebooting.

---

### Post by beanco on 2007-05-10
yoru previous msg said sg about  posting anything withroot here... do you mean things that say robi root or just root?

because there are tons that say robi root, none that say root root...



> **annda said:**
> you can start with claiming everything including subdirs in your home dir:

```
sudo chown -R robi:robi
```

UPDATE: after that, check if there are any root permissions left with this search command:

```
ls -al | grep root
```

if all is fine (no results), try rebooting.

no quite sur what claming mans here but i will just go to terminal and run the command you suggest.

then run the second command and see what happens....

again thanks

robi

---

### Post by Martin on 2007-05-10
You might try this. I keep this link just in case I'll ever need it. Never used it though so I'm not sure if it works, [http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

---

### Post by beanco on 2007-05-11
Annda,

everytiem i type in 

```
sudo chown -R robi:robi
```

I get:

```
chown missing operand after 'robi:robi'
```

what;s this operand?

Martin,

thanks for the link I will try it later.

Robi

---

### Post by beanco on 2007-05-11
Martin

Before I do this


> **Martin said:**
> You might try this. I keep this link just in case I'll ever need it. Never used it though so I'm not sure if it works, [http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)


let me ask what exactly happens when i do it? Just what does setting back to defaults do?

I tried setting up a new user and loggins on but that did nto work.. the user was created, but I coudl not log normally. just this  F10, options method...


also anybody know what this means


ld.so:object ;libjvm.so' from LD_PRELOAD cannot be preloaded:ignored

and the same with  'libbawt'

robi

---

