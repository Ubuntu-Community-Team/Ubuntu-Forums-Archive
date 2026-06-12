---
title: "Switching Desktop Managers"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by kd7swh on 2006-07-08
I was using gdm and switch to kdm and I don't like it. how do I switch back to gdm?

Any help would be great.

---

### Post by catlett on 2006-07-08
When you restart and get to the login screen. Go to the options section and select "change session". Choose "gnome". Enter your user name ans pasword to login. When you do this it will ask you if you want to make GDM your default session manager. Select yes.

It should be as simple as that. If that doesn't hapen post what does, but that has been the way it always worked.

---

### Post by kd7swh on 2006-07-08
"change session" must be a gdm option because there is only session type in kdm. 

I logged into gnome but there was no prompt to switch back.


HELP!

---

### Post by scxtt on 2006-07-08
in a terminal, type **vi /etc/X11/default-display-manager**

put **/usr/sbin/gdm** (nothing else) in that file if you want to use GDM ... and you'll probably have to reboot ...

i've not used KDM, but i assume you can do **sudo /etc/init.d/kdm stop** then do **sudo /etc/init.d/gdm start** to use GDM w/o a reboot ...

---

