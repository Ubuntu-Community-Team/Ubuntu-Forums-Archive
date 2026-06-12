---
title: "Re-create accounts"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by Respenus on 2007-09-24
The story goes as follows. On my school Linux computer, I share admin rights with someone else who will take my place when I leave high school this year.

Enough personal stories, the thing is the other admin deleted some accounts due to inactivity (ironically the same people wanted their accounts the same day).

This happened to someone else before and when I re-created his account, it would not log it. I unfortunately forgot what error, but it was something about his home account (will re-check and post afterwards).

I guess it's the problem with the new account working with the home folder with the same name. I just wanted to restore his account, so he wouldn't lose his home folder, but now it seems there is a problem with this.

Like I said, will post the report in a few moments.

---

### Post by Respenus on 2007-09-24
Something about this lines:

This users $HOME/.dmrc folder is being ignored.

and

The session lasted less then  seconds.

I can't copy/paste the window when I try to log into his account. I don't have the time to copy by hand right now, I might do it afterwards and edit this post.

I hope this info will help you somehow.

---

### Post by Respenus on 2007-09-28
User's $HO;E/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

I press OK, then I get his message:

Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one the failsafe sessions to see if you can fix the problem.

View details (~ /.xsessions -errors file)
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp.
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log /wtmp -u /var/run/utmp -x "/var/lib/gdm/:O.Xservers" -h " " -l " :O" "lutar"
/etc/gdm/X sessions: Beginning session setup...
Could not set mode 0700 on private per-user gnome configuration directory '/home/lutar/.gnome2_private/' :Operation not permitted
________________________________________________________________________

So... Lutar is the name of the user I tried to restore.

Also the reports have been written by hand, so there is a change a wrote something wrong, unfortunately I don't have the time to recheck, so I hope this will be enough to give you some idea on what is going on and help me.

Thanks in advance.

---

### Post by Respenus on 2007-09-29
BUMP!

I could really use help on this one.

---

### Post by Respenus on 2007-09-30
Anyone?

---

### Post by Respenus on 2007-10-01
No one knows how to solve this problem?

---

