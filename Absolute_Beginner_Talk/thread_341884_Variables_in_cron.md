---
title: "Variables in cron?"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by BrianH781 on 2007-01-19
Greetings.. 

Very limited experience with Linux (I use it mainly for a testing webserver).  However, what I'm wanting to do is create a cron job which fetches some backup files on my live server on a daily basis.

I have a php script on the live server which dumps the db and creates/gzips and archive file.  I was having the script email it to me, but it's getting too large for that.  So, I was hoping to call wget in a cron job to just fetch the file daily.

The issue is, I want the file to have a unique name each day (db_2007-01-19.sql.tar.gz) and I'm not sure how to create a date variable in cron.  If that's possible, please let me know.  If not, I'll have to write a bash or php script to run locally and call that from cron.  

Which would be the best/simplest/quickest way to make this work?

Thanks in advance,

Brian H.

---

### Post by kidders on 2007-01-19
Hi there,

You can use the output of the **date** command to make a timestamped filename for yourself. Something like this ought to work...

```
FILENAME="db_`date +"%Y%m%d%H%M"`.sql.tar.gz"
```

Since you mentioned PHP, you could achieve the same thing there with something like...

```
$filename='db_'.date('YmdHi',time()).'.sql.tar.gz'
```

---

### Post by BrianH781 on 2007-01-19
Very good.  Works perfect.  Thanks!

---

### Post by kidders on 2007-01-19
No problem :-)

Of course, if you wanted to be *really* smart, you would check that **if [ ! -e "/path/to/$FILENAME" ]** was true before you used the filename.

---

