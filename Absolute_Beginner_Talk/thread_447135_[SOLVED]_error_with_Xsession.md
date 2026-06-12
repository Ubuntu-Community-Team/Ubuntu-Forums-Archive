---
title: "[SOLVED] error with Xsession"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by k33bz on 2007-05-17
When I try to login in with the xsession (my default) with my main account, i get this error.
```
your session only lasted less than 10 seconds. If you have not logged yourself out, this could mean there is a problem with the installation or you are out of disk space.
```

All my other accounts work, as well as my other sessions, gnome, fluxbox, and all failsafe sessions.
when i click on Xsession problem descriptions it says this.
```
/etc/gdm/PreSession/default: Registering your session with Xtmp and Utmp
/etc/gdm/Pression/default runing /usr/X11R6/bin/sessrg -a -w /var/log/Xtmp -u /var/run/Utmp -x "/var/lib/gdm/:0 .Xserver"" -l " : .0" "k33bz"
/etc/gdm/Xsession: Beginning session setup...
No Profile for user 'k33bz' found
/home/k33bz/ .Xsession: 2: Xgl: not found
/home/k33bz/.Xsession: 4: gnome-window-decorator: not found
```

how the hell do i fix this, and why did it happen
only thing i have done recently after my last session was talk on gaim, view some sites, watched some youtube, and installed limewire.

---

### Post by k33bz on 2007-05-17
Anybody, please, i need help with this

---

### Post by k33bz on 2007-05-17
NVM, I got it fixed, found a post on here that helped out :)

---

### Post by Pollywoggy on 2007-05-17
What was the problem?  Were you trying to login at a console without a ~/.xinitrc ?

---

### Post by k33bz on 2007-05-17
something wrong with my Xsession file, so i followed the advice i found on a diff. thread that suggested to rename the file to Xsession.bak
and that worked

---

### Post by ran_foru on 2007-06-21
> **k33bz said:**
> something wrong with my Xsession file, so i followed the advice i found on a diff. thread that suggested to rename the file to Xsession.bak
and that worked



Hi

I m facing same problem . Can u help me

what is the location of xsession file and if i rename it xsession.bak file then next time it wont find any file with that name it may generate error or it will create new file 


Tell me exactly what u did ??

Thx

---

### Post by the_rajah on 2007-06-28
I found the Xsession file in /etc/X11/xsession.d but it won't let me rename it or delete it...  Grrrrr... I really don't want to have to do a re-install of Feisty. I had this one set up nicely for what I was doing..

---

