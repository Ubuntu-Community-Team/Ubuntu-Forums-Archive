---
title: "vmware server conflicts vmware-player"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by pcomelade on 2007-03-14
Hi all,

I'm having an annoying problem with vmware. A couple of months ago I installed vmware server, and everything went fine. Some days ago I decided to install vmware-player, because the server eats me a lot of memory. The problem is that when I reboot the machine, none of them (server nor player) can start. Seems to be an incompatibility problem between the two.
Now, even if I unninstall vmware-player the server doesn't start.

When I stop it:
$ /etc/init.d/vmware stop
Stopping VMware services:
   Virtual machine monitor                                             done
/etc/init.d/vmware: 766: /usr/lib/vmware-player/net-services.sh: not found
   Virtual ethernet                                                    done

Why is it looking vmware-player archives? I did remove the player!

When I try to start it:
/etc/init.d/vmware start
VMware Server is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

No matter if I run again the /usr/bin/vmware-config.pl script, when I try to start vmware I'm getting always the same answer:
VMware Server is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

Any idea on what is going on??
Thanks in advance!

M;

---

### Post by irish_flu on 2007-03-14
I would reinstall VMWare Server.

---

### Post by pcomelade on 2007-03-14
Thanks, already did it. But when I run again the /usr/bin/vmware-config.pl script, I get always the same answer:

VMware Server is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

M;

---

### Post by pcomelade on 2007-03-14
Finally it seems that I solved the problem unninstalling vmware server and **manually** eliminating all the configurations files (both of the server and the player). After doing that I re-installed vmware server. And now, the server seems to work properly

Cheers!

M;

---

### Post by alextj on 2007-03-22
Can you tell what config files have you removed?
I have the same problem and I can't seem to get it to work anymore.
I have uninstalled both player and server, removed /etc/vmware.
Reinstalled server, but I still get this "vmware is installed, but it has not been (correctly) configure..." stuff.

---

### Post by genti on 2007-03-29
check this forum if you haven't already.

remove the file /etc/vmware/not_configured
It is probably there by default because of the player.

---

