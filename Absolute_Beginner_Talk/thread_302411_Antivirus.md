---
title: "Antivirus"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by snl on 2006-11-18
Looking through this forum, I found several antivirus softwares. Which one would you recommend which is fast, light-weight, and efficient?
Do I need to have it run all the time (on-demand)?
If I does not have it run all the time, how often should I scan my files?

Thank you.

---

### Post by adam.tropics on 2006-11-18
Personally I don't bother, and on these forums, you will read differing advice, but if you really feel the need...

[AVG]("http://www.ubuntuforums.org/showthread.php?t=136064&highlight=virus")

[AVAST]("http://www.ubuntuforums.org/showthread.php?t=229128&highlight=virus")

---

### Post by aysiu on 2006-11-18
I don't think you need it at all.
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by TheWizzard on 2006-11-18
if you're new to linux, don't bother and get familiar with the system. 


if you have linux experience, you can start with security issues.
the most important is to backup your home folder. as already stated by aysiu, you personal files are the most important to care about. 
i also like to backup the /etc folder. this folder contains the system settings and a backup can be helpful in many cases.

keep your system up to date. i use the following script:
```
#!/bin/bash

aptitude -y update #2 >&1 | mail -s "apt update" root
aptitude -y upgrade # 2>&1 | mail -s "apt upgrade" root
aptitude -y autoclean

```
and put it in /etc/cron.daily

the next step should be checking for rootkits. i scan my system once a week with both rkhunter and chckrootkit because they use different methods. rootkits are rare in linux and if you use only the standard repo's to install software you're save. 

you can also scan for viruses. this is not for your protection, but for your windows using friends'. 

both are run with this script that i run weekly by putting it in /etc/cron.weekly

the comments are in dutch, sorry. 
the mail is forwarded to my gmail account, so i have one place to check the health of different computers in one account. 

```

#!/bin/bash

#f-prot virus definities updaten:
/usr/lib/f-prot/tools/check-updates

#scannen op virussen en het resultaat mailen:
f-prot /bin /etc /initrd /lib /media /opt /root /srv /tmp /var /boot /dev /home /lost+found /proc /sbin /usr -ext | mail -s "f-prot output alpha" root

#scannen op rootkits en het resultaat mailen:
chkrootkit 2>&1 | mail -s "chkrootkit output alpha" root

#rkhunter rootkit definities updaten:
rkhunter --update

#scannen op rootkits en het resultaat mailen:
rkhunter -c --report-mode --cronjob 2>&1 | mail -s "rkhunter output alpha" root


```

---

### Post by GenX on 2006-11-18
Ok so I put the first code into terminal and it rejected a few things asking me if I am root?

What is root? I used Su ollie then password before doing this to supe up. I am not sure if I am supposed to everytime I run the terminal or not...

Here is what it retuned:

ollie@ollie-laptop:~$ #!/bin/bash
ollie@ollie-laptop:~$ 
ollie@ollie-laptop:~$ aptitude -y update #2 >&1 | mail -s "apt update" root
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Couldn't lock list directory..are you root?
ollie@ollie-laptop:~$ aptitude -y upgrade # 2>&1 | mail -s "apt upgrade" root
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ollie@ollie-laptop:~$ aptitude -y autoclean






> **TheWizzard said:**
> if you're new to linux, don't bother and get familiar with the system. 


if you have linux experience, you can start with security issues.
the most important is to backup your home folder. as already stated by aysiu, you personal files are the most important to care about. 
i also like to backup the /etc folder. this folder contains the system settings and a backup can be helpful in many cases.

keep your system up to date. i use the following script:
```
#!/bin/bash

aptitude -y update #2 >&1 | mail -s "apt update" root
aptitude -y upgrade # 2>&1 | mail -s "apt upgrade" root
aptitude -y autoclean

```
and put it in /etc/cron.daily

the next step should be checking for rootkits. i scan my system once a week with both rkhunter and chckrootkit because they use different methods. rootkits are rare in linux and if you use only the standard repo's to install software you're save. 

you can also scan for viruses. this is not for your protection, but for your windows using friends'. 

both are run with this script that i run weekly by putting it in /etc/cron.weekly

the comments are in dutch, sorry. 
the mail is forwarded to my gmail account, so i have one place to check the health of different computers in one account. 

```

#!/bin/bash

#f-prot virus definities updaten:
/usr/lib/f-prot/tools/check-updates

#scannen op virussen en het resultaat mailen:
f-prot /bin /etc /initrd /lib /media /opt /root /srv /tmp /var /boot /dev /home /lost+found /proc /sbin /usr -ext | mail -s "f-prot output alpha" root

#scannen op rootkits en het resultaat mailen:
chkrootkit 2>&1 | mail -s "chkrootkit output alpha" root

#rkhunter rootkit definities updaten:
rkhunter --update

#scannen op rootkits en het resultaat mailen:
rkhunter -c --report-mode --cronjob 2>&1 | mail -s "rkhunter output alpha" root


```

---

### Post by scrooge_74 on 2006-11-18
use the command sudo and give your normal user password

---

### Post by GenX on 2006-11-18
> **scrooge_74 said:**
> use the command sudo and give your normal user password
sudo is not working for me. it only works if I use su

---

### Post by igknighted on 2006-11-18
Those aren't commands to enter in the terminal, it is a script.  You should save it in a text file then put that file where Wiz suggested.

---

### Post by TheRingmaster on 2006-11-18
> **GenX said:**
> Ok so I put the first code into terminal and it rejected a few things asking me if I am root?

What is root? I used Su ollie then password before doing this to supe up. I am not sure if I am supposed to everytime I run the terminal or not...

Here is what it retuned:

ollie@ollie-laptop:~$ #!/bin/bash
ollie@ollie-laptop:~$ 
ollie@ollie-laptop:~$ aptitude -y update #2 >&1 | mail -s "apt update" root
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Couldn't lock list directory..are you root?
ollie@ollie-laptop:~$ aptitude -y upgrade # 2>&1 | mail -s "apt upgrade" root
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ollie@ollie-laptop:~$ aptitude -y autoclean
this isn't how you use these commands.

---

### Post by gn2 on 2006-11-18
> **aysiu said:**
> I don't think you need it at all.


Even if you dual-boot with a shared data partition where Ubuntu could easily write downloaded nasties into.....? 

Re-boot into Windows and Hey Presto!!! :(

---

### Post by GenX on 2006-11-18
> **igknighted said:**
> Those aren't commands to enter in the terminal, it is a script.  You should save it in a text file then put that file where Wiz suggested.
Ok I got it now. Sorry, third or fourth day? on linux here. I received help on Irc on how to do it. Gotta love technology.

I put it in a text file, moved it to my home folder and then completed it. Thanks a bunch (:

---

### Post by kiyometane on 2006-11-18
AVG and Antivir are the best.
If you need an anti spyware/addware, you can download the professional version of adaware for free.
I dont know if adaware would work on linux

---

### Post by TheWizzard on 2006-11-19
> **GenX said:**
> Ok I got it now. Sorry, third or fourth day? on linux here. I received help on Irc on how to do it. Gotta love technology.

I put it in a text file, moved it to my home folder and then completed it. Thanks a bunch (:

please read my post. if you're inexperienced, don't bother!

you can easily mess things up if you don't exactly know what you're doing.

---

