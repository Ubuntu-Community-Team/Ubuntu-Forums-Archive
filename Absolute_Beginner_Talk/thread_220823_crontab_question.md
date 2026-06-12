---
title: "crontab question"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-07-22
I have a cron job running in user name lex1 
i have tranfered it to user name admin

how to delete the cron job in lex1?
i thibk the name of the file is 

file:/tmp/crontab.II4VIM/crontab

lex1

---

### Post by bLaDeY on 2006-07-22
Try crontab -e -u lex1

That should give the ability to edit the cron jobs for that particular user.

---

### Post by 5-HT on 2006-07-22
If you want to delete the crontab of a user, you can do also do a ```
crontab -r
``` as the user (or stipulate which user's crontab you'd like to remove via the -u flag).

See 'man crontab' for detailed documentation.

HTH

---

### Post by lex1 on 2006-07-22
thanks for your post

i just did 
crontab -e -u lex1 and deleted what was in the file

before doing that i copied the crontab instructions to a file then 
crontab -l > file in lex1 the n  did sudo cp file /home/admin ( i named the file raj)
and saved the contents to that file which are

# m h  dom mon dow   command
*/44 * * * * suck nntp.aioe.org -A -bp -hl localhost -c -i 200 -M -n -Q


and now when i issue that command on th command line to test it 
stops and does not perform the job as it did in lex1 see below

lex1@xstation:~$ suck nntp.aioe.org -A -bp -hl localhost -c -i 200 -M -n -Q
Invalid default read for new active group, must be <= 0
Attempting to connect to nntp.aioe.org
Using Port 119
Official host name: nntp.aioe.org
Address: 81.174.50.80
Connected to nntp.aioe.org
200 emma.aioe.org InterNetNews NNRP server INN 2.4.3 (20050407 prerelease) ready (posting ok).
200 emma.aioe.org InterNetNews NNRP server INN 2.4.3 (20050407 prerelease) ready (posting ok).
Loading active file from localhost
Reading current sucknewsrc
GROUP <control>, unexpected response, 502
Broken connection, aborting
Elapsed Time = 0 mins 0.81 seconds
GROUP <control>, unexpected response, 502
Broken connection, aborting
Elapsed Time = 0 mins 0.96 seconds
Closed connection to nntp.aioe.org
lex1@xstation:~$ 


lex1
ps admin does not have root privlages but that should not matter

---

### Post by xtacocorex on 2006-07-22
lex1, I think you need to move the sucknewsrc file or whatever it is named to the admin home directoy. 

Also, make sure that the admin user is in /etc/cron.allow so that it can run the cron job.

Hope this helps.

---

### Post by lex1 on 2006-07-22
ok thanks for post yes admin is in /etc/cron.allow
how do i move the directry with all its permissions ?

from lex1 to admin?

here it is
lex1@xstation:~$ cd /etc/suck
lex1@xstation:/etc/suck$ ls -la
total 24
drwxrwxrwx  2 news      news      4096 2006-07-22 08:59 .
drwxr-xr-x 90 root      root      4096 2006-07-22 12:35 ..
-rw-rw-r--  1 news      news      1946 2004-10-27 13:37 get-news.conf
-rw-rw-r--  1 news      news        56 2004-10-27 13:37 suckkillfile
-rw-r--r--  1 lex1      lex1       463 2006-07-22 08:55 sucknewsrc
-rwxrwxrwx  1 news      news       122 2006-07-05 11:15 sucknewsrc.old


lex1

---

### Post by xtacocorex on 2006-07-22
Hmm, I just tested your command with my user and then I did an su to change to my wife's user.

The command worked under both users, so I don't know now. I do know that my previous post is incorrect.

When it runs correctly, there are errors at the end saying that it can't write to /etc/suck/sucknewsrc and another file, but running it with sudo corrected that.

No sudo:
> 
Cleaning up after myself
/etc/suck/sucknewsrc: Permission denied
Moving newsrc to backup: Permission denied
 
With sudo:
> 
Cleaning up after myself
 
In fact, looking at your directory output, you already took that into consideration.

Here is the output of ls -l /etc/suck on my machine.
```

-rw-rw-r-- 1 news news 1946 2004-10-27 07:37 get-news.conf
-rw-rw-r-- 1 news news   56 2004-10-27 07:37 suckkillfile
-rw-r--r-- 1 root root  126 2006-07-22 07:46 sucknewsrc
-rw-rw-r-- 1 news news  124 2004-10-27 07:37 sucknewsrc.old

``` It appears that you need to change the owner of sucknewsrc.

```
sudo chown user:group /etc/suck/sucknewsrc
``` where user and group are the same, most likely the admin user if that's the account that will be running the cron job.

---

### Post by lex1 on 2006-07-23
thanks correct i had a big problem with perrmisions
and yes admin needs thses ie i had to do this
in lex1 so will i have to do the same with
admin?



lex1@xstation:~$ sudo chmod 777 /etc/suck/sucknewsrc
lex1@xstation:~$ sudo chmod 777 /etc/suck

and i am not sure if this is neccessary but how to transfer the suck dir from lex1 to admin?

---

