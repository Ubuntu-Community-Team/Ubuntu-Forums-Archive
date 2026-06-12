---
title: "Help with chmod"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by hansoffate on 2007-04-10
I just uploaded and untarred joomla to my webserver.  Now that I am trying to install it, it says a whole bunch of files are unwritable.  How do I change these so that they are writable?  Also who should the owner and group be?  How would I change all of these?

Thanks
-Hans

---

### Post by annda on 2007-04-10
unless there are other suggestions in the joomla manual (your main reference), i'd go with:

```
sudo chown -R root:admin /joomla_directory
sudo chmod -R 775 /joomla_directory
```

if you want any of those files to be overwritten via http/cms, root:www-data as owner might be a better idea. i'm not an expert - try both.

---

### Post by hansoffate on 2007-04-10
I did the commands you said but I still have "unwritable"

```
hansoffate@mythlinux:/var/www/banduh$ ls -l
total 1924
drwxrwxr-x  9 root admin    4096 2006-12-24 12:21 administrator
drwxrwxr-x  2 root admin    4096 2006-12-24 12:22 cache
-rwxrwxr-x  1 root admin   99938 2006-12-24 12:20 CHANGELOG.php

```

This is what joomla gives me
```
administrator/backups/	Unwriteable
administrator/components/	Unwriteable
administrator/modules/	Unwriteable
administrator/templates/	Unwriteable
cache/	Unwriteable
```


Although, it seems to be writable.  Any ideas?  
Thanks,
Hans

---

### Post by raptor2552 on 2007-04-10
Are you installing Joomla with sufficient permissions to write to those directories?

---

### Post by hansoffate on 2007-04-11
I don't know.  I wget, then sudo tar it.  If you write out what I should do from fresh, I can try again.

Thanks for the help,
Hans

---

### Post by hansoffate on 2007-04-11
bump

---

### Post by darkrose on 2007-04-11
try:
chgrp -R www-data /joomla/directory

Which should get you write access.

Could also try:
sudo chmod -R o+w /joomla/directory

This will give EVERYONE write access though, so not recommended if it's live on the web.

---

### Post by hansoffate on 2007-04-11
I did sudo chmod 777 /var/www/joomla 
and it worked.  

This is just for testing purposes, so i figure it will be fine.  (i think 777 is all open right?)

Thanks for the help
-Hans

---

### Post by tarek on 2007-04-11
Hi,

I don't like numbers so there is another way to change permissions.

a=all, o=other, u=user, g=group

w=write, x=execute, r=read

chmod o+w someFile

makes someFile writable


chmod o-w someFile

makes someFile not writable


tk

---

### Post by hansoffate on 2007-04-12
cool, thanks for the tutorial.

---

