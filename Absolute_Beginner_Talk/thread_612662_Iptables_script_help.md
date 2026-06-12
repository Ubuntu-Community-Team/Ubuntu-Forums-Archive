---
title: "Iptables script help"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by dynamethod on 2007-11-14
hey there ive followed the iptables how to guide from here:
[https://help.ubuntu.com/community/IptablesHowTo#head-fb0be447fbc2aa413c0b27e8bfb665b7728fec7b](https://help.ubuntu.com/community/IptablesHowTo#head-fb0be447fbc2aa413c0b27e8bfb665b7728fec7b)

what im trying to accomplish is the script to load at boot up ive borrowed this script from:

[http://www.linuxguruz.com/iptables/scripts/rc.firewall_023.txt](http://www.linuxguruz.com/iptables/scripts/rc.firewall_023.txt)

however in /etc/NetworkManager/dispatch there is a file called 01ifupdown, so i pasted the iptable scipt into that and then saved and ran:

sudo chmod +x /etc/NetworkManager/dispatcher.d/01ifupdown

then rebooted

but when i run sudo iptables -L it shows no rules in the chains!?

so im doing something wrong, help much appreciated!

---

### Post by dynamethod on 2007-11-14
ive just tried:
/etc/NetworkManager/dispatcher.d$ ./01ifupdown

but it spat out:
Usage: firewall (start|stop|restart|status) EXTIF INTIF

so i tried:
firewall start ppp0 eth0

and i got:
bash: firewall: command not found


:/ stumped

---

### Post by idiotsruleintheshowerjane on 2007-11-16
ola.

the script on that link shows:
# This is the location of the iptables command
IPTABLES="/usr/sbin/iptables"

i'm  gonna guess your  box has it in /sbin/iptables  ;-)

modify  the script?

# This is the location of the iptables command
IPTABLES="/sbin/iptables"

that may not be enough, but, maybe.

j_k

---

