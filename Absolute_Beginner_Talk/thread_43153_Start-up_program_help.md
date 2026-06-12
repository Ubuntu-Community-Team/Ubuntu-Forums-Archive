---
title: "Start-up program help"
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by drdeutsch on 2005-06-20
Whenever I load Ubuntu, I get a number of folders and errors opening that I'd like to get rid of. Specifically:

1) My /home/drdeutsch folder opens
2) Network Manager opens along with a "Enter your password" prompt
3) 1 error that reads "You need to be root to run this program"
4) 1 error that reads "You must run this program as the root user"
5) 1 error that reads "Missing command to run"

As far as the Network manager is concerned, I remove it from the sessions properties, but it keeps popping back on there.
Otherwise, here is what I have loading at startup:

1. gnome-session-properties
2. gnome-smproxy --sm-config-prefix /.gnome-smproxy-ceBeDr/
3. metacity
4. gnome-volume-manager
5. gnome-panel
6. nautilus
7. update-notifier
8. gnome-cups-icon
9. gnome-terminal
10. firefox-bin
11. update-manager
12. gksudo
13. synaptic
14. network-admin (I try to take this off, but it keeps popping back on there every restart)
15. sudo firestarter --start-hidden (done according to the How-to section

If you could tell me what I need to edit and get rid of, I'd appreciate it.
Thanks,
drdeutsch

---

### Post by xmastree on 2005-06-21
[QUOTE=drdeutsch]Whenever I load Ubuntu, I get a number of folders and errors opening that I'd like to get rid of.[/QUOTE]Sounds like you checked 'save this session' or whatever once when you logged out with it in that state.

Close everything, log out checking 'save this session' and next time you log in it should come up clean.

I'm not sure if it's called save session, and my ubuntu box is at home so I can't look right now. But it should be obvious what I mean when you see it.

---

### Post by somuchfortheafter on 2005-06-21
those are not errors...

---

