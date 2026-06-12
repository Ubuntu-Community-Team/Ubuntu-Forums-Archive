---
title: "xorg.conf keeps resetting"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by asakurax on 2007-08-15
Hello, I'm using Ubuntu Feisty Fawn (7.04). My xorg.conf keeps resetting itself every time I reboot, meaning my mouse and resolution configurations need to be re-set every time. This has become quite a nuisance... Anyway, this has been happening for about a week, which is very close by to the date in which I changed the format of one of my partitions, following the advice I was given on [http://ubuntuforums.org/showthread.php?t=504354&page=2](http://ubuntuforums.org/showthread.php?t=504354&page=2) (following which, I force mount one of my drives, and restart dbus every time I reboot). By the way, my X11 folder contains xorg.conf, xorg.conf.backup and xorg.conf.save, is this normal? I'm really compelled to just reinstall Ubuntu, since my Windows experience has taught me this just solves problems, but I think other people may encounter this as well, so it's much better to try and solve it. 

Many thanks in advance,
asakurax.

---

### Post by talby on 2007-08-15
One idea, get it back to your preferences then lock the file using the immutable bit:

sudo chattr +i /etc/X11/xorg.conf

then look for errors in dmesg or /var/log/messages when attempts to modify the file fail.

Reminds me of "Demolition Man"...  Just wait for the next MDK then nab 'em :)

---

### Post by Hobo Joe on 2007-08-15
Are you opening it with sudo?

---

### Post by spaznrq on 2008-02-13
> **talby said:**
> One idea, get it back to your preferences then lock the file using the immutable bit:

sudo chattr +i /etc/X11/xorg.conf

then look for errors in dmesg or /var/log/messages when attempts to modify the file fail.

Reminds me of "Demolition Man"...  Just wait for the next MDK then nab 'em :)

Ah, that command worked for me.

I had my system all setup and working on dualscreen, but everytime I restarted, I wouldn't be able to get back dualscreen because the "Virtual" line kept reverting back to what it was before.  After the line above, it works like a charm.

Thanks.

---

### Post by macogw on 2008-02-14
If you ever want to change it again, don't forget that you chattr'd it immutable.  You can make it mutable (changeable) again by repeating that command with a minus instead of a plus.

---

