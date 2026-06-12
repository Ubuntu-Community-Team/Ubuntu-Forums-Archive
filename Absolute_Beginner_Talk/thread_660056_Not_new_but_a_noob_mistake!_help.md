---
title: "Not new but a noob mistake! help?"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by liberum on 2008-01-06
Okay, doom on me I made a "small" blunder while changing the rights to some files...

and yes i know im not supposed to use 777, but you can still rub my nose in it if you like :)

i went to change some files before moving them to a server and i typed

"chmod 777 /*"

forgetting that this wasnt all the files in the current directory but rather root....

well now that all my root files are naked... what should the important ones be?  i would like to put things back the way they were,  any help is appreciated.

could have been worse, could have type chmod -R 777 /*   !!!!!!

thanks in advance
ken in o-hi

---

### Post by taurus on 2008-01-06
You could try

```
chmod 755 /*
```

---

### Post by mcduck on 2008-01-06
Here's the output of 'ls -l /' on a working system, this should help you to set the correct permissions back:

```
drwxr-xr-x   2 root root 4,0K 2007-10-31 22:28 bin
drwxr-xr-x   3 root root 4,0K 2007-12-20 10:10 boot
lrwxrwxrwx   1 root root   11 2007-10-31 22:13 cdrom -> media/cdrom
drwxr-xr-x  13 root root  14K 2008-01-06 16:46 dev
drwxr-xr-x 132 root root  12K 2008-01-06 16:45 etc
drwxr-xr-x   3 root root 4,0K 2007-10-31 22:23 home
drwxr-xr-x   2 root root 4,0K 2007-10-16 01:17 initrd
lrwxrwxrwx   1 root root   33 2007-10-31 22:27 initrd.img -> boot/initrd.img-2.6.22-14-generic
drwxr-xr-x  18 root root  12K 2007-12-09 14:44 lib
drwx------   2 root root  16K 2007-10-31 22:13 lost+found
drwxr-xr-x   5 root root 4,0K 2008-01-06 16:45 media
drwxr-xr-x   4 root root 4,0K 2007-10-31 22:04 mnt
drwxr-xr-x   2 root root 4,0K 2007-10-16 01:17 opt
dr-xr-xr-x 155 root root    0 2008-01-06 13:40 proc
drwxr-xr-x  12 root root 4,0K 2008-01-01 11:06 root
drwxr-xr-x   2 root root 4,0K 2007-12-09 14:44 sbin
drwxr-xr-x   2 root root 4,0K 2007-10-16 01:17 srv
drwxr-xr-x  12 root root    0 2008-01-06 13:40 sys
drwxrwxrwt  15 root root 4,0K 2008-01-06 18:27 tmp
drwxr-xr-x  12 root root 4,0K 2007-11-01 22:17 usr
drwxr-xr-x  16 root root 4,0K 2007-11-19 16:25 var
lrwxrwxrwx   1 root root   30 2007-10-31 22:27 vmlinuz -> boot/vmlinuz-2.6.22-14-generic
```

---

### Post by liberum on 2008-01-06
thanks taurus, i thought of that but i wanted to put everything back like it was or as near i could.

thanks mcduck, that was basically what i was looking for.

very appreciated.  at least i have a good bonehead story to share with my co-workers on monday.

thanks again!

---

