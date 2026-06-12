---
title: "Administrator Password"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by colddayinapril on 2007-06-15
Just installed today, and i've already run into a bit of a problem. It seems that the password i registard myself with as a user is not the administrator password. I have no idea how to find this password, or how to reset it. It also seems that without it, i can't install any updates or make any major changes.

please help?

---

### Post by obbe on 2007-06-15
> **colddayinapril said:**
> Just installed today, and i've already run into a bit of a problem. It seems that the password i registard myself with as a user is not the administrator password. I have no idea how to find this password, or how to reset it. It also seems that without it, i can't install any updates or make any major changes.

please help?

type ```
sudo passwd root
```
you should be able to insert a new personal password

---

### Post by hyper_ch on 2007-06-15
actually:

Don't set a root password as the above poster said...

Normally you do run admin commands with a "sudo"

e.g.

```

sudo apt-get update

```

Or run a graphical app as admin:

```

gksudo thunar

```

The password for the sudo is the same as your user password.

---

### Post by skymera on 2007-06-15
heh,
[www.ubuntuguide.org](www.ubuntuguide.org)
had loads of stuff, for new usders.
tells tyou about root password aswell.

---

### Post by colddayinapril on 2007-06-15
That works. Thanks.

I wanted to get that taken care of before i start using the begginer manuals. I'm sure some of the stuff in there will require a work admin password :D

---

