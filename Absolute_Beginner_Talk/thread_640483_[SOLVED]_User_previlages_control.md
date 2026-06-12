---
title: "[SOLVED] User previlages control"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by SteelCore on 2007-12-14
How can I allow normal users to execute a terminal command that requires sudo without getting their permission denied.

---

### Post by Dr Small on 2007-12-14
Greetings,
Please read this article that I wrote on this:
[http://php.8ez.com/drsmall/blog/?p=157](http://php.8ez.com/drsmall/blog/?p=157)

Dr Small

---

### Post by ajgreeny on 2007-12-14
I'm not sure Dr Small's answer is quite the one you want.  If I understood your question right, you will need to add the user to the admin group which you as the current admin user can do by going to System->Administration->Users & Groups then to manage groups and add the username to the admin group.  You can also do it in terminal, but I can't remember the command at the moment, perhaps **usermod** but don't count on that being correct.  That user will then be able to carry out sudo commands if they have the password.

If you just want the user to not need to enter a PW for a particular command then Dr Small is right after all.  Now, however, you've got both possibilities available.

---

### Post by Dr Small on 2007-12-14
Oh. Sorry. I must have misread. :O
But yeah, if you want another user to be able to use sudo, just add him to the admin group.

```
sudo adduser -G admin *newuser*
```

---

### Post by SteelCore on 2007-12-14
It was Drsmail's answer that I was actually seeking but regardless I thank you both for your help.

The command I'm trying to allow the user to execute without a password is (echo 0 > /proc/sys/net/ipv4/tcp_window_scaling).
What is the complete path for this command?

---

### Post by spiderbatdad on 2007-12-14
Doc, I'm curious to know if your article provides an effective argument against dynamically loadable LSM?

---

### Post by rkd on 2007-12-14
echo is a built-in command, and I'm not sure Dr Small's method will get a built-in command to run as root (since it is actually bash that is doing the work of echo).  I suppose you could have your users enter /bin/echo rather than just echo, but that might be confusing for them.  Perhaps you can copy /bin/echo to make a new program, perhaps /bin/writeparam, set up that program to run privileged according to Dr Small's method, and have your users use writeparam instead of echo to modify the setting.

I haven't tried any of this, so I might be overlooking something.

---

