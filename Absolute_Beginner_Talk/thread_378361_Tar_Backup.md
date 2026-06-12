---
title: "Tar Backup"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by nhandler on 2007-03-07
I am trying to make an automatic backup of my computer. The only thing I can't find is how to add the current date to the filename, so it would be something like Backup-3.7.tar.gz Backup-3-.8.tar.gz. I would even settle for Backup-Mar-7.tar.gz. Could someone tell me how I would do this automatically (Not having to change the name every day). Thanks.

---

### Post by Bachstelze on 2007-03-07
You can use the *date* command for it :

```
mfb@ana:~$ date
Wed Mar  7 13:56:07 CET 2007

```

**EDIT** : I just realized the *date* comand can output the date in lots of ways, one you could find convenient for what you do is :

```
mfb@ana:~/test$ date +%F
2007-03-07
```

I leave the part about *awk* for information but you don't need it.





Then use *awk* to just return a part of it, for example if I want to just have the month - here, Mar) which is the second word of the output, I do :

```
mfb@ana:~$ date | awk '{print $2}'
Mar

```

So for example, to create a file which will be called Month.Day.txt - today, Mar.7.txt - I would do :
```
mfb@ana:~/test$ touch $(date | awk '{print $2}').$(date | awk '{print $3}').txt
mfb@ana:~/test$ ls
Mar.7.txt

```

And voilà :) This should help you do what you want.

---

### Post by nhandler on 2007-03-07
Thank you so much. I knew about the date command, but I didn't know about the +%F part. This will work perfectly.

Edit: For people wondering how to use this date +%F with tar, you would use: tar -cvf /your/dir/Backup-`date +%F`

---

