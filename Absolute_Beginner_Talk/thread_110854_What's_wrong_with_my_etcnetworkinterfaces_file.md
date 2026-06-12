---
title: "What's wrong with my /etc/network/interfaces file?"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by Jeffroooooo on 2005-12-31
Hello. I just installed Ubuntu, and I'm having a small problem. When I boot, my ethernet connection does not come up. I did a bit of poking around, and I discovered this: 

jeff@SpiffyPC:~$ sudo ifup -a
Password:
/etc/network/interfaces:28: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"

So it looks like a problem in my /etc/network/interfaces file. Here is line 28 of my /etc/network/interfaces file:

    pre-up /sbin/ifconfig eth0 up

When I sudo /sbin/ifconfig eth0 up, my ethernet connection comes up. I'm going to venture to guess that something in the boot process is executing ifup -a, and it is producing the error above. However, I haven't the slightest idea what's wrong, especially since I can execute the command manually. Any help would be greatly appreciated.

---

### Post by ape on 2006-01-01
You are misusing the pre-up directive.  From the interfaces man page:

  "pre-up command              Run command before bringing the interface up.  If this command fails then ifup aborts, refraining from marking the interface as configured, prints an error message, and exits with status 0.  This behavior  may  change  in the future."

You need to just define your interface in the /etc/network/interfaces file like this:

    iface eth0 inet dhcp   (or static if that's the way you have it configured).


The pre-up directive should only be used to do something before the interface is brought up (such as taking down a different interface or loading a driver module), not to actually bring up the interface.

---

### Post by exclipy on 2006-01-01
Can you give us some context for that line please.  The pre-up line must come after a line starting with the "iface" directive.

---

### Post by Jeffroooooo on 2006-01-01
Thanks. That was it.

Purely in the interest of blame deflection, I didn't do it.:) Well, I sort of did it, and sort of didn't. The pre-up line was put there by pppoeconf. There was already an iface section in the file.

I removed the offending pre-up, and now all is well with my ethernet card.

---

