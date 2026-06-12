---
title: "fail to log on"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by clark0820 on 2007-01-27
Hi, I'm new ubuntu user. I wanted to install "eclipse" for my ubuntu
I searched in the forum and found the following command
code:: apt-get install eclipse-jdt

I typed in the code and wait for the installation. After it was installed, I couldn't log in to my ubuntu again, can anyone show me a way save my ubuntu, thanks a lot. 

following msg are shown when I try to log on:

|||||||||||||||||||||||||||||||||||||||||||||||||| ||||||||||||||||||||

User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe seesions to see if you can fix this problem.

View details (~/.xsession-errors file)
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0. Xservers" -h "" -l ":0" "clark0820"
/etc/gdm/Xsession: Beginning session setup...

(x-session-manager:5023) Gdk-WARNING **: locale not supported by Xlib

(x-session-manager:5023) Gdk-WARNING **: cannot set locale modifiers
Could not set mode 0700 on private per-user gome configuration directory ' /home/clark0820/.gnome2_private/': Operation not permitted

|||||||||||||||||||||||||||||||||||||||||||||||||| |||||||||||||||||||||||||||||||||

---

### Post by taurus on 2007-01-27
Boot into recovery mode from GRUB menu and at the prompt, paste the output of this command here.

```
ls -la /home
```

---

### Post by clark0820 on 2007-01-27
yea, I typed the command

code::             ls -la /home

and it shows the following:

|||||||||||||||||||||||||||||||||||||||||||||||||

total 12
drwxr-xr-x  3 root root 4096 Dec 26 23:19 .
drwxr-xr-x 21 root root 4096 Dec 29 21:04 ..
drwxr-sr-x 47 root root 4096 Jan 26 18:49 clark0820

||||||||||||||||||||||||||||||||||||||||||||||||


but I don't know what to do next

---

### Post by taurus on 2007-01-27
Somehow, your system modified the ownership of your $HOME directory.  You need to change it back so you can log in.  Still from the recovery mode, do

```
chown -R **clark0820**:**clark0820** /home/clark0820
ls -la /home
```
Paste the output of the second command here.

---

