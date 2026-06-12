---
title: "Shutting down with Xfce4"
date: 2008-04-05
forum: Arch and derivatives
---

### Post by Masteroc on 2008-04-05
Well, so far i have installed the base system of arch and finally today i had time to install xfce4 and some office stuff. The problem is that i cannot use the power button on the toolbar to shutdown or reboot. I did google and search the arch forums for a solution and i found that i was suppose to add something to my /etc/sudoers file which i did...and it still doesnt even after a logout and reboot. Here is my sudoers file for reference incase i did something wrong:

# Defaults specification

# Runas alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow people in group wheel to run all commands
# %wheel        ALL=(ALL) ALL

# Same thing without a password
# %wheel        ALL=(ALL) NOPASSWD: ALL

# Samples
# %users  ALL=/sbin/mount /cdrom,/sbin/umount /cdrom
# %users  localhost=/sbin/shutdown -h now

username ALL=(root) NOPASSWD: /usr/lib/xfsm-shutdown-helper


Any help is appreciated. Thanks!

---

### Post by kerry_s on 2008-04-05
are you sure you got the right path to xfsm-shutdown-helper

do a whereis in terminal

whereis xfsm-shutdown-helper

also the doc looks different then what you put->
[http://www.xfce.org/documentation/4.2/manuals/xfce4-session#xfsm-shutdown](http://www.xfce.org/documentation/4.2/manuals/xfce4-session#xfsm-shutdown)

---

### Post by Masteroc on 2008-04-05
Well, that is the path that was listed on the arch forums, and when i do a whereis, i get just whereis:xfsm...: on another line. I tried the line from the page that you linked still with no success.

Thanks

---

### Post by fwojciec on 2008-04-05
I think I remember reading something somewhere that in order to get xfce to shutdown properly your user needs to be in the "power" group.  It might be worth a try, in either case...

---

### Post by Masteroc on 2008-04-05
k, ill look into that

---

### Post by crimesaucer on 2008-04-05
I did the old way from the wiki with sudo and the sudoers file.

If I remeber correctly, I installed sudo, and then edited my /etc/sudoers file like this:

```
username ALL=(root) NOPASSWD: /usr/lib/xfce4/xfsm-shutdown-helper
```

so it looked like this:

```

# sudoers file.
#
# This file MUST be edited with the 'visudo' command as root.
# Failure to use 'visudo' may result in syntax or file permission errors
# that prevent sudo from running.
#
# See the sudoers man page for the details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults specification

# Runas alias specification

# User privilege specification
root	ALL=(ALL) SETENV: ALL
username ALL=(ALL) ALL
username computername=/usr/sbin/pacman
# Uncomment to allow people in group wheel to run all commands
# and set environment variables.
# %wheel	ALL=(ALL) SETENV: ALL

# Same thing without a password
# %wheel	ALL=(ALL) NOPASSWD: SETENV: ALL

# Samples
# %users  ALL=/sbin/mount /cdrom,/sbin/umount /cdrom
# %users  localhost=/sbin/shutdown -h now
username ALL=(root) NOPASSWD: /usr/lib/xfce4/xfsm-shutdown-helper


```

... the other way looks pretty easy though.

---

### Post by Masteroc on 2008-04-06
Yeap, got it working that exact way. Thanks

---

### Post by kpkeerthi on 2008-04-07
> **Masteroc said:**
> Well, so far i have installed the base system of arch and finally today i had time to install xfce4 and some office stuff. The problem is that i cannot use the power button on the toolbar to shutdown or reboot. I did google and search the arch forums for a solution and i found that i was suppose to add something to my /etc/sudoers file which i did...and it still doesnt even after a logout and reboot. Here is my sudoers file for reference incase i did something wrong:

# Defaults specification

# Runas alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow people in group wheel to run all commands
# %wheel        ALL=(ALL) ALL

# Same thing without a password
# %wheel        ALL=(ALL) NOPASSWD: ALL

# Samples
# %users  ALL=/sbin/mount /cdrom,/sbin/umount /cdrom
# %users  localhost=/sbin/shutdown -h now

username ALL=(root) NOPASSWD: /usr/lib/xfsm-shutdown-helper


Any help is appreciated. Thanks!

I had to add myself to group 'power' and the problem sorted out

[http://wiki.archlinux.org/index.php/Xfce#How_to_shutdown_and_reboot_from_Xfce](http://wiki.archlinux.org/index.php/Xfce#How_to_shutdown_and_reboot_from_Xfce)

---

