---
title: "PureFTPD and Pure-Admin"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by quiv on 2006-01-15
When I fire up Pure-Admin, it says PureFTPD is not running, but when I go to System > Admin > Services, I see PureFTPD in the list, checked. Any ideas on what I am doing wrong here?

---

### Post by adwait on 2006-01-15
Right click on PureFTP there and select Run Now. the check mark is sto run it on boot......but it may not be currently running. Just a guess.......

---

### Post by quiv on 2006-01-17
right clicking on the service does not produce a right click menu. oh well, thanks.

---

### Post by nanotube on 2006-01-17
open a terminal and type the following: 
```
ps ax |grep ftp
```
see if the proftpd process shows up. if it does, then it is running. if it does not, then do the following in the terminal:
```
sudo /etc/init.d/proftpd
```
That will start the proftpd daemon. 

if you want to make sure that it starts on boot, you might want to install the package sysv-rc-conf with apt-get/synaptic, and use it to enable proftpd in runlevels 2-5 (have to run sysv-rc-conf with sudo, of course).

i am not sure what the services panel's check mark exactly means... that's why i recommend the sysv-rc-conf package.

---

### Post by hen3rz on 2006-01-17
> open a terminal and type the following:
Code:

ps ax |grep ftp

see if the proftpd process shows up. if it does, then it is running. if it does not, then do the following in the terminal:
Code:

sudo /etc/init.d/proftpd

That will start the proftpd daemon. 
I think he was looking how to run **PureFTPD** not **Proftpd**. (Ignore this post if there is no difference between the 2).

---

### Post by Rumor on 2006-01-17
In PureAdmin, click the PureFTPd menu and click on start server to start it.

---

### Post by quiv on 2006-01-25
[QUOTE=Rumor]In PureAdmin, click the PureFTPd menu and click on start server to start it.[/QUOTE]

that option is greyed out. 

[Quote=hen3rz]
I think he was looking how to run PureFTPD not Proftpd. (Ignore this post if there is no difference between the 2).[/QUOTE]

Correct, PureFTP not Pro. 

So again, I see it in the services list, with a checkbox checked. Pure-Admin doesn't think it is running, and I can't start it from Pure-Admin. I am sure I can probably cofigure this in terminal, but would prefer to leverage pure-admin (otherwise, why did I bother with a desktop installation?). 

Any other things I can do to get Pure-Admin to see it?

---

### Post by le0buntu on 2006-02-04
From what I've gathered so far from reading various forum entries here and elsewhere, try setting pure-ftpd to run in standalone mode
```
sudo nano /etc/default/pure-ftpd-common
```
e.g.
```
...
# STANDALONE_OR_INETD: valid values are "standalone" and "inetd".
# Any change here overrides the setting in debconf.
#STANDALONE_OR_INETD=inetd
STANDALONE_OR_INETD=standalone
...
```

From what I can tell reading the README that accomoanies pure-ftpd, the inetd setting is for use with super-servers such as *Inetd (the most common one), TCPserver, G2S, Xinetd, Rlinetd, ... *.

The /etc/init.d/pure-ftp script references /etc/default/pure-ftpd-common and  executes /usr/sbin/pure-ftpd-wrapper.

The manual entry for pure-ftpd-wrapper indicates this *configures and starts Pure-FTPd daemon*.
```
man pure-ftpd-wrapper
```

From this, I've gathered that individual files correesponding to the pure-ftpd command line options should be placed in /etc/pure-ftpd/conf/.

Now that I have my pure-ftpd running
```
leo@snow-leopard:/$ sudo /etc/init.d/pure-ftpd start
Starting ftp server: Running: /usr/sbin/pure-ftpd -l pam -u 1000 -E -O clf:/var/log/pure-ftpd/transfer.log -B
```
it's time to investigate 
```
leo@snow-leopard:/$ sudo pureadmin
```

- leo

---

### Post by jamespi on 2006-05-17
did any one get anywhere with this? i have the same problem.

thanks,
james

---

