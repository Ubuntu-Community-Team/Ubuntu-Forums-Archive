---
title: "Help 2 issues cannot update"
date: 2009-01-01
forum: Apple Hardware Users
---

### Post by linuxdummy1021 on 2009-01-01
I have two issues, I cannot keep Mozilla up it crashes constantly I'll be typing along then bam it closes.

The scond is i am trying install updates and possible opera. 
But i keep getting this 

Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '50331651' '-o' 'Synaptic::closeZvt=true' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmpF6ll6b' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator

I am on a PPC running 8.04

---

### Post by cyberdork33 on 2009-01-02
Run this in a terminal and check the output:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by linuxdummy1021 on 2009-01-02
here is what i get back

user@ubuntu:~$ sudo apt-get update
[sudo] password for user: 
user is not in the sudoers file.  This incident will be reported.

---

### Post by stream303 on 2009-01-02
> **linuxdummy1021 said:**
> I am on a PPC running 8.04

Ah, but are you running Debian or Ubuntu?  Cyberdork's fix should work with Ubuntu, but if you are running Debian, leave out sudo.  If you are on Debian, you'll need to log in as root in the terminal, and perform apt-get update and apt-get upgrade.

The sudoers file can be fixed, but you also appear to have another problem - Are you running Xubuntu, and also how much ram do you have?  It almost sounds like an install that may have gone flaky, missing a swap partition, etc...

A couple more details might help point out the trouble...

---

### Post by linuxdummy1021 on 2009-01-02
> **stream303 said:**
> Ah, but are you running Debian or Ubuntu?  Cyberdork's fix should work with Ubuntu, but if you are running Debian, leave out sudo.  If you are on Debian, you'll need to log in as root in the terminal, and perform apt-get update and apt-get upgrade.

The sudoers file can be fixed, but you also appear to have another problem - Are you running Xubuntu, and also how much ram do you have?  It almost sounds like an install that may have gone flaky, missing a swap partition, etc...

A couple more details might help point out the trouble...

256 ram Imac flowerpot 800mhz

running Ubuntu 8.04

---

### Post by stream303 on 2009-01-03
Ok, did this problem just crop up recently, or were you ok for awhile?

Did you recently try to customize / add a root user manually and encounter any issues?

I'd also do a quick housekeeping check:

What does the *date* command show in a terminal?

And are you running out of disk space?  Can you post the output of:

```
df -h
```

I'm just wondering in case you were dual-booting and may be running out of space possibly getting into a corruption issue.  Not likely, but best to check.

And of course that drive may be failing - normally I'd try to force an fsck on it too:

Log in as root:

```
su -
```

then

```
shutdown -rF now
alternately
shutdown -r -F now
```
or

```
touch /forcefsck
```

and reboot normally.  *reboot*

---

