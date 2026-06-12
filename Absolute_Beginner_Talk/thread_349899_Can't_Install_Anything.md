---
title: "Can't Install Anything"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by Muphin Man on 2007-01-30
Hi, I recently installed ubuntu 6.10 and for some reason I can't install anything it comes back with this error:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

Of course, when I tried dpkg --configure -a, it came right up with this message:

```
dpkg: requested operation requires superuser privilege
```

Can anybody help me out? How do I become a superuser, cause I don't own a cape...

---

### Post by musings on 2007-01-30
> **Muphin Man said:**
> Hi, I recently installed ubuntu 6.10 and for some reason I can't install anything it comes back with this error:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

Of course, when I tried dpkg --configure -a, it came right up with this message:

```
dpkg: requested operation requires superuser privilege
```

Can anybody help me out? How do I become a superuser, cause I don't own a cape...

You need to preface the command with 'sudo' thus:

```
sudo dpkg --configure -a
```

You'll then be prompted for the password.

Regards, Gary

---

### Post by Muphin Man on 2007-01-30
Ok, I tried that and... wait for it... I don't know the password!

I haven't screwed with anything, so it must be the default one, what is it, or how do I set a new password?

Thanks

---

### Post by mhl12 on 2007-01-30
your password is the one you set up during your ubuntu installation.

---

### Post by mikewhatever on 2007-01-30
It is the password you must have chosen while installing Ubuntu.

---

### Post by Muphin Man on 2007-01-30
Ok, it came up with HUGE list of commands, I'm looking to fix installing stuff so... where do I go from here?

Thanks for help so far guys...really fast!

EDIT: Ok, I did the command sudo dpkg --configure -a and the compy started doin' it's thing.

```
Setting up capplets-data (2.16.1-0ubuntu4.2) ...
```

How long is this supposed to be taking...

---

