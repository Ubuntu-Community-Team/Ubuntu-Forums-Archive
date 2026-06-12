---
title: "Problems upgrading 7.10 to 8.04"
date: 2008-09-25
forum: Apple Hardware Users
---

### Post by seeker1458 on 2008-09-25
I was triple-booting OS X 10.4, XP Pro SP2, and Gutsy.  I am using rEFIt as a boot manager.  I decided to go ahead and upgrade 7.10 to Hardy, and everything went seemingly fine.  It asked to overwrite some customized files, and I kept the original b/c I remember having to change some stuff to get WPA2 to work with the wireless.  Everything finished and asked to reboot.

Upon Reboot I now have the following choices after selecting Linux at the rEFIt screen:
```
Ubuntu 8.04.1, Kernel 2.6.24-19-generic
Ubuntu 8.04.1, Kernel 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.1, Kernel 2.6.22-14-generic
Ubuntu 8.04.1, Kernel 2.6.22-14-generic (recovery mode)
Ubuntu 8.04.1, memtest86+
Other operating systems:
Microsoft Windows XP Professional
```

After selecting either one of the kernel verions (this happens regardless of which one i select) I am brought to the login screen.  I log in, and the system just sits there at the tan background with nothing on it.  After about 30 seconds a blank white window pops up in the left hand corner.  After another 5 or so minutes the desktop loads and the window that was blank gives the following message:

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

```
The last error message was:

Did not recieve a reply.  Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
```

What do I need to do to resolve this issue?  I've searched the web, and found people with similar problems...but no fix.

---

### Post by cyberdork33 on 2008-09-25
looks like something broke in the upgrade. Such breakage is not uncommon after an upgrade. It could be a variety of things.

---

### Post by seeker1458 on 2008-09-25
i just did a fresh install

---

