---
title: "/etc/gdm/Xsession fails"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by DSn0wMan on 2006-05-01
I am unable to log into my desktop.

When I login I receive an error message that says try loging in with a failsafe session.

When I check View details (~/.xsession-errors file)

I see a weird message,

/etc/gdm/Xsession: Befinning session setup. . .
/etc/gdm/Xsession: line 73: ls: command not found
/etc/gdm/Xsession: Executing /usr/bin/gnome-session failed!

Any Ideas?

---

### Post by testube_babies on 2006-05-01
This may be a stupid question, but have you tried logging in with a failsafe-gnome session?

---

### Post by DSn0wMan on 2006-05-02
Ya, but that just hangs.

---

### Post by darth_vector on 2006-05-02
[QUOTE=DSn0wMan]/etc/gdm/Xsession: line 73: ls: command not found[/QUOTE]

that doesn't look good, how the hell did that happen?

try booting in safe mode and installing ls. see here: [http://www.ubuntuguide.org/#gainrootwithoutlogin](http://www.ubuntuguide.org/#gainrootwithoutlogin) for instructions on how to boot into safe mode. then do a```
sudo apt-get install ls
```

---

### Post by DSn0wMan on 2006-05-02
[QUOTE=darth_vector]that doesn't look good, how the hell did that happen?

try booting in safe mode and installing ls. see here: [http://www.ubuntuguide.org/#gainrootwithoutlogin](http://www.ubuntuguide.org/#gainrootwithoutlogin) for instructions on how to boot into safe mode. then do a```
sudo apt-get install ls
```[/QUOTE]

The thing is that "ls" is available in the different console run levels.

BTW - 'sudo apt-get install ls' returns a message of no package named ls (or something like that)

---

