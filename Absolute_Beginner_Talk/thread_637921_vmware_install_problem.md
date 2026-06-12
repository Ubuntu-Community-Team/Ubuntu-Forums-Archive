---
title: "vmware install problem"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by iKonaK on 2007-12-11
[COLOR="Sienna"][B][CENTER]after i installed ubuntu and all the updates i wanted to install some other app so i went to add/remove section and i selected vmware and then pop-up said 
> VMware Player cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.
what's happened cuz i installed before and it didn't said that ? please help...[/CENTER][/B][/COLOR]

---

### Post by PhoenixP3K on 2007-12-11
When I look up VMWare in Synaptic the detailed informations says this: 
> Note: You will also need the VMware Server kernel modules to run vmware.
These can be built from source from vmware-server -kernel-source, or you
can install a pre-built vmware-server-kernel-modules package for your kernel.
It only makes mention of the VMWare server. The is an RPM version of VMWare Player 2.0.1 available on [their website]("http://download3.vmware.com/software/vmplayer/VMware-player-2.0.2-59824.i386.rpm").

---

### Post by lswest on 2007-12-11
honestly i think [Virtual Box]("www.virtualbox.org") is better than vmware, and it runs great on Ubuntu.  give it a shot:P

---

### Post by iKonaK on 2007-12-15
thanks 4 the response, i installed both vmware and virtualbox...:)

---

### Post by Paqman on 2007-12-15
VMWare server is better than the player anyway, since you can't make new VMs with the player. I'd just go ahead and install the server version through Synaptic.

---

