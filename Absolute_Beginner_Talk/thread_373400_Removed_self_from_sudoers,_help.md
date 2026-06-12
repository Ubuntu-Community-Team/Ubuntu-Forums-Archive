---
title: "Removed self from sudoers, help"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by muxecoid on 2007-03-01
I played with groups and permissions and mistakingly removed myself from admins group. Is there any way to rewind? Booting from CD? If so what do I need to put to /etc/fstab to mount my HDD?

---

### Post by rjfioravanti on 2007-03-01
do you have the root account enabled? if so you can do

su root

which will switch user to root, different from sudo, then as root you could fix what you messed up

---

### Post by jkeyes0 on 2007-03-01
You could always boot to recovery mode (press Escape when you see the "Grub phase 1.5" screen and select the current Kernel with "recovery mode" at the end). This puts you as root by default, and you can make changes from the command line there.

---

### Post by maniacmusician on 2007-03-01
> **jkeyes0 said:**
> You could always boot to recovery mode (press Escape when you see the "Grub phase 1.5" screen and select the current Kernel with "recovery mode" at the end). This puts you as root by default, and you can make changes from the command line there.
Yes, do as jkeyes said.

In case you need it, the command to add your user back to the admin group is "adduser [your_username] [group_name]", the [group_name] being the name of the group that you want to add the user to.

---

### Post by jkeyes0 on 2007-03-01
> **maniacmusician said:**
> Yes, do as jkeyes said.

In case you need it, the command to add your user back to the admin group is "adduser [your_username] [group_name]", the [group_name] being the name of the group that you want to add the user to.

Thanks maniac. I couldn't remember the adduser command off the top of my head (all Windows here at work, ugh).

---

### Post by maniacmusician on 2007-03-01
same here :( , all Windows. I remembered the command because I've had to use it a lot recently when I was setting up a fileserver at home :)

---

### Post by Ben Sprinkle on 2007-03-01
If you still have the root password even though you are not in with the root permissions, do this.
Reboot, when your at the GDM, press CTRL+ALT+F2 and you can do a root login. I am not sure where the permissions file is but you can
```

sudo apt-get install midnightcommander

```
Or
```

sudo apt-get install mc

```
Type mc to launch it, you can edit files it it along with browsing, other functions as well.

---

### Post by muxecoid on 2007-03-13
The problem was resolved by booting from LiveCD, mounting the partition and directly editing users file. Thank you for your help.

---

