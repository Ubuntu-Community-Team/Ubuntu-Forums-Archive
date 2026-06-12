---
title: "Can't print from mac to server after upgrade to 10.04.1"
date: 2010-09-20
forum: Apple Hardware Users
---

### Post by p2ranger on 2010-09-20
I recently updated my server from 9.04 to 10.04.1

Previously, my two macs running snow leopard were able to connect to the server and print with no problem. Now they won't print. I can print a test page through CUPS web interface and my Ubuntu 10.04.1 laptop will print to the server.

I noticed a difference in Gutenprint that went from v5.2.3 to v5.2.5. At least that was the difference I saw between what the CUPS web interface was showing and what driver I had to choose from when adding a printer on the mac said. I updated the gutenprint drivers to 5.2.5 on the mac.

I've uninstalled CUPS 1.4.3, reinstalled it, deleted the printer, added it again. This is the error I get in the mac when I try to print:

Tree connect failed (NT_STATUS_BAD_NETWORK_NAME)

The print job says its printing, never does, and eventually shows its paused.

The printer is an HP Laserjet 1022

I'm at a loss and can't figure out what to do next. Thanks for any help

Jason

---

### Post by Morbius1 on 2010-09-20
Since you're using samba to print there is a bug in Ubuntu that causes cups to start after samba starts instead of the other way around. 

Restart the two services in the correct order and see if your mac can access the printer:
```
sudo service cups restart
```
```
sudo service smbd restart
```

---

### Post by p2ranger on 2010-09-20
WOW!

That worked! Thank you SO much!

The only thing is if I reboot the server, I have to do that command again. Is there a way to fix so I won't have to run those commands after a reboot?

Thanks again

Jason

---

### Post by Morbius1 on 2010-09-20
.

---

### Post by Morbius1 on 2010-09-20
Here's the fix from the bug report ( look for the "patch" icon ): [https://bugs.launchpad.net/ubuntu/lucid/+source/upstart/+bug/494141](https://bugs.launchpad.net/ubuntu/lucid/+source/upstart/+bug/494141)

Edit /etc/init/smbd.conf as root:
```
gksu gedit /etc/init/smbd.conf
```and change this:
> description "SMB/CIFS File Server"
author "Steve Langasek <steve.langasek@ubuntu.com>"

[COLOR=Blue] start on local-filesystems[/COLOR]
stop on runlevel [!2345]

respawn

pre-start script
RUN_MODE="daemons"

[ -r /etc/default/samba ] && . /etc/default/samba

[ "$RUN_MODE" = inetd ] && { stop; exit 0; }

install -o root -g root -m 755 -d /var/run/samba
end script

exec smbd -FTo this:
> description "SMB/CIFS File Server"
author "Steve Langasek <steve.langasek@ubuntu.com>"

[COLOR=Blue] start on (local-filesystems and stopped rc)[/COLOR]
stop on runlevel [!2345]

respawn

pre-start script
RUN_MODE="daemons"

[ -r /etc/default/samba ] && . /etc/default/samba

[ "$RUN_MODE" = inetd ] && { stop; exit 0; }

install -o root -g root -m 755 -d /var/run/samba
end script

exec smbd -F 

---

### Post by p2ranger on 2010-09-20
Great!

Thanks again

Jason

---

### Post by debili on 2010-09-24
still facing the same issue; 
I can add the printer on the mac via  Windows tab in the Add Printer dialog but a page never arrives to the  printer(connected to ubuntu). after applaying the changes to/etc/init/smbd.conf my network shares became unaccessible

i've got 2 ethernet cards on my ubuntu box, one for the internet connection, the second one connects/shares the internet to ma SL iMac

please do you have any suggestions for me?

---

### Post by debili on 2010-09-28
is there any way to re-configure printer sharing back to defaults ?

---

### Post by p2ranger on 2010-09-28
I'm not home right now, but samba stopped working on me right before I left for a trip. Therefor my printer nor my folder shares  work with my macs right now. So, I don't know if I'll be much help. I've reinstalled samba, but nothing shows up still. Can't work on it really from here either.

Jason

---

