---
title: "Yaboot Fails At First Reboot During Breezy Install"
date: 2005-10-07
forum: Apple PPC Users
---

### Post by billg_g on 2005-10-07
I'm seeing yaboot fail at the first reboot during an install of yesterday's Breezy release on a Mac Mini with an external Firewire drive.

I'm not trying to boot from the Firewire drive. The newworld bootstrap partition is located on the Mini's drive, in a second small partition after the initial partition used by OS X.  Everthing else Linux sees is on the Firewire drive.

The install is free of problems until the initial reboot. At that point, selecting the Linux option presented by yaboot produces this message: "Loading second stage bootstrap...".  At that point the reboot doesn't happen and yaboot displays this: "syntax error near line 10 in file \\yaboot.conf". 

I've done two fresh installs with identical results. At the end of the second install, I opted to shell out and take a look.  /etc/yaboot.conf appeared to be OK, with no obvious errors. Line 10 sets yaboot up to boot /boot/vmlinux, which is right where it should be. 

OS X boots fine, which is what I'm using now.

Has anyone else seen this?  How can I fix it? (I've tweedled around a few lilo files, but this PPC stuff is new to me.)

---

