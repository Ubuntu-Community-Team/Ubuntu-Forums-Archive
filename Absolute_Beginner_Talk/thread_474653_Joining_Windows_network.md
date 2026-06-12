---
title: "Joining Windows network"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2007-06-15
I have a belkin router with 4 wired rj45 ports and wireless, and builtin adsl modem, which usually shows up as 192.168.0.1 on Windows PCs connected to the network.

I have an old XP laptop with a PCMCIA wireless card which is connected ok to the router. It has a share on it.

My ubuntu machine can see the router ok if I ping 192.168.0.1; internet works okay.

I tried nautilus network:/// and it shows me 'Windows Network', but I can't navigate into it and see individual machines or their shares.

Ubuntu's 'Network Settings' app shows me eth0 is using dhcp

What do I have to do to get Ubuntu to talk to the Windows machines properly?

---

### Post by dolphin_oracle on 2007-06-15
Just a couple of thoughts...

Have you checked to see if there is a firewall blocking access to your XP shares.  Some, especially older, firewalls for XP block "network neighborhood" by default.   

You can also check your connection by

$ ping 192.168.xxx.xxx, where this ip address is the address of you winxp machine.

---

### Post by ecs_pf5 on 2007-06-15
Had a look on the XP machine with the shares I want to access - no third party firewall installed, and Windows own firewall not enabled.

Had a look at the router - I believed the firewall on that was only outward-facing to the internet, but I tried disabling it briefly to test, anyway. No improvement.

Currently Target XP machine is on 192.168.0.2, ubuntu machine is on 192.168.0.3, ubuntu can ping XP & XP can ping ubuntu. Both can ping the router.

I have not really looked deeply into configuring samba via the config files - I've only been playing around in the desktop GUI network tools so far.

I just got a slight improvement, I changed the launcher I've been using from

```

sudo nautilus network:///

```to

```

nautilus network:///

```and now when it comes up, it thinks for a second before finding 'Windows Network'. Then, it allows me to click on 'Windows Network' and navigate into it.. but it comes up as an empty directory labelled smb:///

just kinda hangs then

---

### Post by dolphin_oracle on 2007-06-15
is your workgroup settings the same on both machines (I believe windows default is MSHOME).  you should be able to set this in the gui network configuration somewhere ( i'm at work, and can't remember exactly where).

---

### Post by ecs_pf5 on 2007-06-15
ha! no it wasn't

I looked at smb.conf (there seems to be 2 copies - one in /usr/share/samba and one in /etc/samba) and near the top, there's a line 'workgroup='

In the copy in /etc/samba it was set to MSHOME whereas in the one in /usr/share/samba it was set to DEBIAN_something_or-other 

I set both of them to WORKGROUP (that's the name the Windows machines are using) (needed to use root priveliges to save the smb.conf files)

And now everything works HUNKY DORY!

Thanks :)

I'm hoping it might help me with my printer problem as well, that's the subject of a different thread.

---

### Post by dolphin_oracle on 2007-06-15
YEAH!

Glad you got it working!

---

