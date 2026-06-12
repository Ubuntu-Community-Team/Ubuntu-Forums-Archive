---
title: "[SOLVED] Post install issues, (gutsy from Linux Mag dvd)"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Araldia on 2008-04-20
I am relearning linux, after a long time away. Please treat me as a complete beginner.
I ran ubuntu 7.10 (base system) from Linux Magazine and installed. I do not wish to install the other distros on the dvd.
During install I provided username and password. (wrote them down as well)
The install commented out the repos stating security.ubuntu.com commented out entries in /etc/apt/sources.list.
After reboot on install completion, I attempted to log in using the username and pass I provided.
The error incorrect username or password came up.
I have spent all day attempting to follow instructions, I have checked the sudoers, used adduser and useradd, all to no avail.
If I use useradd or adduser it seems to work until I try passwd USERNAME, at which point it states unknown user.
I used xstart to get into the gui, and it shows one user named ubuntu, which is listed in sudoers and i have changed passwd for.
Having checked the sources.list everything is commented out. If I try nano or gedit in terminal nothing happens, and if I try to edit from the folder it tells me I do not have the right privs.
Tried a fresh install and same thing. I can't therefore use apt-get and many things fail to actually load, such as the manual configure network and users and groups.

Is this as simple as I need another distro on the top?
Should I give up and burn an ISO for gutsy from somewhere else?
Or is the problem me?
Thank you all those who answered the "lost username or password" threads, although they didn't work for me, they were worth a go.

---

### Post by wpshooter on 2008-04-20
Are you doing a server installation or are you really wanting to do a Live CD (desktop) installation ?

---

### Post by Araldia on 2008-04-20
Do i need a server installation? (not 100% sure of the difference)
I want ubuntu to run (It has a sperate hdd with win xp on a diff hdd) on the drive in the normal way (with GUI). I assumed that installing from the live cd so I don't need the cd anymore was what I had to do?
Should I get another download and burn an iso instead of using the one on this dvd?

---

### Post by Araldia on 2008-04-20
Gave up, went out bought an Ubuntu book with edgy distro.
That worked.
Whole new set of problems.

---

