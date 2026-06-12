---
title: "Any way to repair a broken installation?"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by vinitlee on 2007-03-04
Well, I tried to update my system from dapper to edgy by means of chaning all occurences of "dapper" to "edgy" in /etc/apt/sources.list, then running "sudo apt-get dist-upgrade".

It installed most of the packages, but, apparently, some failed.

Now, when I boot, my X server is unable to run at all, and shows me a blueish window which can give me info. If I try to log in on a tty, it gives be a consistent error and does not resolve.

Is there any way I can replace the system files, restoring them back to the defaults of dapper? Would this work? Are there any other solutions?

Any and all help appreciated.

---

### Post by taurus on 2007-03-04
Can you at least boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
If you are not sure about a question, just use the default and pick **vesa** as a driver for your graphic card.  Then reboot and see what happens to X.

```
shutdown -r now
```

---

### Post by vinitlee on 2007-03-04
I tried the top solution, but it told me:

```
xserver-xorg is broken or not fully installed.
```

Also, a bunch of other ncurses errors show up in the booting process. I believe this is not simply restricted to the X server.

Do you know of any way, posssible via apt, that I could dl the dapper versions of the files that I downloaded in edgy form, so as to revert back to previous installation? Would such a downgrade be accepted by apt?

---

