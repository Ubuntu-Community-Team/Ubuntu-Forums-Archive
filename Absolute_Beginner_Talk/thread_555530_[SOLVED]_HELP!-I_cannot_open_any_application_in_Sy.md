---
title: "[SOLVED] HELP!-I cannot open any application in System-Administration!"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by christina_svats on 2007-09-20
Completely out of the blue, I cannot install updates, I cannot open Synaptic or Automatix, and unfortunately not even a root terminal...Nothing on system-administration seems to work!

I really didn't do anything to cause this, I would hate to have to reinstall the whole os again...

Could anybody help me?:(

---

### Post by Jeroen Vernooij on 2007-09-20
What happens when you open a normal terminal, and type in 'sudo nautilus' for example?
Does it ask for your password? 
If so, what happens when you type your password?

---

### Post by philinux on 2007-09-20
Please post any error messages in full.

---

### Post by christina_svats on 2007-09-20
Nothing with sudo nautilus, I type su and asks for my password, which I guess is the password I used to open the root terminal, but I get the following:


christina@christina-laptop:~$ sudo nautilus
sudo: must be setuid root
christina@christina-laptop:~$ sudo nautilus
sudo: must be setuid root
christina@christina-laptop:~$ su 
Password: 
su: Authentication failure
Sorry.
christina@christina-laptop:~$

---

### Post by christina_svats on 2007-09-20
I also tried logging in as a different user, but no luck

---

### Post by christina_svats on 2007-09-20
I first suspected that something is wrong when I got the alert for the available updates and when the update manager opened, I clicked on install updates but nothing happened. 
The only thing I did recently was change the ownership of /usr, in order to paste some header files I needed for a c++ code and then returned the ownership back to root

---

### Post by Jeroen Vernooij on 2007-09-20
Ouch I'm afraid that was not very smart of you to change permissions of the whole /usr

Next time you need to save files to it: just type:
```
gksu nautilus /usr
```
And then you can paste as many files as you want.

For now, I can't help you because I don't know the answer.

---

### Post by Bothered on 2007-09-20
Things to try:

1. Type "groups" in a terminal. If the word "admin" does not appear in the list you are not a member of the admin group and hence cannot administer the system. To fix this boot into recovery mode and add yourself to the group with:

```
adduser [you] admin
```

If that doesn't work:

2. Boot into recovery mode and change the permissions on /usr with:

```
chown root:root /usr
chmod 755 /usr
```

---

### Post by christina_svats on 2007-09-20
christina@christina-laptop:~$ groups
christina adm dialout cdrom floppy audio dip video plugdev netdev lpadmin powerdev scanner admin
christina@christina-laptop:~$

---

### Post by Bothered on 2007-09-20
If 2 in my earlier post doesn't work, type in a terminal:

```
sudo cat /etc/sudoers
```

and post the results.

EDIT: That won't work will it :-( Correction:

If 2 doesn't work above, boot into recovery mode and enter:

```
cd /home/[you]
cp /etc/sudoers sudoers.bak
chown [you]:[you] sudoers.bak
chmod 755 sudoers.bak
```

then boot back into ubuntu (non-recovery) and type in a terminal:

```
cat /home/[you]/sudoers.bak
```

and post the results.

EDIT: Note that recovery mode is command line only. You might need to write the commands down. Also the "reboot" command will reboot your system when in recovery mode.
EDIT2: Correction to final cat command.

---

### Post by christina_svats on 2007-09-20
I used chown root:root /usr    when I re-changed the ownership last time, so I am already back to not being able to create folders,or paste anything in usr, as I intended in the first place. Should I do the recovery mode thing?

---

### Post by christina_svats on 2007-09-20
sorry for being stupid, but, how do I reboot in recovery mode?

---

### Post by Bothered on 2007-09-20
When you reboot the system one of the grub options will be something like:

Ubuntu, kernel 2.6.20-16-generic (recovery mode)

Select that and you will boot into recovery mode.

---

### Post by Jeroen Vernooij on 2007-09-20
That's an easy one, just reboot, and when you see the GRUB menu counting 2..1.. just press ESC and choose recovery mode.

---

### Post by christina_svats on 2007-09-20
christina@christina-laptop:~$ cat /home/christina/sudoers.bak 
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
christina@christina-laptop:~$

---

### Post by christina_svats on 2007-09-20
nothing seems to work, do I have to reinstall ubuntu? Is there a way to do this without losing my files? I guess I could copy them in my windows hd, then boot from the windows cd and delete all partitions, and then back to ubuntu live cd. Is there a way to save me all this trouble?
Thanks

---

### Post by Bothered on 2007-09-20
Your sudoers looks ok, so that's not the problem. Could you enter the following in a terminal:

```
ls -l /usr
```

and post the results.

---

### Post by christina_svats on 2007-09-20
christina@christina-laptop:~$ ls -l /usr
total 196
drwxr-xr-x   2 root root 65536 2007-09-17 22:24 bin
drwxr-xr-x   3 root root  4096 2007-08-12 20:48 etc
drwxr-xr-x   2 root root  4096 2007-08-12 20:25 games
drwxr-xr-x  71 root root 12288 2007-09-17 22:24 include
drwxr-xr-x 173 root root 69632 2007-09-17 22:24 lib
drwxr-xr-x  10 root root  4096 2007-03-22 09:20 local
drwxr-xr-x   2 root root 12288 2007-09-09 15:03 sbin
drwxr-xr-x 325 root root 12288 2007-09-12 17:57 share
drwxrwsr-x   6 root root  4096 2007-08-12 20:27 src
drwxr-xr-x   3 root root  4096 2007-03-22 09:22 X11R6
christina@christina-laptop:~$

---

### Post by Bothered on 2007-09-20
That's as it should be. I'm running out of things to try now ...

Could you enter the following in a terminal and post the result:

```
tail -n 10 /var/log/auth.log
```

---

### Post by christina_svats on 2007-09-20
christina@christina-laptop:~$ tail -n 10 /var/log/auth.log
Sep 20 18:41:09 christina-laptop su[8916]: (pam_unix) authentication failure; logname= uid=1000 euid=0 tty=pts/0 ruser=christina rhost=  user=root
Sep 20 18:41:10 christina-laptop su[8916]: pam_authenticate: Authentication failure
Sep 20 18:41:10 christina-laptop su[8916]: FAILED su for root by christina
Sep 20 18:41:10 christina-laptop su[8916]: - pts/0 christina:root
Sep 20 19:17:01 christina-laptop CRON[9862]: (pam_unix) session opened for user root by (uid=0)
Sep 20 19:17:01 christina-laptop CRON[9862]: (pam_unix) session closed for user root
Sep 20 20:17:01 christina-laptop CRON[11381]: (pam_unix) session opened for user root by (uid=0)
Sep 20 20:17:01 christina-laptop CRON[11381]: (pam_unix) session closed for user root
Sep 20 21:17:02 christina-laptop CRON[13297]: (pam_unix) session opened for user root by (uid=0)
Sep 20 21:17:02 christina-laptop CRON[13297]: (pam_unix) session closed for user root
christina@christina-laptop:~$

---

### Post by Bothered on 2007-09-20
Also, you could execute the following in a terminal and post the result:

```
ls -al ~ | grep root
```

and:

```
 ls -l ~/.ICEauthority 
```

---

### Post by christina_svats on 2007-09-20
christina@christina-laptop:~$ ls -al ~ | grep root
drwxr-xr-x  4 root      root         4096 2007-08-16 23:23 ..
drwxr-xr-x  2 christina root         4096 2007-09-12 17:48 .automatix
drwxr-xr-x  6 root      root         4096 2007-08-30 01:11 foo2zjs
-rw-r--r--  1 root      root      1457703 2007-08-27 05:31 foo2zjs.tar.gz
christina@christina-laptop:~$  ls -l ~/.ICEauthority
-rw------- 1 christina christina 3292 2007-09-20 16:50 /home/christina/.ICEauthority
christina@christina-laptop:~$ 



You are very kind! Thank you for trying so much!

---

### Post by Bothered on 2007-09-20
> **christina_svats said:**
> You are very kind! Thank you for trying so much!

Speaking too soon :-(

I'm out of safe ideas. You could try rebooting into safe mode and then entering:

```
apt-get reinstall sudo
```

but you might want to backup files before you try this. sudo is an integral part of the system.

---

### Post by christina_svats on 2007-09-20
by safe mode you mean recovery mode?
so, will this reinstall the os?
I will back up my files and try 
thanks for your attention, I will post the results

---

### Post by Bothered on 2007-09-20
> **christina_svats said:**
> by safe mode you mean recovery mode?

Yes. Oops. I feel ashamed ...

> **christina_svats said:**
> so, will this reinstall the os?

No, only one small (but important) part.

---

### Post by christina_svats on 2007-09-20
WTF... when I type apt-get reinstall sudo, I get :

E: invalid operation reinstall 

I am cursed....:(

---

### Post by Bothered on 2007-09-20
My mistake. The command should be:

```
apt-get install --reinstall sudo
```

---

### Post by christina_svats on 2007-09-20
You are great!!!!! Everything is working as it should!
I couldn't thank you more!!

Please keep me in mind, should I need more help sometime (I guess that's for sure)

Goodnight and thanks again!

---

### Post by Bothered on 2007-09-20
Excellent, glad I could help

---

### Post by smeashy on 2008-05-28
After some searching, this thread seems to describe my problem perfectly, before i try the solution, should this work the same way on Hardy Heron 8.04?

---

