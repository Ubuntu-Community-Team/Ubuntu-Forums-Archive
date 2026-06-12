---
title: "which cron?"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by cnschulz on 2008-01-04
Hi, 

Im confused.

Im running gutsy server and it comes with cron and anacron. I am completely at a loss as to which one to use (and where to use it)

what is the crontab command for? if i do a crontab -e i get a blank file (but i *am* running cron jobs). I have a backup running daily (by placing a script in the cron.daily folder but for the life of me i cant figure out where to set the run times (it runs at 7:40am)

i know that anacron runs under cron but i dont know how to add to anacron. 

i dont really want to have all my daily jobs running at the same time? can i do that with anacron?

what are the cron.* folders for can i just keep dumping scripts in there? wont they all run at the same time?

is it possible for me to ask any more questions??!!

c.

---

### Post by hopelessone on 2008-01-04
you might find this helpful..

[http://www.linuxhelp.net/guides/cron/](http://www.linuxhelp.net/guides/cron/)

especially:
> 
If you want cron to execute a bunch of scripts at 4:18pm every day you could put all of the scripts in one directory (for example, /home/username/cron) and add the following line to your crontab:

18 16 * * * root run-parts /home/username/cron >> /dev/null 2>&1

Ctrl + X then Y and enter will save it...

---

### Post by cnschulz on 2008-01-04
yep. understood. 

i can be more specific with my question now...

i have a cron.d folder which contains (amongst other things) and anacron scrip that contains the following:

30 7    * * *   root	test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null

cool. that explains wher the 7:30-ish  run of my backup script is coming from. 

question. what is the purpose of the cron.d folder and specifically the anacron entry?

next: i have an /etc/crontab file which contains the following:

17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 4	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 4	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 4	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

now, my backup script is in cron.daily... so why isnt it run at 4:25?

what is the connection between 1. cron.d, 2. the cron.daily/weekly/monthly folders and 3., the /etc crontab file? are any redundant?

cheers

c.

---

