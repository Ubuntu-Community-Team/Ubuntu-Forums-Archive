---
title: "chmod questions?"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-02-16
I'm learning about how to use chmod by reading this tutorial
[http://www.linuxcommand.org/lts0070.php](http://www.linuxcommand.org/lts0070.php)
I understand pretty much everything but don't get the logic when you do 
```
ls -l
``` on some files and it says (rwxr-xr-x).

> 755
(rwx[COLOR="Red"]r[/COLOR]-xr-x) The file's owner may read, write, and execute the file. All others may read and execute the file. This setting is common for programs that are used by all users.

If ls -l would print it out like this
(-rwx-rwx-rwx) = 111 111 111 (excluding the digits)
Things would be so logical to me but as I explained 755 above ls -l would printout (rwx[COLOR="Red"]r[/COLOR]-[COLOR="Red"]xr[/COLOR]-x).  OK so owner has (Read Write eXecute) permission, group have (eXecute Read) permissions.

First question if owner has all permission what does the extra [COLOR="Red"]r[/COLOR] stand for?
Second question if group has (eXecute and Read) permission why do they not follow the logical structure like (-rwx-rwx-rwx) and instead reverse the order into (xr) when it logically should be (rx) or (r0x) to be precise :confused:
Third question the tutorial described Group and Others with the same properties.  Both had (Read Execute) permission but they are printed out different (....-xr-x) means the same thing but doesn't look the same why?

---

### Post by bodhi.zazen on 2007-02-16
LOL jingo811

I think you are reading the permissions a little off in terms of the extra r

See if this helps at all 

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by kebes on 2007-02-16
The permissions are three groups of three symbols, all squished together. The dash, "-", means "no" and is NOT a separator.

So for instance:

rwxr-xr-x

We break this (mentally) into three blocks:
rwx  r-x  r-x

The first block is the user (Read, Write, eXecute), the second block is the group (Read, no write (a dash), and eXecute), and the third block is world (Read, no write, and eXecute).


So something like:
rwx------

becomes:
rwx  ---  ---

Means that the user has Read, Write, eXecute, but the group has nothing (---) and the world also has no privileges (---).

The order is alwasy the same (Read, Write, eXecute), and the dash ("-") means "doesn't have this ability" whereas a symbol (r, w, x) means "has this ability."

---

### Post by highneko on 2007-02-16
I'll share my notes on chmod:
```
--- = 0
--x = 1
-w- = 2
-wx = 3
r-- = 4
r-x = 5
rw- = 6
rwx = 7
usage: chmod 644 /example/filename
```Edit: Correction made.

---

### Post by ardchoille42 on 2007-02-16
> **highneko said:**
> I'll share my notes on chmod:
```
 --- = 0     --x = 1
-w- = 2     r-x = 3
 r-- = 4     r-x = 5
rw- = 6     rwx = 7
users groups others all
usage: chmod 644 /example/filename
```

This should be

r=4    u=user
w=2   g=group
x=1    o=other

r = 4 = 4
r+w = 4+2 = 6
r+x = 4+1 = 5
r+w+x = 4+2+1 = 7

There is no 3, I mean you **can** chmod 300 a file but that is useless.. in order to have write or execute perms, you must have read perms also. So, the smallest usable number sequence you can have is 400 (r--------).

---

### Post by dracomordag on 2007-02-16
when moving all of my files over to Ubuntu from the NTFS partition, i moved them all into my personal folder. i then logged in as root and moved each folder to its owner's profile's desktop.

however, the permissions were not changed! so then i logged in as root, went to each persons folders which were still all set to only let me read/write/execute, right clicked, changed the owners, etc. and hit "apply this to all internal files and folders"


however, it did NOT apply it to every internal file and folder, and i certainly dont want to go through the 1000s of files and folders, right click each one, and change its permissions. how can i get the "apply to internal files and folders" to work?

---

### Post by kebes on 2007-02-16
> **dracomordag said:**
> however, it did NOT apply it to every internal file and folder, and i certainly dont want to go through the 1000s of files and folders, right click each one, and change its permissions. how can i get the "apply to internal files and folders" to work?

It's much easier to do this on the commandline (I don't know why the "apply to sub-folders" didn't work, mind you...). So in a terminal, if you're in a directory and want to change the permissions of folder "example" (and include all sub-folders), you would go:

chmod 744 -R example/


The 744 is an example, obviously (depends what you want...). Note that if you've moved the files as root, they will be owned by user "root" and you'll need to change this, too:

chown bob:bob -R example/

(where, as an example, I've switched ownership to user "bob")


Hope that helps.

---

### Post by highneko on 2007-02-16
> **ardchoille42 said:**
> This should be

r=4    u=user
w=2   g=group
x=1    o=other

r = 4 = 4
r+w = 4+2 = 6
r+x = 4+1 = 5
r+w+x = 4+2+1 = 7


My notes should be more complicated? I like my notes how they are but thanks for the suggestion.

---

### Post by kebes on 2007-02-16
> **highneko said:**
> My notes should be more complicated? I like my notes how they are but thanks for the suggestion.

He was pointing out a mistake in your original notes. You wrote:
r-x = 3
r-x = 5

But obviously you meant that top line to be:
-wx = 3

---

### Post by dracomordag on 2007-02-16
thanks!


as a side note, after i did that i decided i wanted others to do more than just list files, so i went logged in as root, and "apply to all interior files" option actually worked.


weird.

---

### Post by highneko on 2007-02-16
> **kebes said:**
> He was pointing out a mistake in your original notes. You wrote:
r-x = 3
r-x = 5

But obviously you meant that top line to be:
-wx = 3

Ah, interesting. I'll take another look at my notes again. Thanks for pointing this out in a way I understand(without using math). :lolflag:

---

### Post by kebes on 2007-02-16
> Here's an experiment. 

1) touch testfile (create a testfile)
2) chmod 000 testfile (chmod the testfile so no one has read, write or execute perms)
3) vim testfile (the owner of the file will still be able to write to it using <ESC> :wq! in vim even though it's chmoded 000)
4) rm testfile (the owner of the file will still be able to delete it even though it's chmoded 000)

This is why I never understood the need for three sets of settings (ie rwx rwx rwx). The owner of the file will be able to do anything with the file regardless of the owner premissions that are set. In my opinion, there should only be two sets of settings (ie rwx rwx), one for group and one for other so the owner of the file can set the file to be unreadable, read only or rwx by group and other.

I did your experiment. With a file set to 000, I cannot read it from any app (vim, nano, more, etc.). nano respects the permissions, and won't let me overwrite it, although vim apparently allows you to delete the old file and replace it with a new one. On the commandline, yes I can delete the file if I want, but it gives a warning that I'm about to delete a write-protected file.

The purpose of the first set of flags is to allow a user to protect files from themselves. There are times where you don't want to be able to easily modify or delete a file. (Or at least get a warning.) Even though the owner can still delete a 000 file, the warning is important, and moreover in a script those write-protected files can be bypassed. There may also be times when you don't want read permission on your own file. (Let's say you have a script scanning through a bunch of things but don't want some protected files to be read.)

The unix permissions exist to allow for maximum flexibility, which comes in handy sometimes, especially when you're automating things and you want to protect some files from your own actions.

---

### Post by ardchoille42 on 2007-02-16
> **kebes said:**
> I did your experiment. With a file set to 000, I cannot read it from any app (vim, nano, more, etc.). nano respects the permissions, and won't let me overwrite it, although vim apparently allows you to delete the old file and replace it with a new one. On the commandline, yes I can delete the file if I want, but it gives a warning that I'm about to delete a write-protected file.

The purpose of the first set of flags is to allow a user to protect files from themselves. There are times where you don't want to be able to easily modify or delete a file. (Or at least get a warning.) Even though the owner can still delete a 000 file, the warning is important, and moreover in a script those write-protected files can be bypassed. There may also be times when you don't want read permission on your own file. (Let's say you have a script scanning through a bunch of things but don't want some protected files to be read.)

The unix permissions exist to allow for maximum flexibility, which comes in handy sometimes, especially when you're automating things and you want to protect some files from your own actions.


Yeah, I made a mistake. Ignore me.

---

### Post by jingo811 on 2007-02-17
> The dash, "-", means "no" and is NOT a separator.
Now I understand.  There should be a separator though of some sort!  Makes things easier to read for ppl with eye astigmatism problems like me. :shock: (>_<) :shock: (>_x) :shock: *squinting eyes*

Is there a plugin program for terminal to make chmod format into (rwx-rwx-rwx) or something similar?
Or could one perpahs change this with some simple BASH script?

---

