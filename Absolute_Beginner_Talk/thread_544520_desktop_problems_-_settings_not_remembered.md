---
title: "desktop problems - settings not remembered"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by dmlc133 on 2007-09-06
Hi. I seem to be having a problem persuading my computer to remember my settings on reboot, particularly desktop configuration

Whenever I restart my computer, although the desktop is usable, none of the windows I launch have title bars and I can't reposition or resize them. Also Alt-F2 doesn't work until I run metacity --replace from the terminal. So I have to do that before I can run compiz --replace to start compiz. In addition no changes I make to the Compiz OCnfiguration Manager are retained from session to session.

I have tried and tried to add first compiz --replace and then metacity -replace to the System > Preferences > Sessions > StartUp Commands but either I being stupid or it's not working as it never retains the additions (I add the command, click "close", reopen it and the command is gone from the list.

I don;t know if it's a problem with my desktop or a more general problem with permissions or what, but it's really driving me crazy - any advice would be really welcome.

Thanks.

---

### Post by magiceraser06 on 2007-09-21
It sounds like an issue with permissions.  That really would be the only thing that could prevent settings from being saved.

perhaps doing a   sudo compiz --replace  in the terminal may help.

Also, maybe try running everything as root and then trying.

---

### Post by asmoore82 on 2007-09-21
... runing compiz with sudo is not a very good idea ...

how did you go about installing compiz?

check the output of these commands(*none* of them *should*
produce output *if* your permissions are *correct*):

```

**~$** ls -lR .config .gconf | grep root
**~$** ls -lR .config .gconf | grep ^.r-
**~$** ls -lR .config .gconf | grep ^.r-x
```

---

### Post by magiceraser06 on 2007-09-23
thanks for the correction asmoore.  my bad.

---

### Post by R.Bucky on 2007-09-23
Also, check in System > Preference > Sessions. Click the tab for Session Options and make sure that the box is checked to remember session settings.

---

