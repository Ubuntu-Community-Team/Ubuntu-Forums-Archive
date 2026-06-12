---
title: "what is wrong with this bash script (pls help)"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by dr_d on 2007-01-14
i have a bash script (/etc/init.d/iptables) to start and stop my firewall. i found it on the net back when i was using hoary.. i checked it for bugs then and i didn't find any then. recently i've found a small bug in it so maybe it's something to do with the fact that i'm now using edgy, or maybe this bug was there the whole time.

anyways i really depend on this script and any help fixing it would be greatly appreciated.


so the script takes any one of these arguments: {start|stop|restart|save}.. everything works fine except for if i pass "stop" as the parameter.. the output should be:

```
Stopping firewall.
```

however the output i get is:

```
Stopping firewall[: 88: ==: unexpected operator
[: 88: ==: unexpected operator
[: 88: ==: unexpected operator
.
```


ok so i've located the code which is called when the script is called with "stop":

```
stop)
if [ "${SAVE_ON_STOP}" = "yes" ]; then
save || exit 1
fi
echo -n "Stopping firewall"
for a in `cat /proc/net/ip_tables_names`; do
/sbin/iptables -F -t $a
/sbin/iptables -X -t $a

if [ $a == nat ]; then
/sbin/iptables -t nat -P PREROUTING ACCEPT
/sbin/iptables -t nat -P POSTROUTING ACCEPT
/sbin/iptables -t nat -P OUTPUT ACCEPT
elif [ $a == mangle ]; then
/sbin/iptables -t mangle -P PREROUTING ACCEPT
/sbin/iptables -t mangle -P INPUT ACCEPT
/sbin/iptables -t mangle -P FORWARD ACCEPT
/sbin/iptables -t mangle -P OUTPUT ACCEPT
/sbin/iptables -t mangle -P POSTROUTING ACCEPT
elif [ $a == filter ]; then
/sbin/iptables -t filter -P INPUT ACCEPT
/sbin/iptables -t filter -P FORWARD ACCEPT
/sbin/iptables -t filter -P OUTPUT ACCEPT
fi
done
start-stop-daemon --stop --quiet --pidfile /var/run/iptables.pid --exec /sbin/iptables
echo "."
;;
```


so what could be the unexpected operator? i can post the whole script (it's not very big) if need be.

btw: SAVE_ON_STOP is always set to "no".. 

any ideas?

---

### Post by ciscosurfer on 2007-01-14
> **dr_d said:**
> i have a bash script (/etc/init.d/iptables) to start and stop my firewall. i found it on the net back when i was using hoary.. i checked it for bugs then and i didn't find any then. recently i've found a small bug in it so maybe it's something to do with the fact that i'm now using edgy, or maybe this bug was there the whole time.

anyways i really depend on this script and any help fixing it would be greatly appreciated.


so the script takes any one of these arguments: {start|stop|restart|save}.. everything works fine except for if i pass "stop" as the parameter.. the output should be:

```
Stopping firewall.
```however the output i get is:

```
Stopping firewall[: 88: ==: unexpected operator
[: 88: ==: unexpected operator
[: 88: ==: unexpected operator
.
```
ok so i've located the code which is called when the script is called with "stop":

```
stop)
if [ "${SAVE_ON_STOP}" = "yes" ]; then
save || exit 1
fi
echo -n "Stopping firewall"
for a in `cat /proc/net/ip_tables_names`; do
/sbin/iptables -F -t $a
/sbin/iptables -X -t $a

if [ $a == nat ]; then
/sbin/iptables -t nat -P PREROUTING ACCEPT
/sbin/iptables -t nat -P POSTROUTING ACCEPT
/sbin/iptables -t nat -P OUTPUT ACCEPT
elif [ $a == mangle ]; then
/sbin/iptables -t mangle -P PREROUTING ACCEPT
/sbin/iptables -t mangle -P INPUT ACCEPT
/sbin/iptables -t mangle -P FORWARD ACCEPT
/sbin/iptables -t mangle -P OUTPUT ACCEPT
/sbin/iptables -t mangle -P POSTROUTING ACCEPT
elif [ $a == filter ]; then
/sbin/iptables -t filter -P INPUT ACCEPT
/sbin/iptables -t filter -P FORWARD ACCEPT
/sbin/iptables -t filter -P OUTPUT ACCEPT
fi
done
start-stop-daemon --stop --quiet --pidfile /var/run/iptables.pid --exec /sbin/iptables
echo "."
;;
```
so what could be the unexpected operator? i can post the whole script (it's not very big) if need be.

btw: SAVE_ON_STOP is always set to "no".. 

any ideas?Post the whole script.  I have some ideas but need to see the *entire* script.  I believe it has to do with which shell you are calling.  Post your entire script and I can help you. :-)

---

### Post by dr_d on 2007-01-14
Okay here is the entire script:

```
#!/bin/sh
#
#This is a ubuntu adapted iptables script from gentoo
#(http://www.gentoo.org) which was originally distributed
# under the terms of the GNU General Public License v2
#and was Copyrighted 1999-2004 by the Gentoo Foundation
#
#This adapted version was intended for and ad-hoc personal
#situation and as such no warranty is provided.

IPTABLES_SAVE="/etc/default/iptables-rules"
SAVE_RESTORE_OPTIONS="-c"
SAVE_ON_STOP="no"

checkrules() {
if [ ! -f ${IPTABLES_SAVE} ]
then
echo "Not starting iptables. First create some rules then run"
echo -n "\"/etc/init.d/iptables save\""
return 1
fi
}

save() {
echo -n "Saving iptables state"
/sbin/iptables-save ${SAVE_RESTORE_OPTIONS} > ${IPTABLES_SAVE}
}

start(){
checkrules || return 1
echo "Loading iptables state and starting firewall"
echo -n "Restoring iptables ruleset"
start-stop-daemon --start --quiet --exec /sbin/iptables-restore -- ${SAVE_RESTORE_OPTIONS} < ${IPTABLES_SAVE}
}

case "$1" in
save)
save
echo "."
;;

start)
start
echo "."
;;
stop)
if [ "${SAVE_ON_STOP}" = "yes" ]; then
save || exit 1
fi
echo -n "Stopping firewall"
for a in `cat /proc/net/ip_tables_names`; do
/sbin/iptables -F -t $a
/sbin/iptables -X -t $a

if [ $a == nat ]; then
/sbin/iptables -t nat -P PREROUTING ACCEPT
/sbin/iptables -t nat -P POSTROUTING ACCEPT
/sbin/iptables -t nat -P OUTPUT ACCEPT
elif [ $a == mangle ]; then
/sbin/iptables -t mangle -P PREROUTING ACCEPT
/sbin/iptables -t mangle -P INPUT ACCEPT
/sbin/iptables -t mangle -P FORWARD ACCEPT
/sbin/iptables -t mangle -P OUTPUT ACCEPT
/sbin/iptables -t mangle -P POSTROUTING ACCEPT
elif [ $a == filter ]; then
/sbin/iptables -t filter -P INPUT ACCEPT
/sbin/iptables -t filter -P FORWARD ACCEPT
/sbin/iptables -t filter -P OUTPUT ACCEPT
fi
done
start-stop-daemon --stop --quiet --pidfile /var/run/iptables.pid --exec /sbin/iptables
echo "."
;;

restart)
echo "Flushing firewall"
for a in `cat /proc/net/ip_tables_names`; do
/sbin/iptables -F -t $a
/sbin/iptables -X -t $a
done;
start
echo "."
;;
*)
echo "Usage: /etc/init.d/iptables {start|stop|restart|save}" >&2
exit 1
;;
esac

exit 0
```



I've also managed to narrow it down and find the three lines which are causing errors. They are:
>> if [ $a == nat ]; then
>> elif [ $a == mangle ]; then
>> elif [ $a == filter ]; then

now the 'a' variable is set in 
>> for a in `cat /proc/net/ip_tables_names`; do

i looked at what is in /proc/net/ip_tables_names, and the contents is just "filter". this makes sense because i have only used this table in my firewall rules.

that said, i can't see what is causing the error... but then again i don't know bash script so i probably wouldn't pick up even a syntax error...

cheers!

---

### Post by ciscosurfer on 2007-01-14
> **dr_d said:**
> Okay here is the entire script:

```
#!/bin/sh
#
#This is a ubuntu adapted iptables script from gentoo
#(http://www.gentoo.org) which was originally distributed
# under the terms of the GNU General Public License v2
#and was Copyrighted 1999-2004 by the Gentoo Foundation
#
#This adapted version was intended for and ad-hoc personal
#situation and as such no warranty is provided.

IPTABLES_SAVE="/etc/default/iptables-rules"
SAVE_RESTORE_OPTIONS="-c"
SAVE_ON_STOP="no"

checkrules() {
if [ ! -f ${IPTABLES_SAVE} ]
then
echo "Not starting iptables. First create some rules then run"
echo -n "\"/etc/init.d/iptables save\""
return 1
fi
}

save() {
echo -n "Saving iptables state"
/sbin/iptables-save ${SAVE_RESTORE_OPTIONS} > ${IPTABLES_SAVE}
}

start(){
checkrules || return 1
echo "Loading iptables state and starting firewall"
echo -n "Restoring iptables ruleset"
start-stop-daemon --start --quiet --exec /sbin/iptables-restore -- ${SAVE_RESTORE_OPTIONS} < ${IPTABLES_SAVE}
}

case "$1" in
save)
save
echo "."
;;

start)
start
echo "."
;;
stop)
if [ "${SAVE_ON_STOP}" = "yes" ]; then
save || exit 1
fi
echo -n "Stopping firewall"
for a in `cat /proc/net/ip_tables_names`; do
/sbin/iptables -F -t $a
/sbin/iptables -X -t $a

if [ $a == nat ]; then
/sbin/iptables -t nat -P PREROUTING ACCEPT
/sbin/iptables -t nat -P POSTROUTING ACCEPT
/sbin/iptables -t nat -P OUTPUT ACCEPT
elif [ $a == mangle ]; then
/sbin/iptables -t mangle -P PREROUTING ACCEPT
/sbin/iptables -t mangle -P INPUT ACCEPT
/sbin/iptables -t mangle -P FORWARD ACCEPT
/sbin/iptables -t mangle -P OUTPUT ACCEPT
/sbin/iptables -t mangle -P POSTROUTING ACCEPT
elif [ $a == filter ]; then
/sbin/iptables -t filter -P INPUT ACCEPT
/sbin/iptables -t filter -P FORWARD ACCEPT
/sbin/iptables -t filter -P OUTPUT ACCEPT
fi
done
start-stop-daemon --stop --quiet --pidfile /var/run/iptables.pid --exec /sbin/iptables
echo "."
;;

restart)
echo "Flushing firewall"
for a in `cat /proc/net/ip_tables_names`; do
/sbin/iptables -F -t $a
/sbin/iptables -X -t $a
done;
start
echo "."
;;
*)
echo "Usage: /etc/init.d/iptables {start|stop|restart|save}" >&2
exit 1
;;
esac

exit 0
```I've also managed to narrow it down and find the three lines which are causing errors. They are:
>> if [ $a == nat ]; then
>> elif [ $a == mangle ]; then
>> elif [ $a == filter ]; then

now the 'a' variable is set in 
>> for a in `cat /proc/net/ip_tables_names`; do

i looked at what is in /proc/net/ip_tables_names, and the contents is just "filter". this makes sense because i have only used this table in my firewall rules.

that said, i can't see what is causing the error... but then again i don't know bash script so i probably wouldn't pick up even a syntax error...

cheers!Just as I suspected: you are calling /bin/sh which in Edgy points to /bin/dash and you want it to point to /bin/bash

So to fix this, simply change your first line from```
#!/bin/sh
```to```
#!/bin/bash
```Enjoy!

---

### Post by ciscosurfer on 2007-01-14
Of course you could always install Firestarter (a GUI frontend for iptables) that will take care of all of this for you (automatically).  You'll need to enable your Universe repo to install Firestarter. :-)

---

### Post by dr_d on 2007-01-14
sweet that fixed it.:p 

as for firestarter, for some reason i prefer to work with raw iptables rules (dont ask me why).


anyway thanks a lot for helping me out of that one.

cheers!

---

### Post by ciscosurfer on 2007-01-14
> **dr_d said:**
> sweet that fixed it.:p 

as for firestarter, for some reason i prefer to work with raw iptables rules (dont ask me why).


anyway thanks a lot for helping me out of that one.

cheers!Absolutely!  Glad I could be of service!

---

### Post by bullgr on 2007-04-15
thank's ciscosurfer...

this is the solution i searched about the last two hours...

thank's again... ):P

---

### Post by ciscosurfer on 2007-04-15
> **bullgr said:**
> thank's ciscosurfer...

this is the solution i searched about the last two hours...

thank's again... ):PSure thing :-)

---

