---
title: "Mplayer plugin AF_INET6 error in firefox"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by WADemosthenes on 2006-06-30
Mplayer claims that it "Couldn't resolve the name for AF_INET6: quicktime.purevideo.com"  The video plays anyway, but what does this mean, and how can I fix it?

PS, this is seperate from my other problem, which was fixed by installing w32codec, thanks.

---

### Post by ookooboontoo on 2007-07-04
Hi, I wonder if you still get this error. I do have it come up on most formats including oggtheora too!

its a really frustrating issue.

---

### Post by jamesrl on 2007-07-29
Basically the `error' message is just a warning saying that it can't use the new fancy ipv6 internet protocol (that basically noone uses), and has to use ipv4 (the familiar 255.255.255.255 type of address).  However, it should still work, it justs posts an annoying dialog first.  To try ipv4 first (and get rid of the error message you can set mplayer to try ipv4 first.

edit ~/.mplayer/conf with your favorite text editor (gedit, emacs, nano, vim, etc.)
and add the following line:
```

prefer-ipv4 = yes

```
or to do it for all users, add the same line to /etc/mplayer/mplayer.conf (though you need root permission to edit that file).
Cheers.

---

