---
title: "[SOLVED] root permission lost"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by omarabbas on 2007-09-18
i some how lost my superuser permission.
when i try to type a command that needs superuser permission for example apt-get
i type $sudo apt-get *package name* but nothing happens
and when i try it without adding sudo it says requested operation requires superuser privilege.

i also cant manage to start synaptic from the system menu
when i click on it nothing happens

any ideas for what could have went wrong?
thank you

---

### Post by psusi on 2007-09-18
sudo apt-get package-name should return an error message because package-name is not a valid apt-get command.  Unless you just made a tyepo in your message and you actually meant apt-get **install** package-name?

---

### Post by thelocust on 2007-09-18
Something similar happened to me once. I restarted and all was well no problems since.

---

### Post by omarabbas on 2007-09-18
yes it was a typo, i meant that any command preceded by sudo won't execute.
and i did try restarting but it didn't fix the problem.
and now i got this message when i tried to run synaptic:"
The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator."

any ideas? i cant even get to download the ubuntu updates.......

---

### Post by omarabbas on 2007-09-19
one more update
now when i try to run a command preceded by sudo i get this message
*omar is not in the sudoers file.  This incident will be reported.*

i'm obviously a complete newbie to ubuntu, and i feel totally lost.
not being able to do anything on my machine for the moment but to use what's already installed which isnt much yet.

i'm getting desperate, please help

---

### Post by psusi on 2007-09-19
Is "omar" the account you created when you installed Ubuntu?

If so, then boot into recovery mode and you will have to fix your /etc/sudoers file.

---

### Post by OffAxis on 2007-09-19
just answered this a few minutes ago...I think it's pertinent.

[http://ubuntuforums.org/showthread.php?t=554316]("http://ubuntuforums.org/showthread.php?t=554316")

> If you screwed up your ownership system wide then give this a try...

reboot into safe mode (boot off the disc and choose 'Repair' to get a root shell)

Then

[B]chown root:root /usr/bin/sudo
chmod u+s /usr/bin/sudo
reboot[/B]


chown = change ownership
root:root = individual : group
/usr/bin/sudo = the sudo command binary

chmod = change mode (how the file operates, what it can modify, etc)
u = user who owns the file (in this case, root)
s = set user (in this case we've changed the user to root, so the file will execute as root)

and make sure that your /etc/sudoers file is read only (thanks to alienexplorers for that).

**ls -l /etc/sudoers** 

should come back something like:

-r--r----- 1 root root 403 2007-01-26 00:31 /etc/sudoers

if not, then 
**chmod 440 /etc/sudoers**
will set it to read only for user and group.

In case you need it, the contents of my sudoers file is
> # /etc/sudoers
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

hth

---

### Post by omarabbas on 2007-09-20
hello

ok i did 
chown root:root /usr/bin/sudo
chmod u+s /usr/bin/sudo
and apparently nothing happened

when i tried 
ls -l /etc/sudoers
i got this
-r--r----- 1 root root 301 2007-09-18 19:47 /etc/sudoers


and by the way 
when i type ls -l /usr/bin/sudo
i get this
-rwsr-xr-x 2 root root 102772 2006-10-09 13:37 /usr/bin/sudo
with /usr/bin/sudo highlighted in red

and thanks a lot for ur help :)

---

### Post by Bothered on 2007-09-20
Could you type "groups" in a terminal and post the results. "admin" should appear in the list.

---

### Post by omarabbas on 2007-09-20
when i type groups i get this
omar adm dialout cdrom floppy audio dip video plugdev scanner netdev lpadmin powerdev admin

yes admin is in the list

---

### Post by Bothered on 2007-09-20
You may have a problem with your /etc/sudoers file. Could you:

Boot into recovery mode and enter (you might need to write this down - recovery mode is command line only):

```
cd /home/[you]
cp /etc/sudoers sudoers.bak
chown [you]:[you] sudoers.bak
chmod 755 sudoers.bak
```

then enter "reboot" and boot into non-recovery mode, enter in a terminal:

```
cat /home/[you]/sudoers.bak
```

and post the results.

---

### Post by omarabbas on 2007-09-20
i followed ur instructions and i got this
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

---

### Post by psusi on 2007-09-20
Yep, you managed to clobber your sudoers file.  Boot back into recovery mode and run nano /etc/sudoers.  The end of the file is missing the following lines:

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

---

### Post by omarabbas on 2007-09-20
Thanks everyone
that worked :D

i'm so happy i can't believe it,,, i was honestly starting to consider reinstalling ubuntu all together!

so thanks a lot for ur help everyone, i would be completley lost without this forum!

and hopefully this post will help anyone who's clumsy enough to screw up his system the way i did mine

thankssssssss

---

### Post by Bothered on 2007-09-20
No problem :-)

By the way, the default /etc/sudoers has the options line set to:

```
Defaults        !lecture,tty_tickets,!fqdn
```

rather than the "Defaults env_reset" that you have. You might want to change that as well.

---

