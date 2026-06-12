---
title: "[SOLVED] synaptic package manager won't start"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by DarinB on 2007-09-12
got this message
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
help???

---

### Post by justin whitaker on 2007-09-12
> **DarinB said:**
> got this message
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
help???

Open a terminal, and copy or type the 'dpkg --configure -a' command into it (as SU or SUDO, of course).

---

### Post by DarinB on 2007-09-12
ok  that worked now this came up what do i do???
i am fearful it will kill my system Help!!!!

the PostgreSQL version 8.1 is obsolete, but you still have the server and/or client package installed. Please install the latest packages (postgresql-8.2 and postgresql-client-8.2) and upgrade your existing  clusters with pg_upgradecluster (see manpage).

Please be aware that the installation of postgresql-8.2 will automatically create a default cluster 8.2/main. If you want to upgrade the 8.1/main cluster, you need to remove the already existing 8.2 cluster (pg_dropcluster --stop 8.2 main, see manpage for details).

The old server and client packages are not supported any more. After having upgraded the existing clusters, you should remove the postgresql-8.1 and postgresql-client-8.1 packages.

---

### Post by krlill on 2007-09-12
I got this message yesterday after trying to install Quake III Arena.  The manager would get the data off the QIII cd then try to download point release from software company.  Their server was down so it would go back to getting data off of cd then trying to download point release again.  Never ending loop.  I couldn't cancel the process (i'm a new at linux) and i couldn't get cd out so i shut down the pc.  I started Ubuntu and still the cd drawer wouldn't open.  Went back to synaptic package manager and that's when I got this message. 

Eventually got cd out by restarting Ubuntu and opening drawer before operating system stared.  The synaptic package manager then started normally. 

Is your problem similar?

---

### Post by Beggar on 2007-09-12
> **DarinB said:**
> ok  that worked now this came up what do i do???
i am fearful it will kill my system Help!!!!

the PostgreSQL version 8.1 is obsolete, but you still have the server and/or client package installed. Please install the latest packages (postgresql-8.2 and postgresql-client-8.2) and upgrade your existing  clusters with pg_upgradecluster (see manpage).

Please be aware that the installation of postgresql-8.2 will automatically create a default cluster 8.2/main. If you want to upgrade the 8.1/main cluster, you need to remove the already existing 8.2 cluster (pg_dropcluster --stop 8.2 main, see manpage for details).

The old server and client packages are not supported any more. After having upgraded the existing clusters, you should remove the postgresql-8.1 and postgresql-client-8.1 packages.

Just read the output. 

You need to install an up to date version of postgresql-8.2. Its not complex, if you really dont know how to do it, search the forums or google for a howto. 

Seriously though, everything you need to know is stated in plain english right there...

```

sudo apt-get install postgresql-8.2 postgresql-client-8.2
man pg_upgradecluster

```

then read the man page to figue out how to upgrade them. remove the 8.2/main cluster, upgrade yours.

```

sudo apt-get remove postgresql-8.1 postgresql-client-8.1

```

---

### Post by krlill on 2007-09-12
Yikes!   Good luck.  :)

---

### Post by DarinB on 2007-09-12
Thanks a bunch it worked exactly as you  wrote it.
now i have emailed the Developer on how to work the sql server on my machine
thanks again

---

