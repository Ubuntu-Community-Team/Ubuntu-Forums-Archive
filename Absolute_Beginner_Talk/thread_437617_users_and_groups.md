---
title: "users and groups"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by NAT1V3 on 2007-05-09
the one time i want to go into the user and group menu it comes up but nothing happens i have a standard window with nothing in it. how can i fix this. Ive tried resizing it restarting. Thanks, Brad

---

### Post by gradedcheese on 2007-05-09
Hi Brad.  Lets see if any errors are shown when you launch it via the terminal (Applications->Accessories->Terminal).  Enter the following, press Enter, give it the password, and then post the results here.

```

sudo users-admin

```

---

### Post by NAT1V3 on 2007-05-09
[same thing]("http://img488.imageshack.us/img488/4939/errormodifiedtp3.png")

---

### Post by gradedcheese on 2007-05-09
I don't mean the screen, what does the terminal say?  Any output/errors there?

---

### Post by NAT1V3 on 2007-05-09
no errors just app launched

---

### Post by graabein on 2007-12-22
> **gradedcheese said:**
> Hi Brad.  Lets see if any errors are shown when you launch it via the terminal (Applications->Accessories->Terminal).  Enter the following, press Enter, give it the password, and then post the results here.

```

sudo users-admin

```

I have the same problem after a reinstall of xubuntu. Kept the /home partition from an earlier install and tried setting chown and chgrp but I think I got it messed up... 

```
$ sudo users-admin
sudo: must be setuid root
```

How do I get back sudo rights for my user?

**And how do I set all files (including hidden directories and sub directories) in the old user directories to the newly created users? I keep the usernames from before.**

I did *sudo chown -R <username> ** in /home/<username> but somehow that affected the other user catalogs outside <username>!!??



I got sudo working by following [this thread]("http://ubuntuforums.org/showthread.php?t=219767") but I still got messed up user rights on my entire file system :cry:

---

### Post by graabein on 2007-12-22
OK I reinstalled xubuntu 7.10 and kept the /home partition as earlier. 

I don't have sudo rights even though **/usr/bin/sudo** and **/etc/sudoers** have root:root and my user is in the root user group. When I try to launch a sudo program nothing happens. When I try from console window it just hangs with sudo prefix... Running without sudo prefix gives me the popup message:

> **The configuration could not be loaded**
You are not allowed to access the system configuration.

Suggestions please? I wish I could install xchat and join #xubuntu or #ubuntu but installing programs requires root so... I'm stuck!

:(

---

### Post by graabein on 2007-12-25
OK here is what I did:

[LIST=1]
[*]Reinstalled Xubuntu and created a new user in process
[*]Moved previous **/home/graabein** to other location
[*]Created new user *graabein* and checked *administer the system* box
[*]Copied old user data into new **/home/graabein**
[*]**sudo chown -hR graabein:graabein /home/graabein**
[/LIST]

Working as expected right now!

:guitar:

---

