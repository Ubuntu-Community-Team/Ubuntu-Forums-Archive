---
title: "Gutsy 7.10 release -  iBook G4 Installation Issues"
date: 2007-10-21
forum: Apple PPC Users
---

### Post by Mattyb_uk on 2007-10-21
Hi

I downloaded the Gutsy PPC Release and installed from disk. Just before I continue, 
I want to thank the Community for 7.10. I actually bought and repaired a G4 for Ubuntu alone.

I have a G4 1.42ghz iBook - 07/2005 revision.

So far, I've had some major issues with the installation. Let me know if you've had the same. I've got no idea where to report these bugs, so please help!

- OpenOffice completely breaks the system
                   - Upon reboot - the cpu is running at 100% - the fan is blowing on full
                  - The Gnome network manager is broken - no network connections are      available even though iwconfig brings up both the ethernet and wifi connections.

- MPlayer breaks the system too, The binary doesn't work, and the system exhibits the same symptoms as above.

- Is there a library that's doing that? I'm not sure how to bug report etc? Can anyone help?


- Sources aren't available. These ones to be precise:

[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/main/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/main/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/restricted/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/restricted/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/universe/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/universe/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/multiverse/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/multiverse/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/main/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/main/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/restricted/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/restricted/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/universe/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/universe/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/multiverse/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/multiverse/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/main/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/main/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/restricted/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/restricted/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/universe/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/universe/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/multiverse/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/multiverse/source/Sources.gz:) 404 Not Found

Any idea where to repoint the sources to?

matt

---

### Post by Auria on 2007-10-21
You can report bugs to (i believe) [https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

PS : i have no idea whether you're new to ubuntu on PPC, but if you are, know that version 7.04 has been reported to work much better than 7.10 for the vast majority of people on PPC

---

### Post by Mattyb_uk on 2007-10-21
Hey

I've been running 7.04 for the last month, but got a little frustrated with the workarounds for gnash, network-manager, compiz etc. and wanted them to work.

So I've installed the GStreamer plugins just now and it's exhibited the same problem. 100% cpu usage, and no cards detected by Network Manager.

Turns out Network manager is chewing up the cpu, so I've removed it and the cpu usage is normal.

But I've got no network :-(

---

### Post by Mattyb_uk on 2007-10-22
**Update**

- Removed Network-Manager and manually configured the network using System > Admin > Network instead.

We're back on!

I've raised a bugticket too for the Network-Manager problem. 

[https://bugs.launchpad.net/ubuntu/+bug/155556](https://bugs.launchpad.net/ubuntu/+bug/155556)

I went and got Network-Manager and Network-Manager-Gnome from Debian testing instead and installed those with success.
(need to do a slight fix after installing Network-Manager-Gnome)

Got a couple of other things I've noticed.

Banshee - Install through Synaptic. Fails to initialise.. Bug has been raised in debian. apparently in mono-gtk

MPlayer - Install through Synaptic. Crashes with a debug error. I'll get the output and post it here.

---

