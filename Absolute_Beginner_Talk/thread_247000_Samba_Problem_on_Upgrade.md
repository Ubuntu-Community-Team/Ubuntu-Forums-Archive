---
title: "Samba Problem on Upgrade"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by bryan4134 on 2006-08-30
Upgrading from 5.10 to 6.06

Mostly working but I keep getting this error:

Setting up libtheora0 (0.0.0.alpha7-1ubuntu1~dapper1) ...

Errors were encountered while processing:
 samba
 samba-dbg
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc2.d/S91samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/S91samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
dpkg: dependency problems prevent configuration of samba-dbg:
 samba-dbg depends on samba (= 3.0.22-1ubuntu3.1); however:
  Package samba is not configured yet.
dpkg: error processing samba-dbg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba
 samba-dbg

Any help appreciated.  Thanks, Bryan

---

### Post by TFX360 on 2006-08-30
> **bryan4134 said:**
> Upgrading from 5.10 to 6.06

Mostly working but I keep getting this error:

Setting up libtheora0 (0.0.0.alpha7-1ubuntu1~dapper1) ...

Errors were encountered while processing:
 samba
 samba-dbg
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc2.d/S91samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/S91samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
dpkg: dependency problems prevent configuration of samba-dbg:
 samba-dbg depends on samba (= 3.0.22-1ubuntu3.1); however:
  Package samba is not configured yet.
dpkg: error processing samba-dbg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba
 samba-dbg

Any help appreciated.  Thanks, Bryan

Dear Bryan,

Could you do:


```
sudo aptitude install samba
```

Aptitude handles dependancies better...

and maybe an

```
sudo apt-get install samba --fix-missing
```

---

### Post by bryan4134 on 2006-08-30
Thanks - tried that but same result - here is the output....

bryan4134@ubuntu_bryan:~$ sudo aptitude install samba
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc2.d/S91samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/S91samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
dpkg: dependency problems prevent configuration of samba-dbg:
 samba-dbg depends on samba (= 3.0.22-1ubuntu3.1); however:
  Package samba is not configured yet.
dpkg: error processing samba-dbg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba
 samba-dbg
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc2.d/S91samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/S91samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
dpkg: dependency problems prevent configuration of samba-dbg:
 samba-dbg depends on samba (= 3.0.22-1ubuntu3.1); however:
  Package samba is not configured yet.
dpkg: error processing samba-dbg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba
 samba-dbg
bryan4134@ubuntu_bryan:~$ sudo apt-get install samba --fix-missing
Reading package lists... Done
Building dependency tree... Done
samba is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc2.d/S91samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/S91samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
dpkg: dependency problems prevent configuration of samba-dbg:
 samba-dbg depends on samba (= 3.0.22-1ubuntu3.1); however:
  Package samba is not configured yet.
dpkg: error processing samba-dbg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba
 samba-dbg
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any other thoughts?   Bryan

---

### Post by TFX360 on 2006-08-30
> **bryan4134 said:**
> Thanks - tried that but same result - here is the output....

bryan4134@ubuntu_bryan:~$ sudo aptitude install samba
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc2.d/S91samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/S91samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
dpkg: dependency problems prevent configuration of samba-dbg:
 samba-dbg depends on samba (= 3.0.22-1ubuntu3.1); however:
  Package samba is not configured yet.
dpkg: error processing samba-dbg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba
 samba-dbg
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc2.d/S91samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/S91samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
dpkg: dependency problems prevent configuration of samba-dbg:
 samba-dbg depends on samba (= 3.0.22-1ubuntu3.1); however:
  Package samba is not configured yet.
dpkg: error processing samba-dbg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba
 samba-dbg
bryan4134@ubuntu_bryan:~$ sudo apt-get install samba --fix-missing
Reading package lists... Done
Building dependency tree... Done
samba is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc2.d/S91samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/S91samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
dpkg: dependency problems prevent configuration of samba-dbg:
 samba-dbg depends on samba (= 3.0.22-1ubuntu3.1); however:
  Package samba is not configured yet.
dpkg: error processing samba-dbg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba
 samba-dbg
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any other thoughts?   Bryan


Reinstall? Backup you configs and 


```
sudo aptitude remove samba
```


```
sudo aptitude install samba
```


Agian use aptitude for the dependancies.

---

### Post by bryan4134 on 2006-08-31
> **TFX360 said:**
> Reinstall? Backup you configs and 


```
sudo aptitude remove samba
```


```
sudo aptitude install samba
```


Agian use aptitude for the dependancies.
I have tried to remove samba but I get the basically the same error message - see below.....

bryan4134@ubuntu_bryan:~$ sudo aptitude remove samba
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REMOVED:
  samba
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 7250kB will be freed.
Writing extended state information... Done
(Reading database ... 82397 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing samba (--remove):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

---

### Post by TFX360 on 2006-08-31
> **bryan4134 said:**
> I have tried to remove samba but I get the basically the same error message - see below.....

bryan4134@ubuntu_bryan:~$ sudo aptitude remove samba
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REMOVED:
  samba
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 7250kB will be freed.
Writing extended state information... Done
(Reading database ... 82397 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing samba (--remove):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

Seems to be something with this simlink,

invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba

Try and move it elsewhere and try again.

---

### Post by desmondo on 2006-09-01
> Seems to be something with this simlink,

invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba

Try and move it elsewhere and try again.

I removed the symlinks (identical ones in rc2.d and rc3.d) and then the install worked.  Samba now seems to be working fine.  I also manually created new symlinks in these 2 directories to point to init.d/samba.

How do we get the problem fixed so others don't have to do this workaround?

---

### Post by TFX360 on 2006-09-01
> **desmondo said:**
> I removed the symlinks (identical ones in rc2.d and rc3.d) and then the install worked.  Samba now seems to be working fine.  I also manually created new symlinks in these 2 directories to point to init.d/samba.

How do we get the problem fixed so others don't have to do this workaround?

You could report your bugs [here]("https://launchpad.net/malone") according to the Forum front page.


Swoong!

Glad it helped!

---

### Post by desmondo on 2006-09-01
Thanks for your help and the link to the bug database, TFX.

Actually, bug [48082]("https://launchpad.net/distros/ubuntu/+source/samba/+bug/48082") already exists.

---

### Post by TFX360 on 2006-09-01
> **desmondo said:**
> Thanks for your help and the link to the bug database, TFX.

Actually, bug [48082]("https://launchpad.net/distros/ubuntu/+source/samba/+bug/48082") already exists.

It's buggy when a bug gets bugged. 

Here to help, good luck sharing!

---

### Post by dsyn on 2006-09-19
[QUOTE=Sebata_Afrika]- got inside this folder by: $ cd /etc/rc2.d/
- and checked all the links, particularly to see the link between K09samba and samba by: $ ls -al (this is what we found K09samba -> /samba)
- then removed K09samba by: $ sudo rm K09samba
- then removed samba by: $ sudo apt-get remove -f samba
- we then did this: sudo apt-get -f install (might not do anything)
- the install samba: $sudo apt-get install samba
- and created the soft link: $ sudo ln -s ../init.d/samba K09samba
Then everything worked. We followed the same procedure in rc3.d strating changing the directory.[/QUOTE]

found this another thread that might help

[http://www.ubuntuforums.org/showthread.php?t=240699&highlight=samba%3A+subprocess+error+exit+status+102](http://www.ubuntuforums.org/showthread.php?t=240699&highlight=samba%3A+subprocess+error+exit+status+102)

---

### Post by jamaas on 2006-10-23
I had the same problem with upgrading, missing links to K09Samba, and it happened previously when upgrading to Dapper.

Jim

---

### Post by acascianelli on 2006-10-25
I had this problem on an install of Dapper.  I ended up removing the link then the samba packaged was able to be removed cleanly.

---

