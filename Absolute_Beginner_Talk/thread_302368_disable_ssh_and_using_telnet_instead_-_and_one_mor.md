---
title: "disable ssh and using telnet instead - and one more Q:s ?"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by janne5011 on 2006-11-18
Hi all can someone help me do this:

1.get rid of ssh and get telnet working and so I dont at the same time get locked out from my server who is a stripped ubuntu.
(yes i know ssh is safer but server is not online)
2.how can i disable syslogd and klogd?

thanks in advance
/J

---

### Post by jpkotta on 2006-11-18
```
sudo aptitude install telnet
```

But why do you want telnet when you have ssh now?  Just make sure telnet is working before removing ssh if this is the only way to access the machine.

To stop klogd and sysklogd, use the init scripts:

```
sudo /etc/init.d/sysklogd stop
sudo /etc/init.d/klogd stop
```

To prevent them from starting at boot up, remove the symlinks in /etc/rc?.d/ that point to them:

```
sudo rm /etc/rc?.d/*klogd*
```

But, I would recommend only removing the ones in rc2.d, because that's the default runlevel.  You may want them for other runlevels for debugging purposes.

```
sudo rm /etc/rc2.d/*klogd*
```

---

### Post by janne5011 on 2006-11-18
I need the amount of RAM thats why I shall disable SSH.
Thank you for the help=)

---

