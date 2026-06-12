---
title: "cannot login Gnome"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by jemmyyong on 2007-11-02
Hi..

I cannot login gnome with my username..after I type username and passwords at the login screen and press Enter, the login screen back again waiting for username entry. This problem not happen with root and other username. How to solve this problems?

Regards,

Jemmyyong

---

### Post by Inxsible on 2007-11-02
> **jemmyyong said:**
> Hi..

I cannot login gnome with my username..after I type username and passwords at the login screen and press Enter, the login screen back again waiting for username entry. This problem not happen with root and other username. How to solve this problems?

Regards,

Jemmyyong
The first user that you created while installing is your root username. did you create additional username that you trying to login with ?

---

### Post by jemmyyong on 2007-11-02
The username when installing is "jemmy".  after that I create username "guest". I have username "root".  Everything going well until yesterday I cannot login with "jemmy"

---

### Post by jemmyyong on 2007-11-02
file ".xsession-errors" in folder /home/jemmy :

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:20.Xservers" -h "" -l ":20" "jemmy"
/etc/gdm/Xsession: Beginning session setup...
The application 'x-session-manager' lost its connection to the display :20.0;
most likely the X server was shut down or you killed/destroyed
the application.

---

### Post by jemmyyong on 2007-11-02
I have solved this problems by deleting folder .gnome .gnome2 .gconf in my home folder /home/jemmy although my desktop setting cannot recover..

---

