---
title: "X-server backup"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2006-12-21
Question on many of the posts it says make a backup before I change something such as the Fstab or X-Server.  

How do I create a backup and once one is created, if I did make a mistake how would I get to the backup I created.


Hope this makes sense.

---

### Post by dbbolton on 2006-12-21
do this
```
sudo cp 'file' 'newfile'
```just adding '.bak' to the end of the original file.

if you need to use the backup, do 
```
sudo cp 'newfile' 'file'
```example might be: 

```
sudo cp '/etc/X11/xorg.conf' '/etc/X11/xbackup.conf'
```

hope this helps.

btw, i love clockwork orange

---

### Post by gentlemanmasher on 2006-12-21
Yes it does thanks for your help.

---

### Post by gentlemanmasher on 2006-12-22
Guess I did have one more question.  Why do you change xorg to xbackup?  That seems to be more than just adding .bak to the end of the file.

---

### Post by dbbolton on 2006-12-22
i guess you could do that, but i wasn't sure if you convert a .bak back to a .conf

i know that the data would still be there, but i just thought it might be safer to rename it, you know ?


i meant to either copy it to "xorg.conf.bak" OR "xbackup.conf" not "xbackup.conf.bak" - my instructions were a little unclear, sorry ;)

---

### Post by gentlemanmasher on 2006-12-22
if you don't mind  could you shoot me another example so I could see what one would look like.

Sorry to be petty but I seem to always mess up the spacing.

---

### Post by dbbolton on 2006-12-22
sure thing

```
sudo cp '/etc/X11/xorg.conf' '/etc/X11/xbackup.conf'
```
or
```
sudo cp '/etc/X11/xorg.conf' '/etc/X11/xorg.conf.bak'
```

---

### Post by gentlemanmasher on 2006-12-22
your the best thank you for explaining this for me.  Learning little by little.

---

