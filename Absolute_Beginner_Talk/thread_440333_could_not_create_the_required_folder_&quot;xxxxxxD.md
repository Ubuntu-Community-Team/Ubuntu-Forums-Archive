---
title: "could not create the required folder &quot;/xxx/xxx/Desktop"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Pulka on 2007-05-11
I feel stupid. Somehow i deleted home and Desktop. I can't access to them. I get this error:

Nautilus could not create the required folder "/home/ogamico/Desktop".
Before running Nautilus, please create the following folder, or set permissions such that Nautilus can create it.

and think they're still in trash bin

---

### Post by Pulka on 2007-05-11
i'm lost here

---

### Post by Seisen on 2007-05-11
Go into the terminal and try this

```
gksudo nautilus
```

this will give nautilus super user rights,

---

### Post by Pulka on 2007-05-11
gksudo nautilus
(nautilus:10522): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by Seisen on 2007-05-11
Try ```
sudo nautilus
``` in the terminal

---

### Post by Pulka on 2007-05-11
still gives me the same error. When i try to go to "places-home folder"

---

### Post by Seisen on 2007-05-11
Which directory are you trying to make these files in.
Try this in the terminal

```
mkdir home
mkdir home/ogamico/Desktop
```

---

### Post by Pulka on 2007-05-11
yeah...had to delete the broken links first. Then mkdir.
Thank you, once again

---

### Post by Seisen on 2007-05-11
I knew something would work eventually.

---

