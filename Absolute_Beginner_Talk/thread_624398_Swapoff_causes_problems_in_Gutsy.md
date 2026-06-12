---
title: "Swapoff causes problems in Gutsy"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-11-26
I used to be able to run sudo swapoff -a; sudo swapon -a to purge the swap partition of any unnecessary data and put what is still in use back in RAM, but not with Gutsy!  Now, not always, but at least 90% or the time I'd say, it will seem to clear it, but then fail to reactivate and the system will then also start slowing down until in about 20 seconds it;s completely locked up!  What did they do to mess this up!!! :mad:

---

### Post by reidbold on 2007-11-26
no problems here. 

post the output of > tail /var/log/messages

---

### Post by ryanVickers on 2007-11-26
> Nov 26 18:58:12 ubuntu -- MARK --
Nov 26 19:14:02 ubuntu kernel: [ 5662.469018] audit(1196129642.331:20):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=7372 profile="/usr/sbin/cupsd"
Nov 26 19:14:02 ubuntu kernel: [ 5662.517789] audit(1196129642.379:21):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=7375 profile="/usr/sbin/cupsd"
Nov 26 19:38:13 ubuntu -- MARK --
Nov 26 19:50:30 ubuntu kernel: [ 7813.161144] emerald[31101]: segfault at 0000000000000004 rip 00002b2e13604521 rsp 00007fff9aa390a0 error 4
Nov 26 20:18:13 ubuntu -- MARK --
Nov 26 20:38:13 ubuntu -- MARK --
Nov 26 20:58:14 ubuntu -- MARK --
Nov 26 21:11:39 ubuntu python: hp-toolbox[9078]: warning: Reportlab not installed. Fax coverpages disabled.
Nov 26 21:19:12 ubuntu python: hp-toolbox[9147]: warning: Reportlab not installed. Fax coverpages disabled.

printer stuff - I had to just re-add my printer recently (it's on the router and the ip changed...)

---

