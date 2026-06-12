---
title: "Need an apt-get command"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-04-20
If there is one, what is the apt-get command to upgrade from Edgy to Feisty?

Thanks for the info.
kh

---

### Post by Vic_Astro on 2007-04-20
sudo apt-get dist-upgrade

---

### Post by kittyhawk63 on 2007-04-20
> **Vic_Astro said:**
> sudo apt-get dist-upgrade

Thank you.
kh

---

### Post by hardyn on 2007-04-20
Make Sure You Read The How-to!!!

---

### Post by kittyhawk63 on 2007-04-20
> **hardyn said:**
> Make Sure You Read The How-to!!!

Which one? Do you have a good one in mind?

---

### Post by kittyhawk63 on 2007-04-20
> **Vic_Astro said:**
> sudo apt-get dist-upgrade

Nothing happens.
I will go to the HOW TOs and see if there is something else I need to do to use this command. Thanks again.
kh

---

### Post by jordanmthomas on 2007-04-20
```
sudo apt-get update
sudo apt-get dist-upgrade
```

Is it possible you haven't updated apt's cache lately?

---

### Post by kittyhawk63 on 2007-04-20
> **jordanmthomas said:**
> ```
sudo apt-get update
sudo apt-get dist-upgrade
```Is it possible you haven't updated apt's cache lately?

I ran both commands earlier and nothing happened. I will do it again and let you know what happened.

---

### Post by kittyhawk63 on 2007-04-20
kittyhawk63@kittyhawk63:~$ sudo apt-get update
Password:
Reading package lists... Done
kittyhawk63@kittyhawk63:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kittyhawk63@kittyhawk63:~$

I wonder if Feisty is set up for this dist-upgrade yet?

---

### Post by igknighted on 2007-04-20
> **kittyhawk63 said:**
> kittyhawk63@kittyhawk63:~$ sudo apt-get update
Password:
Reading package lists... Done
kittyhawk63@kittyhawk63:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kittyhawk63@kittyhawk63:~$

I wonder if Feisty is set up for this dist-upgrade yet?

You need to change your sources.list file and change every instance of the word "edgy" to "feisty", then update and dist-upgrade

---

### Post by jordanmthomas on 2007-04-20
```
sudo sed -e &#8217;s/edgy/feisty/g&#8217; -i /etc/apt/sources.list
```
^^change all your edgys to feistys

---

### Post by kittyhawk63 on 2007-04-20
> **igknighted said:**
> You need to change your sources.list file and change every instance of the word "edgy" to "feisty", then update and dist-upgrade

I read this on another thread today. Does that mean I delete the word Edgy and write in the word Feisty _***wherever***_ I see the word?

---

### Post by kittyhawk63 on 2007-04-20
> **jordanmthomas said:**
> ```
sudo sed -e ’s/edgy/feisty/g’ -i /etc/apt/sources.list
```^^change all your edgys to feistys

Did you mean this will automatically change every word **edgy **to the word **feisty** in sources.list?

---

### Post by jordanmthomas on 2007-04-20
Generally, yes to your first question.
You may have to be careful if you have added any third party repos that don't have feisty sections yet though.


Yes, that's what the sed command will do.  It changes edgy to fesity

---

### Post by kittyhawk63 on 2007-04-20
> **jordanmthomas said:**
> Generally, yes to your first question.
You may have to be careful if you have added any third party repos that don't have feisty sections yet though.
Yes, that's what the sed command will do.  It changes edgy to fesity

Great. The more I learn Linux the better I "love" it.

What will happen to any 3rd party repos? Will they "just" have to be reinstalled? Or, should I uninstall them first. I have installed a few from Automatix.
kh

---

### Post by jordanmthomas on 2007-04-20
Probably they will have upgraded to have feisty packages, so you should be able to just change edgy to feisty and be on your way.  

Of course, with Automatix you may have troubles.  If you do, it'll probably just be something where you need to comment out (put a # in front of) the repos that are from automatix.

---

### Post by kittyhawk63 on 2007-04-20
> **jordanmthomas said:**
> Probably they will have upgraded to have feisty packages, so you should be able to just change edgy to feisty and be on your way.  
Of course, with Automatix you may have troubles.  If you do, it'll probably just be something where you need to comment out (put a # in front of) the repos that are from automatix.

Ok. Thanks alot jordanmthomas.
kh

---

### Post by kittyhawk63 on 2007-04-20
.

---

### Post by jordanmthomas on 2007-04-20
Look in /etc/apt and see if you have any backups you could rename.
Otherwise, you can probably find the default one somewhere around here.  I don't use Ubuntu or I'd give you mine.

---

### Post by kittyhawk63 on 2007-04-20
> **jordanmthomas said:**
> Look in /etc/apt and see if you have any backups you could rename.
Otherwise, you can probably find the default one somewhere around here.  I don't use Ubuntu or I'd give you mine.

Thanks again Jordan... I searched and found what I needed to do and I already was able to fix it. I got the latest one back. I wonder what made it disappear? First time that has happened.

---

### Post by jordanmthomas on 2007-04-20
It was probably black magic or something.  ;)

---

### Post by kittyhawk63 on 2007-04-20
> **jordanmthomas said:**
> It was probably black magic or something.  ;)

:lolflag:

kh

---

### Post by kittyhawk63 on 2007-04-20
> **jordanmthomas said:**
> It was probably black magic or something.  ;)

I can't believe this. It's gone again. I can't get it to "save".

---

### Post by jordanmthomas on 2007-04-20
maybe use nano instead of gedit?
```
sudo nano /etc/apt/sources.list
```

To press, type Ctrl-x (to exit), y (to answer yes to the question that pops up), enter (to save and quit)

---

### Post by kittyhawk63 on 2007-04-20
> **jordanmthomas said:**
> maybe use nano instead of gedit?
```
sudo nano /etc/apt/sources.list
```To save, type Ctrl-x, y, enter

I'll try that next. I just changed edgy to feisty and am ready to save. I will see if it worked this time. If not, I will give nano a go.
kh

---

### Post by kittyhawk63 on 2007-04-20
That save didn't work either. Tried nano. Nothing on the page. I'll try copying and pasting into nano. I;ll let you know if that works.

---

### Post by jordanmthomas on 2007-04-20
Let's see just what you have in /etc/apt

What does 
```
ls -l /etc/apt
```
output?  Is there in fact a sources.list in there (even though saving in nano or gedit should make a new file when you save anyway)?

---

### Post by kittyhawk63 on 2007-04-20
> **jordanmthomas said:**
> Let's see just what you have in /etc/apt

What does 
```
ls -l /etc/apt
```output?  Is there in fact a sources.list in there (even though saving in nano or gedit should make a new file when you save anyway)?

kittyhawk63@kittyhawk63:~$ ls -l /etc/apt
total 132
drwxr-xr-x 2 root root  4096 2007-04-18 14:28 apt.conf.d
-rw------- 1 root root     0 2006-10-25 06:27 secring.gpg
-rw-r--r-- 1 root root  1760 2007-04-18 10:21 sources.list~
-rw-r--r-- 1 root root  1748 2007-04-18 10:49 sources.list_backup_200704181049
-rw-r--r-- 1 root root  2115 2007-04-18 11:10 sources.list_backup_200704181110
-rw-r--r-- 1 root root  2115 2007-04-18 11:18 sources.list_backup_200704181118
-rw-r--r-- 1 root root  2168 2007-04-18 15:28 sources.list_backup_200704181528
-rw-r--r-- 1 root root  2168 2007-04-18 18:02 sources.list_backup_200704181802
-rw-r--r-- 1 root root  2168 2007-04-19 08:32 sources.list_backup_200704190832
-rw-r--r-- 1 root root  2168 2007-04-19 08:38 sources.list_backup_200704190838
-rw-r--r-- 1 root root  2168 2007-04-19 10:26 sources.list_backup_200704191026
-rw-r--r-- 1 root root  2202 2007-04-19 23:34 sources.list_backup_200704191511
-rw-r--r-- 1 root root  2168 2007-04-19 23:27 sources.list_backup_200704191511~
drwxr-xr-x 2 root root  4096 2006-09-27 16:44 sources.list.d
-rw-r--r-- 1 root root  2168 2007-04-18 11:29 sources.list.old
-rw------- 1 root root  1200 2007-04-18 10:49 trustdb.gpg
-rw-r--r-- 1 root root 36465 2007-04-18 10:49 trusted.gpg
-rw-r--r-- 1 root root 35280 2007-04-18 10:49 trusted.gpg~
kittyhawk63@kittyhawk63:~$ 

I used the last one on the list. I will try copying it and pasting it into nano. Will that work?

---

### Post by jordanmthomas on 2007-04-20
```
sudo cp /etc/apt/sources.list_backup_200704191511~ /etc/apt/sources.list
```
will copy the old file into the proper place.  No need to copy and paste!

but, yes, copy and pasting in nano should work fine.

---

### Post by kittyhawk63 on 2007-04-20
> **jordanmthomas said:**
> ```
sudo cp /etc/apt/sources.list_backup_200704191511~ /etc/apt/sources.list
```will copy the old file into the proper place.  No need to copy and paste!
but, yes, copy and pasting in nano should work fine.

[SIZE=6][COLOR=SeaGreen]B[/COLOR][COLOR=Red]I[/COLOR][COLOR=Blue]N[/COLOR][COLOR=Green]G[/COLOR][COLOR=Magenta]O

I'm copying this one down right now.
[/COLOR][/SIZE]

---

### Post by jordanmthomas on 2007-04-20
```
gksudo "update-manager -c -d"
```
For the record, had you not specified that you wanted an apt-get command I would have suggested this.  It automatically updates your sources.list for you.

---

### Post by kittyhawk63 on 2007-04-20
> **jordanmthomas said:**
> ```
gksudo "update-manager -c -d"
```For the record, had you not specified that you wanted an apt-get command I would have suggested this.  It automatically updates your sources.list for you. 

Live and learn. What can you expect from a man in his mid sixties?

Thanks for the tremendous help.

Now I can go to bed and sleep and not think about this all night.
It is going on 12am.
Good night Jordan....
kh

---

