---
title: "How to login with root privelages"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by maharajan on 2007-03-14
How do i login as root with all privileges. When i tried to install the NVIDIA graphics driver an error occured saying "Permission Denied". Also how can i change the read, write, execute permissions.

---

### Post by dstew on 2007-03-14
Use the sudo ("soo doo") command. It gives you root privleges for 5 minutes or so, so you can do administrative tasks without logging in a root.

sudo cp ~/myfile /etc/etc/

if /etc/etc/ is a system directory that requires root privleges. Sudo will ask for your password, then execute the command.

---

### Post by aysiu on 2007-03-14
There's no need to log in as root. And changing permissions on system files is a bad idea.

This will help you make changes to system files (not necessary for this task but good to know):
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

This will help you understand software installation (necessary for understanding this task):
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Read that to expand your general knowledge. Then do this (actual steps for this task).
**Step 1**. Enable extra repositories by following [these instructions](http://www.psychocats.net/ubuntu/sources).

**Step 2**. Install the drivers by pasting this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get update && sudo apt-get install nvidia-glx nvidia-kernel-common
```

---

### Post by Strider on 2007-03-14
You can do one of two things:

1) execute the command with "sudo".  i.e. "sudo <command>".  May require to enter your current password.

2) run "sudo bash", which will create a new bash instance with full root priv.  Not recommended unless you know what you're doing because you can easily remove files that are critical to the system.

To change r/w/x permissions do a "man chmod" and look at the man pages for it.  Pretty simple to use.

-Mike

---

