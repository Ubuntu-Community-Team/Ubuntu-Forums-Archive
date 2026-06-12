---
title: "[SOLVED] Wifi Quits Working In Gusty"
date: 2007-10-22
forum: Apple Intel Users
---

### Post by czechman86 on 2007-10-22
Gusty has been running very smooth until the other day when my wifi just stopped working. At first I thought it was my router and decided to reset it, but did not test to see if it was still working with my computer, because i decided that it was bedtime and only a router problem. However, the other day, I had the same problem and decided to check my system log. Sure enough, this was found in the log:

```
Oct 22 11:36:03 macbook kernel: [ 8313.796000] wifi0: rx FIFO overrun; resetting
```

This error was repeated many times down the Kernel log. I was wondering if there are any known fixes for this or if anyone else is having the same problem. I am running a Macbook 2nd Gen with Madwifi.

I found this on another post, is this a possible fix for the problem?

```
sudo /etc/init.d/networking restart
```

Thanks for the help!

---

### Post by epaulin on 2007-10-22
This is a known bug of madwifi, use this as a work around:
[PHP]iwpriv ath0 bgscan 0[/PHP] 

see: [http://madwifi.org/ticket/1017](http://madwifi.org/ticket/1017)

---

### Post by czechman86 on 2007-10-22
> **epaulin said:**
> This is a known bug of madwifi, use this as a work around:
[PHP]iwpriv ath0 bgscan 0[/PHP] 

see: [http://madwifi.org/ticket/1017](http://madwifi.org/ticket/1017)

do i just type that code into the terminal or where do i implement it at?
thanks!

---

### Post by cyberdork33 on 2007-10-22
> **czechman86 said:**
> do i just type that code into the terminal or where do i implement it at?
thanks!

it is a terminal command.

---

### Post by czechman86 on 2007-10-23
> **cyberdork33 said:**
> it is a terminal command.

awesome! thanks! another quick question: do i enter it one time or when the wifi stalls out? thanks!

---

### Post by cyberdork33 on 2007-10-23
I don't have this hardware, but judging from what I assume it is doing, it is once (maybe once per reboot). It is basically turning off background scanning.

---

### Post by Namtabmai on 2007-10-23
I believe this gets reset on each reboot, so I popped the line into the rc.local file (/etc/rc.local), mine looks like this

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

iwpriv ath0 bgscan 0

exit 0

```

---

### Post by czechman86 on 2007-10-23
awesome guys! thanks ill pop it in there soon and it should work! thanks again!

---

### Post by cyberdork33 on 2007-10-23
> **Namtabmai said:**
> I believe this gets reset on each reboot, so I popped the line into the rc.local file (/etc/rc.local), mine looks like this

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

iwpriv ath0 bgscan 0

exit 0

```
That ought to do it!

---

