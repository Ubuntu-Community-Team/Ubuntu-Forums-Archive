---
title: "Samba will not start"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by thefutoneng on 2007-06-05
Recently upgraded to fiesty from edgy, I use an old P4 machine as a web and file server.  After the upgrade, samba simply would not start.

root@romance:~# smbd
root@romance:~# ps -ef | grep smb
root      3270  4290  0 11:45 pts/0    00:00:00 grep smb


Testparm shows that the smb.conf file which I've been using for nearly a year is fine.  If i attempt to start / restart the process here's what I get:

root@romance:~# /etc/init.d/samba start
 * Starting Samba daemons...                                                                                                                            [ OK ] 

So it appears that the process started, however....

root@romance:~# /etc/init.d/samba restart
 * Stopping Samba daemons...                                                                                                                                   start-stop-daemon: warning: failed to kill 3427: No such process
                                                                                                                                                        [ OK ]
 * Starting Samba daemons...                                                                                                                            [ OK ] 
root@romance:~# 

I'm using version 3.0.24 of samba 

Do i need to upgrade to a more recent version of samba?  Is it worth looking into NFS?  Any help is greatly appreciated.

---

### Post by ukripper on 2007-06-06
> **thefutoneng said:**
> Recently upgraded to fiesty from edgy, I use an old P4 machine as a web and file server.  After the upgrade, samba simply would not start.

root@romance:~# smbd
root@romance:~# ps -ef | grep smb
root      3270  4290  0 11:45 pts/0    00:00:00 grep smb


Testparm shows that the smb.conf file which I've been using for nearly a year is fine.  If i attempt to start / restart the process here's what I get:

root@romance:~# /etc/init.d/samba start
 * Starting Samba daemons...                                                                                                                            [ OK ] 

So it appears that the process started, however....

root@romance:~# /etc/init.d/samba restart
 * Stopping Samba daemons...                                                                                                                                   start-stop-daemon: warning: failed to kill 3427: No such process
                                                                                                                                                        [ OK ]
 * Starting Samba daemons...                                                                                                                            [ OK ] 
root@romance:~# 

I'm using version 3.0.24 of samba 

Do i need to upgrade to a more recent version of samba?  Is it worth looking into NFS?  Any help is greatly appreciated.


Looking at it Samba is already started. Are you refereing to daemons not starting or you are not able to see other machines on network?

Not very clear what exactly the problem is?

---

### Post by thefutoneng on 2007-06-07
If samba is starting, then something is killing it immediately after it starts.  It's PID gets written to a file somewhere after it starts then when i try to restart immediately after here's what i get:

root@romance:~# /etc/init.d/samba restart
 * Stopping Samba daemons...                                                                                                                                   start-stop-daemon: warning: failed to kill **17114**: No such process
                                                                                                                                                        [ OK ]
 * Starting Samba daemons...                                                                                                                            [ OK ] 
root@romance:~# 


So process 17114 (which was the PID when samba "started") doesnt exist.  To confirm I tried to connect from another machine and here's what i got:

root@underwearless:~$ smbclient //192.168.1.1/
Error connecting to 192.168.1.1 (Connection refused)
Connection to 192.168.1.1 failed

---

### Post by abds on 2007-06-07
Hi

I am having the exact same problem. Any help would be appreciated. 

Regards

---

### Post by thefutoneng on 2007-06-11
Anyone out there know how to handle this?

---

### Post by ]Nbx*cmD[ on 2007-07-12
> **thefutoneng said:**
> Anyone out there know how to handle this?

Hey i've got exactly the same problem, and it's VERY important for me to solve it because i'm having it in the school server o_O'

Anyway, check out that when you ps -A | grep smb you get NOTHING, so actually /etc/init.d/samba start is doing nothing at all, and for some reason it tells you [OK] like if it was working alright.

Any answer? The system is a fresh install from today, i did nothing but installing samba and creating the samba users via smbpasswd -a...

Thx!

---

### Post by ukripper on 2007-07-12
TRY this guide -
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by thefutoneng on 2007-07-15
My samba install was working for over a year before this problem started.  The only change I made was an upgrade to Feisty from Edgy.

---

### Post by thefutoneng on 2007-07-16
Digging through the samba log files (/var/log/samab/log.smbd) I found that for some reason samba didn't like the guest account settings.  Commenting out the follwing lines allowed samba to start:
```

map to guest = Bad Password 
guest account = guest 
```

---

### Post by ]Nbx*cmD[ on 2007-07-22
Hey i fixed that by modifying the default smb.conf

Right now i don't have it here as i'm on holiday, but when i come back home (september) i'll post it.

Maybe you'll have solve it already, but just for the record ;)

---

### Post by Akira Tadao on 2007-07-29
I had the same problem when I deleted the user "nobody" for security reasons. When I added the user back, the system got normal and functional.

---

### Post by abds on 2007-08-01
Remving the following line from my smb.conf fixed it for me...

passdb backend = tdbsam guest

---

### Post by barts2108 on 2007-10-25
I had the same message. 

found I forgot the = in the realm line from smb.conf

realm domain.local changed to
realm = domain.local and it works

---

