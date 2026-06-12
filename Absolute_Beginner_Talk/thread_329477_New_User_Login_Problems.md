---
title: "New User Login Problems"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by loves to ski on 2007-01-01
Just installed ubuntu on an old 570 via alternate CD in low memory mode.  Setup seemed to work OK, but after finsishing the setup, I can't seem to login.  It keeps asking me for my login and password, but I'm typing them as I set them up, but it's not working.  Suggestions? Thanks!:confused:

---

### Post by scrooge_74 on 2007-01-01
You have probably ran out of space in the HD, you are going to have to open more space by deleting things, or installing a lighter version of Linux.  How big is the drive?

---

### Post by taurus on 2007-01-01
Did you use the standard install option or did you use the oem option with the alternate CD?  Also, what's your login name then?

---

### Post by loves to ski on 2007-01-01
I used the alternate CD with oem option.  The harddrive is 4 GB.  It never asked me to specify a user name.

Thanks for your prompt response!

---

### Post by jerrynewt on 2007-01-01
Try "oem" without the quotes as username and your extablished password. This will take you to the configure screens and will let you set your own username.

---

### Post by loves to ski on 2007-01-01
Hey thanks.....that worked, but now I need to know how to boot into GNOME.....according to my son.

Appreciate your response.

---

### Post by MkfIbK7a on 2007-01-01
what do you mean "boot into gnome" this is the default desktop manager for ubuntu

---

### Post by taurus on 2007-01-01
> **jerrynewt said:**
> Try "oem" without the quotes as username and your extablished password. This will take you to the configure screens and will let you set your own username.

Actually, you have to run one more command from a terminal to create an actual account for your to use from now one and remove the oem account at the same time.

Applications -> Accessories -> Terminal
```
sudo oem-config-prepare
```

---

