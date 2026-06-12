---
title: "New users. Confused by man pages?"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by xmastree on 2005-11-16
Take a look at [this]("http://en.wikipedia.org/wiki/Category:Unix_software") instead. It's wikipedia's explanations of some of the more common comands. chown, chgrp, chmod (explaining what that 755 stuff is all about) and it seems to be very well written.

Example:
> **sudo** (superuser do) is a program in Unix, Linux, and similar
operating systems such as Mac OS X that allows users to run programs in
the guise of another user (normally in the guise of the system's superuser).

Compare that with **man sudo:** > SYNOPSIS
       sudo -K &#9474; -L &#9474; -V &#9474; -h &#9474; -k &#9474; -l &#9474; -v

       sudo [-HPSb] [-a auth_type] [-c class&#9474;-] [-p prompt] [-u username&#9474;#uid]
       {-e file [...] &#9474; -i &#9474; -s &#9474; command}

       sudoedit [-S] [-a auth_type] [-p prompt] [-u username&#9474;#uid] file [...]

DESCRIPTION
       sudo allows a permitted user to execute a command as the superuser or
       another user, as specified in the sudoers file.  The real and effective
       uid and gid are set to match those of the target user as specified in
       the passwd file and the group vector is initialized based on the group
       file (unless the -P option was specified).  If the invoking user is
       root or if the target user is the same as the invoking user, no pass&#8208;
       word is required.  Otherwise, sudo requires that users authenticate
       themselves with a password by default (NOTE: in the default configura&#8208;
       tion this is the user’s password, not the root password).  Once a user
       has been authenticated, a timestamp is updated and the user may then
       use sudo without a password for a short period of time (15 minutes
       unless overridden in sudoers).



I know which I prefer... :rolleyes:

---

