---
title: "sudo doesn't work!"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by careca on 2006-08-03
I ran KUSER and I changed something at my profile (I added my account to sudo group I think, but can't remember exactly).

I also created 'wheel gruop' and fron console:
chgrp wheel /bin/su /usr/bin/sudo

Now i can't run any program with sudo.

Help!](*,)

---

### Post by careca on 2006-08-03
It says

```
$ sudo kate
sudo: must be setuid root

```

---

### Post by scxtt on 2006-08-03
reboot into recovery mode and change the files back to:
```
:> ll /bin/su
-rwsr-xr-x 1 root root 24K 2006-04-03 09:37 /bin/su

:> ll /usr/bin/sudo
-rwsr-xr-x 1 root root 92K 2006-05-17 04:41 /usr/bin/sudo
```and you shouldn't need to do anything w/ a wheel group, just add a user to various groups in /etc/group:
```
:> cat /etc/group | grep scxtt
adm:x:4:scxtt
dialout:x:20:cupsys,scxtt
cdrom:x:24:haldaemon,scxtt
floppy:x:25:haldaemon,scxtt
audio:x:29:scxtt
dip:x:30:scxtt
video:x:44:scxtt
plugdev:x:46:haldaemon,scxtt
lpadmin:x:106:scxtt
scanner:x:110:cupsys,scxtt
scxtt:x:1000:
admin:x:111:scxtt
```

---

### Post by careca on 2006-08-03
Still doesn't work.

I've done:
chmod 777 /bin/su
and
chmod 777 /usr/bin/sudo


is OK?

---

### Post by careca on 2006-08-03
It still says:

**sudo: must be setuid root**

---

### Post by careca on 2006-08-03
It still says:

**sudo: must be setuid root**

---

### Post by moma on 2006-08-03
SetUID bit must been set on /usr/bin/sudo 

Do this (as root or sudo)
[COLOR="Green"]chmod 4755 /usr/bin/sudo [/COLOR]

Ls should report this (notice the tiny 's', set_user_id bit)
[COLOR="Green"]ls -l /usr/bin/sudo[/COLOR]
-rw[COLOR="Red"]s[/COLOR]r-xr-x 1 root root 93844 2006-05-17 08:41 /usr/bin/sudo

Study chapter "6. Set user ID, set group ID, sticky bit"
[http://www.zzee.com/solutions/linux-permissions.shtml]("http://www.zzee.com/solutions/linux-permissions.shtml")

or read this book ;-)
[http://www.chongluo.com/books/rute/]("http://www.chongluo.com/books/rute/")
------------------------------------
PS. If you have loosed "User ID" bit on sudo and root-account is locked (it's locked by default), then boot with Ubuntu CD (it's liveCD), mount the root_partition and  set the SetUID bit as instructed.

---

### Post by BLTicklemonster on 2006-09-05
I went into the recovery console, and typed 

ls -l usr/bin/sudo 

and the readout looked fine.

but I knew better...


so I put 

chwon root:root /usr/bin/sudo
then
chmod 4755 /usr/bin/sudo

then I typed 

reboot


and I now have sudo again.

---

### Post by cyborgspiders on 2007-03-08
I had the error
sudo: must be setuid root

I logged in as root. Single user mode would work also.
I followed the above directions
chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo
reboot


and all is well. sudo is back for regular users.

:guitar:

---

### Post by misconfiguration on 2007-05-23
> **cyborgspiders said:**
> I had the error
sudo: must be setuid root

I logged in as root. Single user mode would work also.
I followed the above directions
chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo
reboot


and all is well. sudo is back for regular users.

:guitar:

Worked great for me on my Fedora server, thanks :)

---

### Post by ububaba on 2007-06-16
> **cyborgspiders said:**
> I had the error
sudo: must be setuid root

I logged in as root. Single user mode would work also.
I followed the above directions
chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo
reboot


and all is well. sudo is back for regular users.

:guitar:

[COLOR="Blue"]I tried to apply the above but I could not solve the problem still.
In the terminal I get this[/COLOR]
> ubu@desk~$ sudo script.sh
sudo: /etc/sudoers is owned by uid 1000, should be 0
ubu@desk:~$ 2007-06-16 16:17:57 1HzZ6D-0001SH-J8 <= ubu@desk U=clap P=local S=460


Do not know how to go about further. Please give me a guiding hand. Thanks.

---

### Post by scxtt on 2007-06-16
you need to make sure the file **/etc/sudoers** is owned like mine below:
```
:> ll /etc/sudoers
-r--r----- 1 root root 1.6K May 30 16:27 /etc/sudoers

:> cat /etc/passwd | grep 1000
scxtt:x:1000:100:Scott:/home/scxtt:/bin/bash
```yours seems to be owned by UID 1000, which is generally the 1st user account created ... so you want to be root (boot to recovery mode if you have to) and do **chown root:root /etc/sudoers && chmod 440 /etc/sudoers** ...

---

### Post by ububaba on 2007-06-17
> **scxtt said:**
> you need to make sure the file **/etc/sudoers** is owned like mine below:
```
:> ll /etc/sudoers
-r--r----- 1 root root 1.6K May 30 16:27 /etc/sudoers

:> cat /etc/passwd | grep 1000
scxtt:x:1000:100:Scott:/home/scxtt:/bin/bash
```yours seems to be owned by UID 1000, which is generally the 1st user account created ... so you want to be root (boot to recovery mode if you have to) and do **chown root:root /etc/sudoers && chmod 440 /etc/sudoers** ...
Thank you **SCXTT** I was able to change the ownership from UID 1000. Everything is back to
the old normalcy.

---

### Post by ububaba on 2007-06-17
> **ububaba said:**
> Thank you **SCXTT** I was able to change the ownership from UID 1000. Everything is back to
the old normalcy.

I became too happy too soon apparently there still is a glitch see this:[HTML]
~$ cat /etc/sudoers
cat: /etc/sudoers: Permission denied
[/HTML]

Earlier when I connected the camera to the computer's USB contact,  immediately the information 
popped up on the monitor and the pictures could then be copied/moved to the computer. But now 
its once again demanding installation at **suid root**.  I thought the **suid root** problem was out of 
this world.

[IMG]http://farm2.static.flickr.com/1049/562609595_e30ed9f63d_o.png[/IMG]

---

### Post by scxtt on 2007-06-17
you'd have to be root, or in the "root" group to **cat /etc/sudoers** if it looks like:
```
:> ll /etc/sudoers
-r--r----- 1 root root 1.6K May 30 16:27 /etc/sudoers

```like i mentioned before ... try **sudo cat /etc/sudoers** or **sudo visudo**

as far as the issue w/ your camera, i'm sure HAL (i think it's HAL) tries to automount the storage device and your current user can't do mounts ... you may just need to edit /etc/fstab, not sure - never run into that problem myself ...

---

### Post by ububaba on 2007-06-17
> **scxtt said:**
> you'd have to be root, or in the "root" group to **cat /etc/sudoers** if it looks like:
```
:> ll /etc/sudoers
-r--r----- 1 root root 1.6K May 30 16:27 /etc/sudoers

```like i mentioned before ... try **sudo cat /etc/sudoers** or **sudo visudo**

as far as the issue w/ your camera, i'm sure HAL (i think it's HAL) tries to automount the storage device and your current user can't do mounts ... you may just need to edit /etc/fstab, not sure - never run into that problem myself ...

This is the result. You had something called ***1.6K***  while I had the date preceded by ***403***:

[PHP]

$ ls -l /etc/sudoers
-r--r----- 1 root root 403 2007-06-16 21:33 /etc/sudoers[/PHP]
[PHP]
:~$ visudo cat /etc/sudoers
usage: visudo [-c] [-f sudoers] [-q] [-s] [-V]
[/PHP]

You are spot on about HAL which does the automounting. My problem started when I ran into 
the setsuid root problematics a couple of days ago. I never had to reedit fastab for this reason. 
I will check if there is anything that can be altered. I am one and the only user/owner. At least I
am learning some more aspects of Ubuntu.

---

### Post by scxtt on 2007-06-18
1.6K is the file size, ours won't be the same size because there are differences in the amount of text in the file - not to mention i'm using a totally different OS than you (gentoo) - so the defaults are different i'm sure ...

your /etc/sudoers file looks ok now, on the "outside" - no idea what's in it ...

visudo is a command to use vi (w/ syntax checking + locking) on /etc/sudoers ... so you'd do **sudo visudo** (assuming it's working correctly to begin with) to modify /etc/sudoers ... if you can't sudo @ all and don't have a root login (disabled by default) - you can boot into recovery mode to become root, then do **visudo** to enable the wheel group, the add yourself to the wheel group  ...

---

### Post by ububaba on 2007-06-18
My **/etc/sudoers** file looks like this. I believe it is empty. Some more information ought to go in, for it to 
function properly. Any one has a suggestion?


[PHP]# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL[/PHP]

---

### Post by scxtt on 2007-06-18
it's not empty, just basic ... if you add your non-root user accout to the 'admin' group (the /etc/group file), you'll be able to use sudo as that user ... i'm sure there's a GUI program to do that in ubuntu ...

---

