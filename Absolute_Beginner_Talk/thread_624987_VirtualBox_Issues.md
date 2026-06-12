---
title: "VirtualBox Issues"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by continentaltest on 2007-11-27
Have read through all prior ports regarding setup of virtualbox.  I cannot get past the vboxdrv kernel not installed error.  This script exists in etc/init.d, I have downloaded the appropriate linux-headers for my 7.10 Kubuntu version.  Have installed the virtualbox .debs from the repositories.

However, my noobhead just cannot figure out how to get the following to work:
sudo su
/etc/init.d/vboxdrv setup KERN_DIR=/usr/src/linux-headers-`uname -r`

This returns the error:
Usage: /etc/init.d/vboxdrv {start|stop|restart|status}

I've read everything seemingly related to sudo, virtualbox, etc.  What is the correct command syntax for 'setup' ?

---

### Post by master_kernel on 2007-11-27
Apparently it doesn't see "setup" as an option...

---

### Post by annda on 2007-11-27
i had a similar problem yesterday. rebooting took care of proper module installation. then all i had to do was add myself to the vboxusers group.

---

### Post by 11hjpphty76lkjj on 2007-11-27
Not sure what you are doing...you are wanting to install it? or use it?

to use it you should just need to "VirtualBox" from a terminal.  It's case sensitive.

As for installing I went to:

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

and clicked on the i385 next to Gutsy.  Works great and I love it.  great for testing.

A

---

### Post by continentaltest on 2007-11-27
Just trying to install it for testing.  Cannot get the /etc/init.d/vboxdrv to install and start.  The vboxdrv script is in /etc/init.d, but it will not start ...

enter:
sudo /etc/init.d/vboxdrv start

results in:
FATAL: Module vboxdrvdrv not found.

 * Modprobe vboxdrv failed.  Please use 'dmesg' to find out why.

but dmesg reveals nothing of use.

Thanks for any help.  Why can't I get 'sudo /etc/init.d/vboxdrv setup' to work?  How do I get the setup command to work?

---

