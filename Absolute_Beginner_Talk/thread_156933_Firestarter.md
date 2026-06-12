---
title: "Firestarter"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2006-04-08
Hi, I get this error.

"Failed to run /usr/sbin/firestarter as user root:
 Child terminated with 1 status"

I have read in other forums that I should "right click on the icon in the applications menu and make it gksudo"

I have two questions.

1) What if there is no "properties" when I right click.

2) Now, because there was no "properties" I uninstalled it the same way I installed it (through synaptic) and I still get the error on startup, and I have no way of finding the application in the applications menu (and even if I did, there was no "properties" choice.

---

### Post by Perfect Storm on 2006-04-08
```
sudo gedit /etc/sudoers
```

add in the buttom of the page:

**username ALL= NOPASSWD: /usr/sbin/firestarter**

where username is your login name.

```
gnome-session-properties
```

Go to startup Programs tab and click add

and add this to the command box:
**sudo firestarter --start-hidden**

---

### Post by sands on 2006-04-08
I think this is better in startup
gksudo /usr/sbin/firestarter

---

### Post by entryname on 2006-04-08
Reference using sudo to avoid needing the password for firestarter - sorry but I can't get this to work.

Firstly I see stern warnings NOT to gedit sudoers. The reason for this is apparently that dire consequences ensue if this file is wrong. The correct command, as root, is apparently visudo.  This command checks the syntax of sudoers before it is saved, and gives a warning message if it's wrong.

Unfortunately I tried editing this file as specified, and I'm afraid it didn't work. It made no difference, I'm still asked for the password. Furthermore adding firestarter to the start programs list made no difference either, it doesn't start (although it's possible this is because of the password issue).

An added complication is that using penggy firestarter needs to monitor tun0, while using gnome PPP it needs to monitor ppp0. It can't work this out, and there isn't even a command option to set it, I need to run the wizard and select from the list every time I change from one to the other. I should also add firestarter is supposed if configured that way to start automatically on dialup, but that doesn't work either and never has done, though again it may be because of the password issue.

I've lost all confidence in editing sudoers :( why doesn't it work??

sudoers:
> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL
michael	ALL= NOPASSWD: /usr/sbin/firestarter

# Members of the admin group may gain root privileges
%admin	ALL=(ALL) ALL

dmesg (extract)
> [  156.264671] IPv6 over IPv4 tunneling driver
[ 1628.723281] tun: Universal TUN/TAP device driver, 1.6
[ 1628.723325] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[ 1710.080032] ip_tables: (C) 2000-2002 Netfilter core team
[ 1710.248371] ip_conntrack version 2.1 (1536 buckets, 12288 max) - 248 bytes per conntrack


---

### Post by entryname on 2006-04-09
OK this is going to be very brief - 

for the sudo no password trick to work that line has to be last in the sudoers file

effective firewall can be obtained by starting firestarter and once it is going using iptables-save > (file) to save the configuration. A script can then be written to use iptables-restore < (file) to apply that configuration, and then use the appropriate dial-up tool (gnome-ppp, penggy, etc). That script can then be run using a launcher from the desktop thus making the whole business invisible to the user. This means firestarter only needs to be used once (to write the iptables configuration) and isn't needed at all after that. For this to work without a password, iptables-restore does of course have to be named in sudoers (command visudo) as not requiring a password, which some will see as a security risk they would rather avoid.

I'm going to assume nobody needs to know any more unless someone posts and says they do.

cor all this sounds very technical, I'm quite impressed myself :KS posted here as that's where I found the firestarter thread

---

