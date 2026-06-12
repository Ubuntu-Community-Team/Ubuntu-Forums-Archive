---
title: "Extra mouse buttons"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Spacedementia87 on 2007-09-04
I have 2 extra mouse buttons on the side and i'd like to configure them so that one is F5 (for refresh) and the other one can go back in the browser (in windows would be backspace but this doesn't seem to go back for me in ubuntu)

How can i do this?

---

### Post by linuxwizard on 2007-09-04
[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

---

### Post by Spacedementia87 on 2007-09-04
Right i did a few edits and then on restart it wouldn't boot into the GUI so i had to fix the xorg.conf file in the command prompt ( i had missed the S off section)

Once that was done i booted in and could not log in.  After entering my name and password it told me that I was being immediately logged out and gave this as the details

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:20.Xservers" -h "" -l ":20" "bob"
/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 20: [[: not found
Warning: Only changing the first 7 of 11 buttons.
```

Currently logged in as root to make this post.

How can I fix this?

---

