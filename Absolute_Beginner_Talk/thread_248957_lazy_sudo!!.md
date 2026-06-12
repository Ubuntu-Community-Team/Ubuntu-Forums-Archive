---
title: "lazy sudo?!?!"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by mcolwell on 2006-09-01
I just installed ubuntu.  Everything was fine, then I tried to configure cups.  during which some how sudo stoped working.  here is an example of a term session as it is for me now
```
:~$ sudo ls          
Password:            # I typed the password in wrong
Sorry, try again.
Password:            #typed it in write but WHERE'S LS??
:~$ sudo animal      #animal is not a command. NO ERROR??
:~$

```
This is what happens for any command I try and run with sudo.  I've restarted, investigated my groups, and sudoers. nothing seems wrong any suggestions?  I very much appreciate any help.

---

### Post by jordanmthomas on 2006-09-01
chances are, your user wasn't created with the ability to use sudo.  If you have another user on the system, log in as them and go to System --> Administration --> Users and Groups.

Once in there, click on your user and the Properties.  Go to the User Privileges tab and make sure 'Executing system administration tasks' is checked.  If it already is, I have no clue what the problem is.  

Also, if you don't have any other users to start with I am not sure what you should do either.

---

### Post by mcolwell on 2006-09-01
Well first of all I have only one user.  that user was created with sudo privs because I was happilly using sudo up untill yesterday.  I just investigated and infact everything that requires root pass is behaving simillarly.  I suspect however that all of these other things like System --> Administration --> Users and Groups and gksudo are really just front ends for a sudo command.  the real trouble is that I can't actually do anything usefull right now to fix any of this because I have no other users.  if anyone knows if there is a fix I can do using a live cd that would be great.  I am prepared to reinstall but I would really like to know what caused this so I can avoid it next time.

---

### Post by mcolwell on 2006-09-01
Oh I forgot to mention I was using xfce at the time that it happened however I get the same problem on tty and gnome

---

### Post by taurus on 2006-09-01
Open up a terminal and paste the output of this command here then!!!

```
id
```
Make sure you belong to both adm & admin...

---

### Post by mcolwell on 2006-09-01
results of id

```
uid=1000(mcolwell) gid=1000(mcolwell) groups=1000(mcolwell),1001(printadmin)
```

---

### Post by taurus on 2006-09-01
> **mcolwell said:**
> results of id

```
uid=1000(mcolwell) gid=1000(mcolwell) groups=1000(mcolwell),1001(printadmin)
```
No wonder sudo doesn't work because you don't belong to groups amd & admin!!!  So, you need to boot your machine to recovery mode (from GRUB menu) and edit /etc/group and add yourself, login name, to both groups adm and admin...

```
nano /etc/group
```
Save it and reboot.  Now, see if you can use sudo.

---

### Post by mcolwell on 2006-09-01
it appears that I have a problem looking at that last result.  what I can tell you is that I created the group printadmin then added myself to it I intended to finish this transaction by making printadmin the group that could use the printers but the very next command sudo didn't work.  so I figure this is what caused the problem.  Whats the solution?

---

### Post by mcolwell on 2006-09-01
sorry you posted quicker than I.

---

### Post by taurus on 2006-09-01
> **mcolwell said:**
> sorry you posted quicker than I.
I guess you just have to type faster then!!!  ;)

---

### Post by mcolwell on 2006-09-01
Thank GOD!!  it worked!  Thank you very very much.

---

### Post by taurus on 2006-09-01
> **mcolwell said:**
> Thank GOD!!  it worked!  Thank you very very much.
See how easy it was...  =D>

---

### Post by mcolwell on 2006-09-01
IT WORKED!!!!  Thanks soo very very much.  now off to bigger problems :-)

---

### Post by mcolwell on 2006-09-01
arg I'm confused sorry about that last post. I thought my first one didn't get through or something.

---

