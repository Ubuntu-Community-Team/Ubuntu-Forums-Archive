---
title: "Need to run a line in the terminal every day"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-04-02
Hey everyone. I need to run the following command in the terminal every day:

sudo perl eDNS.pl -u everydnsusername -p everydnspassword

How can I set it as a task that will do it at a secified time every day? Thanks!

---

### Post by xXx 0wn3d xXx on 2006-04-02
[QUOTE=amitroy5]Hey everyone. I need to run the following command in the terminal every day:

sudo perl eDNS.pl -u everydnsusername -p everydnspassword

How can I set it as a task that will do it at a secified time every day? Thanks![/QUOTE]
[ Crontab might help. ](http://doc.gwos.org/index.php/Crontab)

---

### Post by IYY on 2006-04-02
You'll need to use [cron]("https://wiki.ubuntu.com/CronHowto?highlight=%28cron%29").

---

### Post by patrick295767 on 2006-04-02
> sudo apt-get -f -y install kcron
sudo kcron

Kcron 
is the kde frontend for crontab

(dotn forget to check the /etc/crontab file once done)

Greetz

---

### Post by kont.raen on 2006-04-02
[QUOTE=amitroy5]Hey everyone. I need to run the following command in the terminal every day:

sudo perl eDNS.pl -u everydnsusername -p everydnspassword

How can I set it as a task that will do it at a secified time every day? Thanks![/QUOTE]

Imho it would be best to set up a cronjob for this :

```
man 5 crontab
```

on the command line will give you all the necessary information on how-to use cron. Feel free to ask, if there should be any questions left, though :)

---

### Post by amitroy5 on 2006-04-02
Do any of these have a GUI? I'm still fresh off of Windows. :(

---

### Post by patrick295767 on 2006-04-03
[QUOTE=amitroy5]Do any of these have a GUI? I'm still fresh off of Windows. :([/QUOTE]
  
Kcron has GUI

once set up
do:

gedit /etc/crontab
and I would highly recommend you to add 'root' in it like the previous lines ... !!
(kcron has just this prob sometimes, i dont know why)

---

### Post by amitroy5 on 2006-04-03
This says it uses the KDE enviornment. Will it still work with Gnome? Thanks!

[QUOTE=patrick295767]Kcron has GUI

once set up
do:

gedit /etc/crontab
and I would highly recommend you to add 'root' in it like the previous lines ... !!
(kcron has just this prob sometimes, i dont know why)[/QUOTE]

[QUOTE=catlett]If you can't solve it by editing, you can go back and reconfigure your settings. It's best to search for a manual on your monitor so you will know the refresh limits and color depth etc. The more info you put in during the configuration, the better resolution detection you'll get. Do this command. 
```
sudo dpkg-reconfigure xserver-xorg
```[/QUOTE]

---

### Post by amitroy5 on 2006-04-04
Kcron only works with programs. I need it to run a line in the terminal. What will also work? I don't mind if there is a GUI or not. Thanks! :)

---

### Post by amitroy5 on 2006-04-04
I read the posts again and I decided to use Crontab. However, I am not sure how to save what I edited. How do we do this? Thanks!

---

### Post by patrick295767 on 2006-04-06
In order to help you, this is my crontab:
   
to make it in 3 steps & very easily: 
0/ > apt-get -f -y install crontab
apt-get -f -y install kcron

1/ kcron
   
2/ vi /etc/crontab     # make sure the root is there to make it run !!  Otherwise, wont work
   
3/ check also : ls -l /etc/crontab
that should be owned by root 
   
```
# This file also has a username field, that none of the other crontabs do.
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
# m h dom mon dow user	command
17 * * * *	root	run-parts --report /etc/cron.hourly
# 
25 6 * * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
# 
47 6 * * 7	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
# 
52 6 1 * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
# Please be informed tthat I am stopping gdm
0,30 0,23 * * *	root	/etc/init.d/gdm	stop
# Please be informed tthat I am stopping kdm
0,30 0,23 * * *	root	/etc/init.d/kdm	stop
# I start the gdm
0 7 * * *	root	reboot
# stop at 22:30
30,45 22 * * *	root	/etc/init.d/gdm stop
# stop at 22:30 kdm
30,45 22 * * *	root	/etc/init.d/kdm stop
# start the chk network 
0,30 * * * *	root	sh -c /etc/init.d/thescript0334.sh
# start the gdm after break for children
5,35 0,1,2 * * *	root	/etc/init.d/gdm start
# script
0 8,12,16,22 * * *	root	sh -c /etc/init.d/myscript_linux.sh
# This file was written by KCron. Copyright (c) 1999, Gary Meyer
# Although KCron supports most crontab formats, use care when editing.
# Note: Lines beginning with "#\" indicates a disabled task.

```

---

