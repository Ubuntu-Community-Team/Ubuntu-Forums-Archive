---
title: "confused about onwership and permissions"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-05-18
hi everybody,

again, having had many problems of lat ei turned here and got lots of great help.


one thing that keeps confusing me is this whole ownership and permissions thing

when I ran

```
robi@robi:~$ ls -al
```

I got this (just a partial list)

```

drwxrwxrwx  2 robi robi     4096 2007-01-01 18:53 000
-rwxrwxrwx  1 robi robi  5323870 2006-05-22 22:05 AbiwordSetup.exe
-rwxrwxrwx  1 robi root  2656058 2007-01-22 17:53 Af_Am_Broch.pdf
-rwxrwxrwx  1 robi robi     6455 2007-01-02 19:32 a.odt
```

what is the 'd' in the first line?

why are some lines user robi group robi

and some user robi group root?

is that normal or not? hsould I be worried or not?

Earlier today it was robi root all the way through but then in systems/administration/users and groups i changed thigns... i thought i got rid of the user robi in group root thing but apparently i was unsucessful...


i will read through the following again, and see if I can come to better grips with things.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)


thanks

robi

---

### Post by Najand on 2007-05-18
d is directory.
see there are three sets of rwx. The first rwx shows the read/write/execute permissions for the user who owns it (The owner), The second rwx shows the permissions for other people in the group which owns the file. And the last one is the permission for other people.
For more information about permissions see The Linux Documentation Project (tldp):
[http://tldp.org/LDP/intro-linux/html/sect_03_04.html#AEN3898](http://tldp.org/LDP/intro-linux/html/sect_03_04.html#AEN3898)

---

### Post by Cypher on 2007-05-18
The 'd' in the listing means Directory. You will see a 'l' for symbolic links, and just a "-" for regular files. 

The pieces that follow are [R]ead/[W]rite/E[x]ecute permission for Owner, Group and World respectively.

On most personal systems, User = Group, i.e., your userame is used to create a group that you belong to. On ubuntu you will also belong to other groups like Admin or something, but the group named after your name is the primary group.

Other multi-user systems, you might all belong to a group that isn't related to your username.

The reason for the mixed robi/robi and robi/root files is because you're playing around with them.

I would suggest that you
```

sudo chown robi.robi <file>

```
whichever <file> you want to wholely own. You can replace <file> with "*" to affect all files/directory under the current directory..

---

### Post by FuturePast on 2007-05-18
Well, the d means directory.

As for the group, that's assigned at the time you created the file, so any changes you make
to your users group will not affect that.
You can use chgrp to change the group to whatever you want.

---

### Post by Najand on 2007-05-18
It won't make any differnce to have them as "root" or "robi" as far as all people have all read/write/execute permission to those files.

---

### Post by Najand on 2007-05-18
> **Cypher said:**
> 
I would suggest that you
```

sudo chown robi.robi <file>

```
whichever <file> you want to wholely own. You can replace <file> with "*" to affect all files/directory under the current directory..

I believe you mean:
```

sudo chown robi:robi <file>

```
Right?

---

### Post by Cypher on 2007-05-18
Both syntax's work..

---

### Post by beanco on 2007-05-18
ok, thanks for all the info....

i guess i could just leave things as they are and all will be fine.

Najand... is this at all related to the other thread you are helping me on about th ependrive and merissions there?

thanks

robi

---

### Post by Najand on 2007-05-18
No, it is not. It is about file permissions, etc. however mount permission is something else.

---

