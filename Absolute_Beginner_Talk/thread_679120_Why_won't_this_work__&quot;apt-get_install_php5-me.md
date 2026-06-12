---
title: "Why won't this work?  &quot;apt-get install php5-memcache&quot;"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by idavidcrockett on 2008-01-26
Hi All,

I am trying to install php5-memcache on my Dapper Drake server.  The only way I know how to do this is by entering the command:  "apt-get install php5-memcache."  Unfortunately this is not working.  Is there another way to install the memcache module for php5?

Thanks.

---

### Post by RebounD11 on 2008-01-26
what is the output when you run that command?

You might need root priveleges, try adding ***sudo*** in front of it. 

Like this: 
```
sudo apt-get install php5-memcache
```

If that doesn't work, try enabling more repos in System -> Administration -> Software Sources. Check all repos in Third Party Software tab and click close. click reload if it asks you to. Then open up a terminal and do 

```
sudo apt-get update
sudo apt-get install php5-memcache
```

---

### Post by idavidcrockett on 2008-01-26
The output:

[PHP]
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package php5-memcache
[/PHP]

After running "apt-get update," "apt-get install php5-memcache" returned the same output.  Running both commands as sudo did not help either (I am logged in as root).

---

### Post by RebounD11 on 2008-01-26
> **idavidcrockett said:**
> The output:

[PHP]
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package php5-memcache
[/PHP]

After running "apt-get update," "apt-get install php5-memcache" returned the same output.  Running both commands as sudo did not help either (I am logged in as root).

1. don;t log in as root... it can be dangerous .. use sudo ...
2. did you enable the repos?

and you can try searching for php in Synaptic 

System -> Administration -> Synaptic Package Manager

---

### Post by idavidcrockett on 2008-01-26
There is no php5-memcache module in the Dapper Drake Software Packages webpage via([http://packages.ubuntu.com/dapper/web/](http://packages.ubuntu.com/dapper/web/)), but its listed for other versions of ubuntu.  So why is php5-memcache not available for my ubuntu version?

---

### Post by RebounD11 on 2008-01-26
I don't know... try getdeb.net, maybe it's there... :)

Sorry I don't know what to say... maybe it's  a newer package...

---

### Post by hyper_ch on 2008-01-26
maybe it's in universe or multiverse... are those enabled?

---

### Post by JoshuaRL on 2008-01-26
Where did you find about that app?  Was it on a website?  If it's just a program on a different version you can go to packages.ubuntu.com and search for that app.  It should come in a deb.  Hope that helps.

---

