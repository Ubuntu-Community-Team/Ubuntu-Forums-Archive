---
title: "chmod usage"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by mzilhao on 2006-03-11
hi,

i want to copy all the files i have on my windows partition to my linux partition.
when i do that, all the files get execute permissions... 
how can i chmod all the files from one folder, including the ones on all the sub-folders?

thanks,
Miguel

---

### Post by chuckyp on 2006-03-11
You can man chmod to view which switch you are looking for but if memory serves correct it should be chmod -R would be recursive.  maybe little r not in front of nix right now.  Then you could use a-x to remove executable on the file for all users.

---

### Post by mzilhao on 2006-03-11
yes, but the problem with chmod -R is that it also removes the execute permissions from the folders themselves... meaning that i can no longer access them. 
so, what i need is something that would change the permissions from the files (on all subfolders), but not the subfolders themselves...

---

### Post by chuckyp on 2006-03-11
Well the folders don't need to be executable to enter them.  They only need to be readable.  Are you sure you are using the capitol R.  Try something along the lines of chmod -R a-x /<directory>  if you need to then make the files readable for all users you can chmod -R a+r /<directory>.

-R a-x is making all folders and files non executable for all users.  a+r is making them readable for all users.  a=all o=owner and g=group.  You could also use chmod with numerical values if you look around the net you maybe able to find out how those work.  As the man pages can be confusing if this is your first experience with linux.  Also hop on irc via. xchat join the irc.freenode.net server and channel #ubuntu i'm sure plenty of people would be willing to help you there.

Make sure you post what you did to get it working here so other users whom have the same problem can search.

---

### Post by mzilhao on 2006-03-11
this is what i did:
```
miguel@ubuntu:~$ ll
drwx------  3 miguel miguel   4096 2006-03-11 11:27 test
miguel@ubuntu:~$ chmod -R a-x ./test/
chmod: `./test/': Permission denied
miguel@ubuntu:~$ cd test/
bash: cd: test/: Permission denied
miguel@ubuntu:~$

```
and then i can't access the folder 'test'... i have to 
```
chmod u+x test
```
so that i can acces it again...

---

### Post by psycode on 2006-03-11
insted of changing the file permissions it is always wiser to simply change the group ownership 

chown user:group /file 

the file then inherits the default file attributes of your group.
if you are transfering files from a samba share you should be doing this anyway.

---

### Post by kabus on 2006-03-11
You could run this command  :

```
 find . -type d -exec chmod 755 '{}' \;
```

to give the directories the right permissions again.
(or use '-type f' to change just the permissions of regular files.)

---

### Post by mzilhao on 2006-03-11
kabus, worked just great!

thanks everyone,
Miguel

---

