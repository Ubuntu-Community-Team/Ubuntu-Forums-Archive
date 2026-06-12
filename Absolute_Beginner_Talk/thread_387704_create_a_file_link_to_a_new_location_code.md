---
title: "create a file link to a new location code"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Draddy on 2007-03-18
I was following this script trying to get my dyndns updater to start at startup, and at step 5 and can't find the code to copy a file link....

I would greatly appreciate the help!

> iknopf wrote:
Adding @reboot /usr/sbin/inadyn to crontab didn't work for me - it just gives me an error message.

This is how I did it (in Ubuntu 6.10):

1. Create the /etc/inadyn.conf file using the previous instructions.
2. Create a file named inadyn in /etc/init.d containing the following:

#!/bin/sh
case "$1" in
start)
/user/sbin/inadyn
;;
stop)
;;
*)
echo @"Usage: $0{start}"
exit 1
esac
exit 0

3. Make the file executable - chmod 755 /etc/init.d/inadyn
4. cd to /etc/rc2.d
[B]5. Create a link to the /etc/init.d/inadyn file
ln -s ../init.d/inadyn S30inadyn
[/B]
When you reboot inadyn should start automatically

---

### Post by dbbolton on 2007-03-18
```
$ cd /etc/rc2.d
$ ln -s /etc/init.d/inadyn S30inadyn
```

is that what you already tried ?

---

### Post by Draddy on 2007-03-18
nope! didn't know the LN part.

thanks a ton!

---

### Post by Draddy on 2007-03-18
on a second note, 

how do I see if it is actually doing anything? is it updating my IP address?

---

### Post by turok40 on 2007-05-09
I use the following parameters as well, to have it display nothing and just put it in a log file:

--background --log_file /home/#USERNAME#/inadyn.log

The log file never grows to more than like 3 lines.  States that there is a change; Update needed; Update successful.

Hope it helps.

---

