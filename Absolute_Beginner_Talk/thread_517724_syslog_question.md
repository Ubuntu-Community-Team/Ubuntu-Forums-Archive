---
title: "syslog question"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Miguellint on 2007-08-04
Hi all....I've removed "quiet splash" from menu.lst and now when the computer boots up I get to see what's starting up (I think this is called Upstart)

However as all the lines race by too fast to read I wondered is the file /var/log/syslog a record of Upstart. If not, is there a boot log kept anywhere.

Many thanks
Miguel

---

### Post by nitro_n2o on 2007-08-05
there are all sorts of log files in /var/log/ 
have a look at them try this out 
```
tail /var/log/bootstrap.log
```
or /var/log/boot
to actively monitor a log use (for example)
```
tail -f /var/log/syslog 
```

---

### Post by nitro_n2o on 2007-08-05
one more thing 
```
cat /var/log/syslog | grep upstart 
```
will tell you if upstart in syslog or not

---

### Post by nick_h on 2007-08-05
You can also use System->Administration->System Log to view log files.

---

### Post by dreadlord_chris on 2007-08-05
> **Miguellint said:**
> Hi all....I've removed "quiet splash" from menu.lst and now when the computer boots up I get to see what's starting up (I think this is called Upstart)

However as all the lines race by too fast to read I wondered is the file /var/log/syslog a record of Upstart. If not, is there a boot log kept anywhere.

Many thanks
Miguel

syslog is kind of a system-wide catch-all log file - many system entries end up here, not just boot messages...

```

dmesg > boot.log

```
will dump the current kernel ring-buffer (boot messages) to a file that you can examine to your heart's content....

---

### Post by Miguellint on 2007-08-22
Thanks all for the replies :-)

Miguel

---

