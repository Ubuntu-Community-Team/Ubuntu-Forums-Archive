---
title: "Help me put this into a cron job"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-09-27
Hi I have a few things I would like to add as a cron job. I have never tried it before so I need some help.

What I want to do is to handle my rsync backup stuff. I have two backup scripts that are intended to run from my file server, but i want them executed from my pc cron. ( hope that makes sense) any way here are the details:

[SIZE="5"]I would first of all like to do something like this:[/SIZE]
have the cron login to my server:
> ssh rudolf@192.168.0.124
then have it execute something like this from terminal:
> rm -rf /media/Backup_200GB/Medier_Backup/backup.3
mv /media/Backup_200GB/Medier_Backup/backup.2 /media/Backup_200GB/Medier_Backup/backup.3
mv /media/Backup_200GB/Medier_Backup/backup.1 /media/Backup_200GB/Medier_Backup/backup.2
mv /media/Backup_200GB/Medier_Backup/backup.0 /media/Backup_200GB/Medier_Backup/backup.1
rsync -a --delete --log-format="%%o %%t %%f" --link-dest=/media/Backup_200GB/Medier_Backup/backup.1 /media/Medier_100GB/ /media/Backup_200GB/Medier_Backup/backup.0/ > /media/Backup_200GB/Medier_Backup/rsync.log
and then log back out again
> logout
I would like this to be done once a week

[SIZE="5"]Secondly and much the same, I would like this executed once a day:[/SIZE]
again log in to my server:
> ssh rudolf@192.168.0.124
then execute something like this:
> rm -rf /media/Backup_200GB/Home_Backup/backup.7
mv /media/Backup_200GB/Home_Backup/backup.6 /media/Backup_200GB/Home_Backup/backup.7
mv /media/Backup_200GB/Home_Backup/backup.5 /media/Backup_200GB/Home_Backup/backup.6
mv /media/Backup_200GB/Home_Backup/backup.4 /media/Backup_200GB/Home_Backup/backup.5
mv /media/Backup_200GB/Home_Backup/backup.3 /media/Backup_200GB/Home_Backup/backup.4
mv /media/Backup_200GB/Home_Backup/backup.2 /media/Backup_200GB/Home_Backup/backup.3
mv /media/Backup_200GB/Home_Backup/backup.1 /media/Backup_200GB/Home_Backup/backup.2
mv /media/Backup_200GB/Home_Backup/backup.0 /media/Backup_200GB/Home_Backup/backup.1
rsync -e ssh -a --delete --log-format="%%o %%t %%f" --link-dest=/media/Backup_200GB/Home_Backup/backup.1 rudolf@192.168.0.149:/home/rudolf/testbackup/ /media/Backup_200GB/Home_Backup/backup.0/ > /media/Backup_200GB/Home_Backup/rsync.log
and then log out again
> logout
Hope someone will help me do this

---

### Post by Dr Small on 2007-09-27
I can make some shell scripts to execute those commands, give you the shell scripts, and the crontab scripts, but it isn't neccessary for crontab to login via ssh. All the server needs is the crontab scripts, and it runs the crontab deamon, whether anyone is logged in or not... So that is not needed, but I see what I can do ;)

Dr Small

---

### Post by Dr Small on 2007-09-27
Attached are day.sh and week.sh, with the proceeding commands that you listed above, for the correct agenda.

Here are the crontabs you need to add to crontab:
```
0 0 * * 0 /home/`whoami`/week.sh
0 0 * * * /home/`whoami`/day.sh
```

Depending upon where you place the shell scripts, depends upon what the path is to them, so I just made it default for the /home/`whoami`/ directory.

Dr Small

---

### Post by jerutley on 2007-09-27
While I'm not going to walk you thru it step by step (I'm a firm believer that being pointed in the right direction to learn how to do something you need is better than just being told how to do it), I will give you some ideas that will hopefully get you started in the right direction.

The first thing you're going to want to do is to set up ssh key-based authentication between your pc and your server - that way your pc can log into the server without a password being provided.  The command to set up a key is "ssh-keygen" - searching for that will undoubtedly give you a few pages that will tell you what you need to do.  But the goal is to be able to log into your server from your pc without providing any form of password.

Second, without some massive work with things such as Expect and TCL, you're not going to be able to run multiple commands on the server - but once you have key-based authentication working, that won't be an issue either, as you will see.

SSH has the capability to simply execute a single command on the remote server, rather than giving you an interactive shell.  You do this by including the command to run after the username/hostname combo - similar to the following:

ssh [email]username@server.name[/email] command options

So, if I wanted to run the command "ls -al" on machine foobar.org as username myself, it would look like the following:

ssh [email]myself@foobar.org[/email] ls -al

pretty simple hmmm?

Now for your rsync command - it's obvious you know about the -e ssh option - why not just use that -e option to push your data from your pc to the server, rather than pull from the pc by running on the server:

rsync -a --delete -e ssh /local/path username@server:/remote/path

Create your scripts, run them by hand to ensure they work as you expect.  Then you have to add them into the crontab - that's also pretty easy.

you edit your crontab file by typing the command "crontab -e" - this will open up your default editor (on Ubuntu this is usually nano) - entries are one per line, consisting of 5 numeric fields separated by white space, and the command to run.  The first 5 fields tell it the time to run:

<From the crontab man page: man 5 crontab>
1 - minute (0-59)
2 - hour (0-23)
3 - day of month (1-31)
4 - month (1-12)
5 - day of week (0-7, with 0 and 7 both indicating Sunday)

so, lets say, for example, you want your first backup script, which you saved to /usr/local/bin/backup.sh, to run every sunday at midnight system time - your crontab line would look like:

0 0 * * 0 /usr/local/bin/backup.sh

See how easy that is?


One gotcha - because of some weirdness in how the $PATH environment variable gets set up for a script running from cron, it's better to have your commands reference full paths inside your script - so, for example, instead of just saying "ssh username@hostname", you would say "/usr/bin/ssh username@hostname"

Hope this info gets you on the right track!

Jeremy

---

### Post by kasperbs on 2007-09-27
Thanks for all your help.
I have mange to set the authentication right so login is not required.

I have set up the following:
> # m h  dom mon dow   command
0 20 * * * /home/rudolf/.scripts/day.sh
0 18 * * 1 /home/rudolf/.scripts/week.sh

day.sh:
> #!/bin/sh

ssh rudolf@192.168.0.124 rm -rf /media/Backup_200GB/Home_Backup/backup.7
mv /media/Backup_200GB/Home_Backup/backup.6 /media/Backup_200GB/Home_Backup/backup.7
mv /media/Backup_200GB/Home_Backup/backup.5 /media/Backup_200GB/Home_Backup/backup.6
mv /media/Backup_200GB/Home_Backup/backup.4 /media/Backup_200GB/Home_Backup/backup.5
mv /media/Backup_200GB/Home_Backup/backup.3 /media/Backup_200GB/Home_Backup/backup.4
mv /media/Backup_200GB/Home_Backup/backup.2 /media/Backup_200GB/Home_Backup/backup.3
mv /media/Backup_200GB/Home_Backup/backup.1 /media/Backup_200GB/Home_Backup/backup.2
mv /media/Backup_200GB/Home_Backup/backup.0 /media/Backup_200GB/Home_Backup/backup.1
rsync -e ssh -a --delete --log-format="%%o %%t %%f" --link-dest=/media/Backup_200GB/Home_Backup/backup.1
rudolf@192.168.0.149:/home/rudolf/ /media/Backup_200GB/Home_Backup/backup.0/ > /media/Backup_200GB/Home_Backup/rsync.log

week.sh:
> #!/bin/sh


ssh rudolf@192.168.0.124 rm -rf /media/Backup_200GB/Medier_Backup/backup.3
mv /media/Backup_200GB/Medier_Backup/backup.2 /media/Backup_200GB/Medier_Backup/backup.3
mv /media/Backup_200GB/Medier_Backup/backup.1 /media/Backup_200GB/Medier_Backup/backup.2
mv /media/Backup_200GB/Medier_Backup/backup.0 /media/Backup_200GB/Medier_Backup/backup.1
rsync -a --delete --log-format="%%o %%t %%f" --link-dest=/media/Backup_200GB/Medier_Backup/backup.1 /media/Medier_100GB/
/media/Backup_200GB/Medier_Backup/backup.0/ > /media/Backup_200GB/Medier_Backup/rsync.log
Would this work?

---

