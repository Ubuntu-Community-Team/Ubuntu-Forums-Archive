---
title: "best debian based server distro?"
date: 2011-10-24
forum: Any Other OS
---

### Post by cortman on 2011-10-24
We're thinking about replacing our data storage and Exchange servers at the small business I'm employed at. There was talk about switching to Unix servers for better reliability (Windows Server2003 is REALLY lame). I'm not on the IT committee or anything, but I thought I'd ask around, just for curiosity. Anyone have any opinions?

---

### Post by Lars Noodén on 2011-10-24
For servers, I'd recommend plain Debian Stable.  It's got all the packages and a long, stable release cycle which means no surprises.  Plus you can always use [s]APT-Pinning[/s] backports if you need a newer version of a package.

---

### Post by Lars Noodén on 2011-10-24
For a replacement for the mail-calendar combo, you can look at [Kolab](http://kolab.org/) and [Citadel](http://www.citadel.org/).  Both do the job well.

---

### Post by kaldor on 2011-10-24
Ubuntu LTS (10.04 right now) or Debian Stable gets my vote. 

If you want a more traditional Linux server, try Scientific Linux 6 (free clone of RHEL and faster updates than CentOS).

---

### Post by T.J. on 2011-10-24
@Cortman:  To replace Exchange, I'd suggest the Postfix Mail agent with LDAP and SPF enabled.  For generic datastorage over a network Samba can interface with Windows well.  Samba is meant specifically for file and folder sharing with Windows Networking.



@Lars:   I agree, Debian Stable is by far one of the better choices for Linux servers hands down, but with respect - you should never use APT pinning on a server.

> **Lars Noodén said:**
> For servers, I'd recommend plain Debian Stable.  It's got all the packages and a long, stable release cycle which means no surprises.  Plus you can always use APT-Pinning if you need a version of a package from Testing.

(To those not familiar with Debian, APT pinning is the process where you can "mix and match" packages from any of the Debian versions (Stable, Testing, Unstable, or Experimental) based on a priority you decide.  While it is generally not harmful, and you CAN rollback, it's not officially supported because you can end up with a mixed setup of packages from versions that lack timely security patches. )

Debian Stable packages are no older than RHELs, despite Debian Stable's reputation for "being old". Debian Testing packages were never meant to be used in the world of servers. They do not receive patches as quickly as Debian Stable or Unstable.  Debian explains this quite clearly.  Testing is literally for testing only.

There is an alternative instead of using Debian Testing or Unstable if you absolutely must have a newer package. You can use Debian Backports instead.  Debian Backports gives you updated software - even between releases of Debian and avoids the problems associated with APT pinning and security patches.

---

