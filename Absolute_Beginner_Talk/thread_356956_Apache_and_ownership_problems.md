---
title: "Apache and ownership problems"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by equate975 on 2007-02-09
Hi, I am making an ubuntu server for my webpage, I know a little about linux but I messed something up and I can't seem to get it to work now.

I installed apache and php, I was trying to test to see if php was working by making the phpinfo php file.

I could see .html files no problem, but when I tried to see the .php file for the test I got this:

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/var/www/index.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0


I searched this forum and another user had the same problem, as to what the thread said I did a chmod 744 to /var/www/

Now the only thing I can get is this:

Forbidden

You don't have permission to access / on this server.

What did I do? And how do I fix this?

Thanks for all the help, I really appreciate it!

Peter

---

### Post by equate975 on 2007-02-09
Wow this ALWAYS happens when I post on boards. I spend about 2 hours trying to fix it myself before I ask for help, then 2 min after I ask I fix it!

I just did chmod 755 to /var/www/ and now it all works great

---

### Post by equate975 on 2007-02-09
Spoke too soon :)

I can't seem to view .jpg (or I am assuming other non .php or .html) files on the apache server, not ones that are in a HTML page, but in directory view when I click on them.

I just get this:

Forbidden

You don't have permission to access /err22.JPG on this server.

---

### Post by equate975 on 2007-02-09
bump

---

### Post by marcus2004 on 2007-02-16
Not sure if this is too late or not but you should do a:
```
chmod 755 -R /var/www/
``` that makes everything that directory accessable as well.

---

