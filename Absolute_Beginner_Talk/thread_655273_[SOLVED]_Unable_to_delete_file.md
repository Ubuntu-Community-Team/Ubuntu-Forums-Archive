---
title: "[SOLVED] Unable to delete file"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by manemannen on 2008-01-01
A similar question was raised in another thread but it could not be properly solved there so i'll give it a try here.

I have a file (located an a NAS mounted with samba). If I list the directory content I get the following:
[B]
>ls
06Disney[/B]

However, I know this is not the real name of the file. If I list the same directory through the ftp on the NAS I get the following:

**06DisneyÂ´s - Nalle Puh pa Aventyr (swedish).mpg**

The problem here seems to be the Â´ character. I have tried to delete with wildcards and to escape the funny character with no success.

How can I remove the file?? - and don't tell me I need Windows to do it....(since this was the solution in the other thread). I don't have Windows at all.

Please help.

---

### Post by chewearn on 2008-01-01
Can you use ftp to delete it then, since it can properly show the filename?

---

### Post by capink on 2008-01-01
The Solution to this is to delete the file by it's inode number:

1. Find the file inode number by typing:

```
ls -il /path/to/directory/containing/the/file
```

the inode number of the file should by the value on the left.


2. Delete the file:

```
find /path/to/directory/containing/the/file -inum inode/number -exec rm {} \;
```

replace inode/number with the proper value.


Edit: This only works on unix filesystems, so it might not work on windows filesystems.

Edit2: I tried this on fat32 and it seems to work. It seems that linux is assinging the files inode number even though the filesystem does not support it.

---

### Post by manemannen on 2008-01-01
Thanks for your suggestion capink. Unfortunately it doesn't seem to work for me.

I got the following response:
**rm: cannot remove `/home/mane/vault/movies/barn/06Disney': No such file or directory**

So the file was found using the inode number since it obviously translated it to the name (although truncated) but it was unable to delete.

---

### Post by capink on 2008-01-01
Well, try enclosing it within single quotes and see if it works:

```
find /path/to/directory/containing/the/file -inum inode/number -exec rm [COLOR="Red"]'{}'[/COLOR] \;
```

---

### Post by capink on 2008-01-01
also you can try:

```
find /path/to/directory/containing/the/file -inum inode/number -exec rm '{}' new-name \;
```


Or as a last resort move all other files form the same directory to somewhere else and delete the directory using rm -r command

---

### Post by zabien1970 on 2008-01-01
Are you sure that's the right path? whereis 06disney should output the correct path.
 Note: I'm currently at a friends house and not on my linux machine so the syntex may be a little off

---

### Post by manemannen on 2008-01-01
Nope :( I also tried **"find /path/to/directory/containing/the/file/ -inum 687 -delete"** but with the same result. I tried the solution suggested by AstalaVista and it worked! So the problem is solved but its a pity I couldn't understand how to do it properly.

Thanks for your help guys.

---

### Post by capink on 2008-01-01
> **zabien1970 said:**
> Are you sure that's the right path? whereis 06disney should output the correct path.
 Note: I'm currently at a friends house and not on my linux machine so the syntex may be a little off

The right path is the path of the directory containing the file. I assume you already replaced /path/to/directory/containing/the/file/ with the corrent path since your whrere able to get the inode number.

I don't know why it is not working. But you managed to solve your problem anyway.

---

