---
title: "eclipse installation lead to failure to log on"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by clark0820 on 2007-01-27
Hi, I'm now ubuntu user. I wanted to install "eclipse" for my ubuntu
I searched in the forum and found the following command
code::      apt-get install eclipse-jdt

I typed in the code and the I couldn't log in to my ubuntu again, can anyone show me a way save my ubuntu, thanks a lot. following msg are shown when I try to log on:

||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||

User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe seesions to see if you can fix this problem.

View details (~/.xsession-errors file)
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0. Xservers" -h "" -l ":0" "clark0820"
/etc/gdm/Xsession: Beginning session setup...

(x-session-manager:5023) Gdk-WARNING **: locale not supported by Xlib

(x-session-manager:5023) Gdk-WARNING **: cannot set locale modifiers
Could not set mode 0700 on private per-user gome configuration directory ' /home/clark0820/.gnome2_private/': Operation not permitted

|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||

---

### Post by kidders on 2007-01-28
Hi there,

These messages suggest a few things that might be worth checking, although none of them seems to have anything to do with eclipse, per se.

[LIST]
[*]See if your ~/.dmrc is as suggested in the messages ... ie owned by you, and with 644 permissions.
[*]See if your home directory itself is writable by you (and no-one else).
[*]Check that you have some disk space available ... **df** should do the trick.
[*]See if there's a reason why your system failed to change the permissions of ~/.gnome2_private.
[/LIST]

Since the messages you posted seem to give out about problems accessing multiple files, the two most likely possibilities are:

[LIST=1]
[*]You're out of disk space.
[*]Your home directory is a bit screwed up.
[/LIST]

See what you can find out and post back ... whatever your problem is, I'm sure we can sort it out. :-)

---

### Post by MkfIbK7a on 2007-01-28
> **kidders said:**
> Hi there,

These messages suggest a few things that might be worth checking, although none of them seems to have anything to do with eclipse, per se.

[LIST]
[*]See if your ~/.dmrc is as suggested in the messages ... ie owned by you, and with 644 permissions.
[*]See if your home directory itself is writable by you (and no-one else).
[*]Check that you have some disk space available.
[*]See if there's a reason why your system failed to change the permissions of ~/.gnome2_private.
[/LIST]

Since the messages you posted seem to give out about problems accessing multiple files, the two most likely possibilities are:

[LIST=1]
[*]You're out of disk space.
[*]Your home directory is a bit screwed up.
[/LIST]

See what you can find out and post back ... whatever your problem is, I'm sure we can sort it out. :-)

yes i also had this problem the solution was to change the perrmissions of my home BACK to me because they had somehow changed

probably from a graphical sudo...

---

