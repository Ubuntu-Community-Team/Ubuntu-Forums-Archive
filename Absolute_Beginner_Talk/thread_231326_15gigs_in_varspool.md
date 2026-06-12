---
title: "15gigs in /var/spool"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-08-07
I need to get rid of these 15gigs in /var/spool

lex1@xstation:~$ sudo du -sh /var/spool
15G 

    
total 20
drwxr-xr-x 5 root   root    4096 2006-06-13 13:54 .
drwxr-xr-x 6 root   root    4096 2006-06-29 10:53 ..
drwxrwx--T 2 daemon daemon  4096 2006-06-13 14:30 atjobs
drwxrwx--T 2 daemon daemon  4096 2005-08-04 15:47 atspool
drwx-wx--T 2 root   crontab 4096 2006-08-07 09:54 crontabs

so without cuseing to much damage how to delete
theres a cron job going in admin that I can stop

is it rm -rf?

lex1

---

### Post by steve.horsley on 2006-08-07
rm -rf may well also delete important directories and cause problems that expect to write to those directories. You probably have to pick through by hand and delete the biggies. But then that may not help because daemons may still be holding the deleted files open which will prevent them from really being deleted, and leave you unable to read later output.

Probably best is to find the big files, check why they are so big, then stop the daemon that's writing to them, delete them, then restart the stopped daemon. 

But I'm no expert - parhaps you should wait for someone else's answers too.

---

### Post by lex1 on 2006-08-07
as far as i can see doing a ps -A the deamons not runing .i am sure they can be deleted some how?
it was a mistake to run the suck program which had suked in masive articles from a partictular newsgroup.

lex1

---

### Post by orb9220 on 2006-08-07
Dosn't the suck program have a option or flag to delete them for you?

---

### Post by lex1 on 2006-08-07
no it does not seem to.
it seems to place them in a control cancel mode in thr programe INN2.

i just need to delete these directories but they are all in blue


lex1

---

