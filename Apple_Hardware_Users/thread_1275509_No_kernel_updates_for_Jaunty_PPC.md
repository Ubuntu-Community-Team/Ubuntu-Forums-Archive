---
title: "No kernel updates for Jaunty PPC?"
date: 2009-09-25
forum: Apple Hardware Users
---

### Post by sweetleaf on 2009-09-25
It looks to me like there are no kernel updates in the repositories for Jaunty PPC. My iMac is still running kernel 2.6.28-6 (#20), from April. I think I have a good [FONT="Courier New"]sources.list[/FONT] file (see below), because I've received dozens of package upgrades from jaunty-security and jaunty-updates. However, I haven't gotten any for the kernel.          

Is anyone else running a more recent kernel on PPC? Do you think I might have something wrong in my setup?

I have a theory about this, which may well be *completely wrong*, since I'm basically brand new to Linux. But it seems like this is probably one result of losing official PPC support from Canonical. The upstream kernel maintainers only apply security and bug patches to the most recent development [version]("http://en.wikipedia.org/wiki/Linux_kernel#Versions") (currently [2.6.31]("http://kernel.org")). So, the distributions have to hack their own patches for people using older kernels (like 2.6.28, for Jaunty).

For most packages, the community PPC maintainers can probably just grab an upstream update and compile it for PPC. But applying patches to older kernel versions may require more tweaking, and I'm guessing that the community lacks the resources to do this. Canonical is no longer doing it for PPC, as you can see from the packages listed in their most recent [kernel]("http://www.ubuntu.com/usn/usn-793-1") [security]("http://www.ubuntu.com/usn/usn-807-1") [notices]("http://www.ubuntu.com/usn/usn-819-1"). (They DO appear to be releasing PPC kernel updates for 8.04, which is a nice surprise. As far as I had read, 6.10 was supposed to be the last officially supported PPC version.)

Does this sound like a plausible theory? I'd like to ask one of said community PPC maintainers about this, but I'm not sure where to find or how to contact them. The [PPC team page]("https://launchpad.net/~ubuntu-powerpc/+members") on Launchpad looks sort of inactive, but clearly *someone* has been putting in a lot of good work to keep cranking out releases and updates. (Thank you!)

I'm starting a separate thread in the security forum to ask about the implications of not having kernel updates.

For reference, here are the relevant lines from my [FONT="Courier New"]sources.list[/FONT] file:   
```
deb http://ports.ubuntu.com/ubuntu-ports/ jaunty main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ jaunty-security main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ jaunty-updates main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ jaunty-backports main restricted universe multiverse
```

Thanks for any advice!

---

### Post by sweetleaf on 2009-09-30
Bump. Any thoughts on this?

---

### Post by jml on 2009-09-30
Don't have any insight on your specific question.  However, if the lack of kernal updates is a concern for you.  One option would be to switch to Debian 5.0 (Lenny) for the PowerPC architecture.  It is still actively supported by the Debian project.  Debian is not noted for cutting edge programs, but once installed and configured it's rock solid and like Ubuntu, you should only need to install it once.  From then on one does rolling upgrades.

Joe

---

