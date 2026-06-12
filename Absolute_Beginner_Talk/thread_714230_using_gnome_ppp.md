---
title: "using gnome_ppp"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by whitecore on 2008-03-03
I am using gnome_ppp because network manager takes a minute or two to load. It gets stuck saying Authenticating this is the part of the log that is causing it to get stuck.

WvDial<*1>: Looks like a welcome message.
WvDial<Notice>: Starting pppd at Mon Mar  3 15:01:30 2008
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.
WvDial<Notice>: Pid of pppd: 5920

---

### Post by spiderbatdad on 2008-03-03
try running ```
sudo wvdialconf
```
then edit /etc/wvdial.conf to include your username, password, and phone info. Save the file.
```
gksu gedit /etc/wvdial.conf
```

Then I think gnome-ppp will behave.

---

### Post by spiderbatdad on 2008-03-03
btw kppp is preferred by many due to fewer bugs.

---

