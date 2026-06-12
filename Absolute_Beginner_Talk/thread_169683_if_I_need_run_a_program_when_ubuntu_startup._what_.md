---
title: "if I need run a program when ubuntu startup. what should I do ?"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by neil_yueh on 2006-05-03
Hi,

in Redhat, if we need auto start a application. we could add program name in rc.local, how to do the same thing on ubuntu (debian) ? 

any advise will be appreciate. thanks a lot ..

best regards
NEIL.;)

---

### Post by frodon on 2006-05-03
Add your script in /etc/init.d then run a : ```
sudo update-rc.d *name_of_script* defaults
```

---

### Post by byenary on 2006-05-03
make a bash called startprog (example)file, something like this

/usr/local/yourprogramtostart

and put it in /etc/init.d

then make a linkname in /etc/rc2.d

Like this

ln -s /etc/init.d/startprof /etc/rc2.d/S99startprog

---

### Post by neil_yueh on 2006-05-03
frodon.

  Thanks , I got it. Very appreciate..

best regards
NEIL.

---

### Post by neil_yueh on 2006-05-03
byenary.

  thanks. understand now..

best regards
NEIL.

---

### Post by cronholio on 2006-05-03
If you want to run a program after you logged into Gnome, set it in System->Preferences->Sessions->Startup Programs.

---

