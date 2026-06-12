---
title: "Need examples to &quot;exclude&quot; using rsync"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by towsonu2003 on 2006-10-24
I'm trying to use rsync for backup my home to an external drive. For the last couple of months, I have been backing up all the folders in there, about 16GB, and it takes long time and very boring. 

Here is what I wanna do:
1. Use baobab to see and select from which folders contain the most data (I know how to do that)
2. Use rsync to back up home (I know how to do that) while excluding the folders I choose in step 2 (not sure about this one)

Can anyone provide me some examples on how to use --exclude-from= and the ~/.rsync/exclude file (found tip at [http://sial.org/howto/rsync/](http://sial.org/howto/rsync/))?

For example, I wanna exclude the folders ~/vmware , ~/.mozilla/firefox/uu0abcd.defalt , and ~/.epiphany ; while copying over ~/

how do I tell rsync this? 
thanks in advance :)

---

### Post by xyz on 2006-10-24
I found this:
[**by Lunar_Lamp**]("http://ubuntuforums.org/showthread.php?t=274297")

and
[**Backup Strategy**]("http://kurup.org/blog/tag/rsync")
Hope this helps. I use a different backup method.

---

### Post by towsonu2003 on 2006-10-24
> **xyz said:**
> 
[**Backup Strategy**]("http://kurup.org/blog/tag/rsync")
Hope this helps. I use a different backup method.

thanks :) this part was very helpful
[quote=link]Here's what my exclude file looks like:
```

- *~
+ /etc
- /home/vinod/web/kurup/log
+ /home
+ /root
+ /usr
+ /usr/local
- /usr/*
- /var/lib/courier
- /var/lib/postgres/data
+ /var
+ /var/lib
- /var/*
- /*

```
The rsync exclude syntax allows you to backup just the files you want. I'll just discuss a couple examples, so you should see the manpage for more details. Line 1 says to ignore any emacs backup files. Line 3 says to ignore /home/vinod/web/kurup/log while Line 4 says to include everything else in the /home directory. Conversely, line 7 says to include /usr/local (and everything in it), while Line 8 says to ignore anything else in the /usr directory. Line 6 is important. If you didn't include it, nothing in /usr/local would get included. Each filename is checked against this list, but in a recursive fashion. So if rsync is working on the file /usr/local/foo, it first looks for a pattern that matches /usr, then for a pattern that matches /usr/local, then finally for a pattern that matches /usr/local/foo. It uses the first pattern that matches. So, if you didn't include line 6, the search for /usr would fine line 8 and stop, thus excluding everything in /usr/local. Not what you want. I know that was confusing - recursion always makes my head spin...

[/quote]

---

### Post by xyz on 2006-10-25
Glad it helped. I haven't but I'll try that backing up method one of these days soon.
Good day to you.

---

