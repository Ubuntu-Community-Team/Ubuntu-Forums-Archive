---
title: "Delete a file"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by salvo1 on 2006-04-22
```
salvo@toshiba:~$ cd Desktop/
salvo@toshiba:~/Desktop$ ls -l *.bin
-rw-r--r--  1 salvo salvo 2419676 2006-04-22 12:20 jmf-2_1_1e-linux-i586.bin
salvo@toshiba:~/Desktop$ sudo rm -f jmf-2_1_1e-linux-i586.bin
rm: impossibile rimuovere `jmf-2_1_1e-linux-i586.bin': Operation not permitted
salvo@toshiba:~/Desktop$
```

What's the matter?

---

### Post by louis_nichols on 2006-04-22
it is strange indeed. try

```
sudo rm -f <filename>
```

---

### Post by salvo1 on 2006-04-22
```
salvo@toshiba:~/Desktop$ sudo rm -f jmf-2_1_1e-linux-i586.bin
rm: impossibile rimuovere `jmf-2_1_1e-linux-i586.bin': Operation not permitted
salvo@toshiba:~/Desktop$

```

---

### Post by louis_nichols on 2006-04-22
wow! And you can add/delete/rename anything else at will inside this folder?

---

### Post by taurus on 2006-04-22
Since you are the owner of that file, try removing it without the sudo command then...
```

rm jmf-2_1_1e-linux-i586.bin

```

---

### Post by salvo1 on 2006-04-22
[QUOTE=louis_nichols]wow! And you can add/delete/rename anything else at will inside this folder?[/QUOTE]

Of course, it's my desktop!

[QUOTE=taurus] 	Since you are the owner of that file, try removing it without the sudo command then...[/QUOTE]

```
salvo@toshiba:~/Desktop$ rm jmf-2_1_1e-linux-i586.bin
rm: impossibile rimuovere `jmf-2_1_1e-linux-i586.bin': Operation not permitted
salvo@toshiba:~/Desktop$

```

---

### Post by louis_nichols on 2006-04-22
[QUOTE=salvo1]Of course, it's my desktop!
[/QUOTE]
easy, man! I had to ask, seeing how strange all this is. I was thinking it might be a read-only mount thing.

Sorry, but my knowledge is limited and I really don't know what else you might try. Perhaps boot a livecd, mount the partition rw there and delete it that way.

---

### Post by zaba on 2006-04-23
Actually, Louis, you might be on the right track. For example, I have one folder on my desktop with a big ol' lock on it right now (since I have been too lazy to do what I am about to suggest to salvo).

Salvo, try: 

```
sudo chown salvo jmf-2_1_1e-linux-i586.bin
``` 
then, try:

```
rm jmf-2_1_1e-linux-i586.bin
``` 
If that doesn't work, please provide the errors. If chown doesn't work, it might be that the file is in use.

---

### Post by louis_nichols on 2006-04-23
[QUOTE=zaba]Actually, Louis, you might be on the right track. For example, I have one folder on my desktop with a big ol' lock on it right now (since I have been too lazy to do what I am about to suggest to salvo).[/QUOTE]

I was thinking of somkind of lock, but I haven't heard of such a thing under linux. are there any?

[QUOTE=zaba]Salvo, try: 

```
sudo chown salvo jmf-2_1_1e-linux-i586.bin
``` [/QUOTE]

*ls* shows the file is already owned by him. think it migt some kind of fs error?
[QUOTE=zaba]If that doesn't work, please provide the errors. If chown doesn't work, it might be that the file is in use.[/QUOTE]

To my knowledge, linux doesn't lock files that are in use, so one can actually delete them at will (the entire os, if needed). Is my knowledge wrong?

---

### Post by salvo1 on 2006-04-23
```
salvo@toshiba:~/Desktop$ sudo chown salvo jmf-2_1_1e-linux-i586.bin
Password:
salvo@toshiba:~/Desktop$ rm jmf-2_1_1e-linux-i586.bin
rm: impossibile rimuovere `jmf-2_1_1e-linux-i586.bin': Operation not permitted
salvo@toshiba:~/Desktop$ rm -f jmf-2_1_1e-linux-i586.bin
rm: impossibile rimuovere `jmf-2_1_1e-linux-i586.bin': Operation not permitted
salvo@toshiba:~/Desktop$

```

I try these commands after reboot..

---

### Post by salvo1 on 2006-04-23
[QUOTE=louis_nichols]I was thinking of somkind of lock, but I haven't heard of such a thing under linux. are there any?



*ls* shows the file is already owned by him. think it migt some kind of fs error?


To my knowledge, linux doesn't lock files that are in use, so one can actually delete them at will (the entire os, if needed). Is my knowledge wrong?[/QUOTE]

I agree about all.

---

### Post by salvo1 on 2006-04-23
[QUOTE=zaba]If chown doesn't work, it might be that the file is in use.[/QUOTE]

```
salvo@toshiba:~/Desktop$ lsof jmf-2_1_1e-linux-i586.bin
lsof: WARNING: can't stat() ext3 file system /dev/.static/dev
      Output information may be incomplete.
salvo@toshiba:~/Desktop$ sudo lsof jmf-2_1_1e-linux-i586.bin
salvo@toshiba:~/Desktop$ rm -f jmf-2_1_1e-linux-i586.bin
rm: impossibile rimuovere `jmf-2_1_1e-linux-i586.bin': Operation not permitted
salvo@toshiba:~/Desktop$ sudo rm -f jmf-2_1_1e-linux-i586.bin
rm: impossibile rimuovere `jmf-2_1_1e-linux-i586.bin': Operation not permitted
salvo@toshiba:~/Desktop$
```

---

### Post by gr0kzer0 on 2006-04-23
Are you already looking at/using this file in another login session? That would stop you being able to remove it. This has happened to me.

---

### Post by zaba on 2006-04-23
From [http://www.tldp.org/LDP/abs/html/basic.html:](http://www.tldp.org/LDP/abs/html/basic.html:)

> chattr

    Change file attributes. This is analogous to chmod above, but with different options and a different invocation syntax, and it works only on an ext2 filesystem.

    One particularly interesting chattr option is i. A chattr +i filename marks the file as immutable. The file cannot be modified, linked to, or deleted , not even by root. This file attribute can be set or removed only by root. In a similar fashion, the a option marks the file as append only.


I hadn't heard about this command before, but it sounds like it might be what the problem is. So, what happens if you sudo chattr -i (and -R, if it's a folder), then try and rm it?

---

### Post by salvo1 on 2006-04-27
[QUOTE=zaba]From [http://www.tldp.org/LDP/abs/html/basic.html:](http://www.tldp.org/LDP/abs/html/basic.html:)



I hadn't heard about this command before, but it sounds like it might be what the problem is. So, what happens if you sudo chattr -i (and -R, if it's a folder), then try and rm it?[/QUOTE]

```
salvo@toshiba:~/Desktop$ sudo chattr -i jmf-2_1_1e-linux-i586.bin
salvo@toshiba:~/Desktop$ sudo rm -f jmf-2_1_1e-linux-i586.bin
rm: impossibile rimuovere `jmf-2_1_1e-linux-i586.bin': Operation not permitted
salvo@toshiba:~/Desktop$

```

Maybe I need to check the disk? How?

---

### Post by zaba on 2006-04-30
Okay, I'm grasping at straws, but what happens if you do any of the following:

1. now that you have chattr -i, what happens if you try to rm without sudo? ditto with rm -f?

2. do you get any kind of error dialogue if you drag the file to the trash/wastebasket through a gui? If so, what? If not, what happens if you try to empty the wastebasket?

3. Right-click on the icon and choose properties. Can we get a screen-shot of what the permissions tab says?

4. If you have it set-up, have you tried logging in as root and trying to remove the file via the gui?

As far as checking the disk, you can try fsck -f or e2fsck -f, but that seems like an unlikely problem to me.

---

### Post by Rinzwind on 2006-04-30
If you want to know if someone is using the file do

**/sbin/fuser -u jmf-2_1_1e-linux-i586.bin**

**-ku** kills the user that's using it.

---

### Post by Rinzwind on 2006-04-30
After some googleing some extra info from linux-kernel-archives:

> Assuming this is an ext2 filesystem, if root tries to unlink afile, Linux returns EPERM (Operation not permitted) only in thefollowing cases:
1. The directory in which these files are is append-only.
2. The directory in which these files are is immutable.

But this is linux specific; not Ubuntu.


So also check the rights of the directory.


Btw: deleting a file is an operation on a DIRECTORY. Not on the file itself!! (you remove the entry
from the directory pointing to the file)

---

### Post by zaba on 2006-04-30
[QUOTE=Rinzwind]After some googleing some extra info from linux-kernel-archives:



But this is linux specific; not Ubuntu.


So also check the rights of the directory.[/QUOTE]

I would actually say that is "linux-general, not Ubuntu-specific", but that's just me being pedantic.

As for the rights of the directory, that's one of the reasons I wanted a screenshot of the permissions tab... it would show us the read/write/execute properties for the file. It will also show whether there is a sticky tab set, etc.

---

### Post by Rinzwind on 2006-04-30
[QUOTE=zaba]I would actually say that is "linux-general, not Ubuntu-specific", but that's just me being pedantic.

As for the rights of the directory, that's one of the reasons I wanted a screenshot of the permissions tab... it would show us the read/write/execute properties for the file. It will also show whether there is a sticky tab set, etc.[/QUOTE]

You are correct :) :)

I copied this as an example:
> # mkdir aa
# touch aa/bb
# rm aa/bb
# chattr +a aa
# touch aa/aa
# rm aa/aa
rm: cannot remove `aa/aa': Operation not permitted
# rm -f aa/aa
rm: cannot remove `aa/aa': Operation not permitted
# echo asdf > aa/aa
# rm aa/aa
rm: cannot remove `aa/aa': Operation not permitted
# cat aa/aa
asdf
# touch aa/bb
# rm aa/aa aa/bb
rm: cannot remove `aa/aa': Operation not permitted
rm: cannot remove `aa/bb': Operation not permitted
# 

chattr changes the atributes.
touch changes the file's date and time (basically changes the file).
You can see touch always works, But rm doesn't if the file is set with 'chattr +a'

This should mean it's the directory .Desktop that's bugging you.

---

### Post by louis_nichols on 2006-04-30
wow, guys! that's a lot of digging. I was pretty puzzled myself, but really didn't know where to start looking for the answer. it's good to know where to find it.

still... what does the man do to delete the file? LOL

---

### Post by salvo1 on 2006-05-03
[QUOTE=zaba]1. now that you have chattr -i, what happens if you try to rm without sudo? ditto with rm -f?
[/QUOTE]

```
salvo@toshiba:~/Desktop$ rm -f jmf-2_1_1e-linux-i586.bin
rm: impossibile rimuovere `jmf-2_1_1e-linux-i586.bin': Operation not permitted
salvo@toshiba:~/Desktop$

```

[QUOTE=zaba]
2. do you get any kind of error dialogue if you drag the file to the trash/wastebasket through a gui? If so, what? If not, what happens if you try to empty the wastebasket?
[/QUOTE]

```
salvo@toshiba:~/Desktop$ mv jmf-2_1_1e-linux-i586.bin /dati/.Trash-salvo/
mv: impossibile rimuovere `jmf-2_1_1e-linux-i586.bin': Operation not permitted
salvo@toshiba:~/Desktop$

```

...and impossible to move the file using GUI. Error: Impossible to move to trash.

> 
3. Right-click on the icon and choose properties. Can we get a screen-shot of what the permissions tab says?


see attachment..
4. If you have it set-up, have you tried logging in as root and trying to remove the file via the gui?

> 
As far as checking the disk, you can try fsck -f or e2fsck -f, but that seems like an unlikely problem to me.

Do I need to unmount all partitions? How? Maybe..
```

sudo umount /
sudo umount /second_partition
sudo umount /third_partition
fsck -f

```

but...

```

a$ sudo umount /
umount: /: device occupato (english: device in use)

```

---

### Post by salvo1 on 2006-05-03
[QUOTE=Rinzwind]If you want to know if someone is using the file do

**/sbin/fuser -u jmf-2_1_1e-linux-i586.bin**

**-ku** kills the user that's using it.[/QUOTE]

```
salvo@toshiba:~/Desktop$ fuser -u jmf-2_1_1e-linux-i586.bin
salvo@toshiba:~/Desktop$


```

PS: I upgrade (upgraded?) to Dapper

---

### Post by salvo1 on 2006-05-03
[QUOTE=louis_nichols]wow, guys! that's a lot of digging. I was pretty puzzled myself, but really didn't know where to start looking for the answer. it's good to know where to find it.
[/QUOTE]

Usually in Windows i did:
1. Prompt MS-DOS
2. ctrl+alt+canc
3. kill Explorer
4. del /f file_name_in_use
5. run explorer

> 
still... what does the man do to delete the file? LOL

I'm thinking to 2 solutions:
1. run Ubuntu live from CD and try to delete the file;
2. to pray

---

### Post by zaba on 2006-05-03
[QUOTE=salvo1]I'm thinking to 2 solutions:
1. run Ubuntu live from CD and try to delete the file;
2. to pray[/QUOTE]


That's about what I would say, too. When you run the Live CD, you can then umount the partitions to do the fsck, as well.

Hope that solves it... Otherwise I've pretty much run out of ideas!

---

### Post by louis_nichols on 2006-05-03
[QUOTE=zaba]That's about what I would say, too. When you run the Live CD, you can then umount the partitions to do the fsck, as well.

Hope that solves it... Otherwise I've pretty much run out of ideas![/QUOTE]

Somehow, I don't think that would work. Whatever is locking the file, it's in the filesystem, so wherever mounted, the effect would be the same.

Unless... you use a r-w driver for windows, which doesn't take into account any file permissions.

---

### Post by Rinzwind on 2006-05-03
You forgot to check 1 thing!

Go back up one directory and do an
ls -la |more

find the line that has your file (desktop was it?) and post it here :)

it should be:
**drwxr-xr-x  2 rinzwind rinzwind 4096 2006-04-30 21:23 Desktop**

edit: the part in my last post about the chattr shows it's NOT the file. It's the directory.
Like I said: a remove is a mutation on a direcory (basically you remove a reference to the file so the directory knows the file is not part of the directory).

Something else!
Can you add and remove another file from there!? Don't think it's been asked yet (I breefly scanned the post for a reference to it)

---

### Post by salvo1 on 2006-05-11
solved using ```
debugfs
```

```
debugfs
open -w /dev/...
cd /....
rm *.bin
```

---

### Post by louis_nichols on 2006-05-11
so it was indeed a bug of the filesystem? did you consider filing a bug report? well... you would need to be able to replicate this... just an idea.

---

### Post by Schmots on 2006-05-11
lvm?  or normal file systems?

I belive you need a root password for init 1.. so 
sudo passwd root
*
*
sudo init 1
stuff..

rm -rf /path to your file


then you can reboot, or 
init 2


which brings me to another quesiton.. why use init2 as default.. wouldn't init5 make more sense for a gui multiuser enviorment?

---

### Post by louis_nichols on 2006-05-11
[QUOTE=Schmots]lvm?  or normal file systems?

I belive you need a root password for init 1.. so 
sudo passwd root
*
*
sudo init 1
stuff..

rm -rf /path to your file

then you can reboot, or 
init 2


which brings me to another quesiton.. why use init2 as default.. wouldn't init5 make more sense for a gui multiuser enviorment?[/QUOTE]


the OP had tried all of that. not necessarily going to init1, but removing as root, which is the same, and it didn't work.

the init issue, it's a debian thing, to my knowledge. myself, I don't see the sense of having 5 actual runlevels for a regular desktop pc user, who might not even be able to use the recovery console mode, therefore only needing one runlevel in fact (well, 3 counting restart and shutdown).

---

