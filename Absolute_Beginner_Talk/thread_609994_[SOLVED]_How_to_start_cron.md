---
title: "[SOLVED] How to start cron?"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by TreverT on 2007-11-11
I posted elsewhere regarding some backup scripts that would not run, despite being in the cron.hourly (and similar) directories.  Some investigation now makes me think that cron is just not running on my Unbuntu 7.1 install.  

ps aux | grep crond
gets me....
trevert  16729  0.0  0.0   2972   752 pts/0    R+   20:53   0:00 grep crond


Which, if I understand correctly, tells me that I just searched for cron but there is no cron running.  According to what I find online, supposedly cron is started by typing crond as root.  However, when I try:

trevert@trevert-desktop:~$ sudo cron
I get...
cron: can't lock /var/run/crond.pid, otherpid may be 5498: Resource temporarily unavailable

trevert@trevert-desktop:~$ sudo crond
sudo: crond: command not found


And I can't run it as my account, either:

trevert@trevert-desktop:~$ crond
bash: crond: command not found
trevert@trevert-desktop:~$ cron
cron: can't open or create /var/run/crond.pid: Permission denied

How do I start cron?

---

### Post by onelife151 on 2007-11-11
You could possibly at the prompt$ do a sudo su go to root # itself and then run crond and see what happens. It seems that sometimes sudo blows up on itself.

---

### Post by qpieus on 2007-11-11
try```
sudo /etc/init.d/cron start
```

---

### Post by TreverT on 2007-11-11
> **qpieus said:**
> try```
sudo /etc/init.d/cron start
```

Thanks for your help!  I tried that, and it produced this result:

 * Starting periodic command scheduler crond                             [fail] 


It seems to be failing to start up, but I don't know why.

---

### Post by qpieus on 2007-11-11
Hmm, I just tried it on my pc and I got the fail message too. But I know my cron is running and working.

Try "cron" in your grep command instead of crond```
ps aux | grep cron
```
On my pc I get ```
root      5734  0.0  0.0   2336   912 ?        Ss   17:29   0:00 /usr/sbin/cron
```

which tells me cron is loaded.
I suspect cron is actually running Ok on your pc too, perhaps it's your scripts that are the problem? Also, I use my crontab to run my backup scripts rather than the cron.hourly (and similar) directories. I am not familiar with using those directories.

---

### Post by TreverT on 2007-11-12
> **qpieus said:**
> Hmm, I just tried it on my pc and I got the fail message too. But I know my cron is running and working.

Try "cron" in your grep command instead of crond```
ps aux | grep cron
```
On my pc I get ```
root      5734  0.0  0.0   2336   912 ?        Ss   17:29   0:00 /usr/sbin/cron
```

which tells me cron is loaded.
I suspect cron is actually running Ok on your pc too, perhaps it's your scripts that are the problem? Also, I use my crontab to run my backup scripts rather than the cron.hourly (and similar) directories. I am not familiar with using those directories.

Swapping cron for crond produced:

```
trevert@trevert-desktop:~$  ps aux | grep cron
root      5498  0.0  0.1   2332   900 ?        Ss   Nov11   0:00 /usr/sbin/cron
trevert  27136  0.0  0.0   2976   752 pts/0    R+   14:48   0:00 grep cron

```

So, that tells me that cron really is running.  (BTW, what is the difference between cron and crond?)  I know my backup scripts work because I have run them all manually and they do what they're supposed to.  It looks like the problem is in crontab - like cron is reading it but the directions in it are not properly causing cron to run the scripts in the hourly & etc directories.Right now the contents of my crontab are as follows:

```
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#
```

Supposedly these instructions cause cron to run whatever it finds in the /etc/cron.hourly (and other) directories.  But, it isn't doing it.  I'm going to add crontab lines that explicitly direct cron to run the backup scripts by name and see what happens.  I'll report back.

---

### Post by Rinzwind on 2007-11-12
crond is the cron-daemon (basically a process that does nothing unless it's told that there is something to do). 
cron is what addresses crond (I think).

> I know my backup scripts work because I have run them all manually and they do what they're supposed to.
Here you asssume something that might not be correct.
If you use anything outside the dir's in PATH  (I see you have it in your cron) your scripts will fail if you did not use the complete path.

1 hint that might lead you to a notice about what's wrong  ----> 
Did you check the cron log? See: 
/var/log/cron.log 

You can check for the word "error" like this:
more /var/log/cron.log | grep error

But it could also show something like "not found".
Or search your script ;)

It that shows nothing post the script if you can. The one you try to start.

---

### Post by TreverT on 2007-11-12
IT'S ALIVE!!!!  :guitar:

I commented out the daily/hourly/weekly folder commands in my crontab and added direct paths to my scripts, making this:

```
# m h  dom mon dow   command
20 *	* * *	/home/trevert/backup.sh
25 6	* * *   /home/trevert/backupdaily.sh
47 7	* * 7   /home/trevert/backupweekly.sh
# 17 *	* * *	trevert    cd / && run-parts --report /etc/cron.hourly
# 25 6	* * *	trevert	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
# 47 7	* * 7	trevert	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
# 52 4	1 * *	trevert	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
```

I don't know why the previous commands weren't running things in the /etc/cron.daily (and other) folders like they should have, but this is just as well since I can keep all my backup scripts in one spot for easy editing if needed.  I changed crontab to the above, and just like clockwork, on the 20th minute it ran the hourly backup, and I confirmed that both the local drives and the remote FTP site had all received the latest versions of the files.  

Thanks EVERYONE for your help and patience!  I think I've learned something about cron, too, so this worked out well even if it was a bit clumsy.  Oh, and Rinzwind, good luck with the luggage... :)

---

