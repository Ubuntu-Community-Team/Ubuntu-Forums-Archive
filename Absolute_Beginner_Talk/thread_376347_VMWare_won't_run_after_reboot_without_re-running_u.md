---
title: "VMWare won't run after reboot without re-running /usr/bin/vmware-config.pl"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Monsieur le Comte on 2007-03-04
After running the VMWare installer script I was able to get VMWare server running.  However after a restart it won't open.  I get an error saying that "VMWare is not properly configured. Please run /usr/bin/vmware-config.pl"

Nothing has changed since my last run of it.  I will run /usr/bin/vmware-config.pl and then be able to use it.  Everything works fine.  Then, if I restart again it makes me run the vmware-config.pl script again!

I'm running this as root and can't understand why it keeps apparently losing the configuration.

Any help would be appreciated.

---

### Post by Repent on 2007-03-04
I have the same exact thing happing to me, I have asked for help with no response good luck with your request.

---

### Post by Monsieur le Comte on 2007-03-04
I'm booted in XP right now so this will have to wait for a bit for me to test, but this could be one possible solution?

> 
 Bridge Networking setup fails; Running VMware Prompts you to Run vmware-config.pl

If you attempted to enable networking during the vmware-config.pl script, and then received this message when you tried to start VMware.

vmware is installed, but it has not been (correctly) configured for this system. To (re-)configure it, invoke the following command: /usr/bin/vmware-config.pl.

Also, if you run vmware-config.pl and do not enable networking, VMware Workstation starts.

This means that you probably ran the vmware-config.pl script before running runme.pl from the vmware-any-any-update. Configuring the VMware networking support fails unless you have already applied the vmware-any-any-update.

---

### Post by Monsieur le Comte on 2007-03-04
One more possible solution from 
[http://www.linux.lu/pipermail/lilux-info/2006-December/001167.html](http://www.linux.lu/pipermail/lilux-info/2006-December/001167.html)

> 
Hi,

since this cost me some time and others might run into the
same trouble...

Context: kubuntu (here in 64bit-mode on an Athlon64 X2,
but seen also in 32bit-mode).

I'm using VMWare Player quite a lot. After a kernel upgrade,
I also had to reinstall the player - but it wouldn't properly
start, saying that I needed to run /usr/bin/vmware-config.pl
- which would fail while shutting down all services etc.

In the end, the issue is rather trivial - the installation
of the player leaves a file "/etc/vmware/not_configured"
even though everything is configured as it should be.
It is sufficient to rename or delete the file, and vmplayer
will run.

hth, Eric


---

### Post by Repent on 2007-03-06
Bump.

---

### Post by rocktorrentz on 2007-03-11
> **Monsieur le Comte said:**
> One more possible solution from 
[http://www.linux.lu/pipermail/lilux-info/2006-December/001167.html](http://www.linux.lu/pipermail/lilux-info/2006-December/001167.html)

This one worked for me. Just run the following commands in a terminal if you are still having trouble:
```

cd /etc/vmware
sudo mv not_configured not_configured.bkup

```

Then try and run vmware again; which worked perfectly for me.

---

### Post by demiurgicdaemon on 2007-03-24
> **rocktorrentz said:**
> This one worked for me. Just run the following commands in a terminal if you are still having trouble:
```

cd /etc/vmware
sudo mv not_configured not_configured.bkup

```

Then try and run vmware again; which worked perfectly for me.

This worked for me as well. Thanks!

---

### Post by upthelum on 2008-03-26
> **rocktorrentz said:**
> This one worked for me. Just run the following commands in a terminal if you are still having trouble:
```

cd /etc/vmware
sudo mv not_configured not_configured.bkup

```

Then try and run vmware again; which worked perfectly for me.

This worked for me too thanks.

---

### Post by tzd on 2008-05-14
This works for me until I reboot. Then it's back to it's original state with the same issue. 
I then have to do the same thing (rename/delete the file: not_configured) once again.
It continues like this.... Any ideas on this issue please?

---

### Post by Fatman_UK on 2008-05-15
I've looked into this a lot recently. VMware is buggy, but there are usually workarounds.

The problem is the startup script for VMware. If it fails for *any* reason, it drops this annoying zero-length file /etc/vmware/not_configured. Since it fails due to a bug on my system and not for a valid reason, I have to disable it and run the script manually. AFAICT the best resolution is to either:

a) set a cron job to delete the file every five minutes, or
b) edit the VMware startup script (/etc/init.d/vmware if my recall serves) to not drop the file.

Perhaps a) is a little too regular. Maybe every boot or every six hours would work better, I don't know. It's the solution I use anyway.

The downside with option b) is that every time you upgrade VMware, your script modification goes away.

Anyway, happy VMware-ing, folks. :)

---

### Post by muecker on 2008-07-02
I noticed in my rc*.d folders, there are links to vmware, vmware-player and vmware-server.  I'm running vmware-server so it seems that should be the only one in there..  Is it possible the reason we are having to run vmware-config.pl at every startup is due to these scripts?  Is it possible it runs all three scripts and only one succeeds and the others drop the not_configured files?

---

### Post by itsdaveperdue on 2008-07-02
Just out of curiosity is the vmware-config.pl script completing properly (e.g.: compiles the modules properly, it says they load perfectly, etc.)?

I've recently switched from VMware on my laptop to Virtualbox.  I'm not sure if it's something I did but Virtualbox seems to run much much faster than VMware did.  The networking isn't quite as easy to setup on Virtualbox (you have to configure bridging manually) and it has its quirks (snapshots work in a way that differs from VMware, and I'm just not used to it yet), but so far I'm very happy with the results.

[www.virtualbox.org]("http://www.virtualbox.org")

---

