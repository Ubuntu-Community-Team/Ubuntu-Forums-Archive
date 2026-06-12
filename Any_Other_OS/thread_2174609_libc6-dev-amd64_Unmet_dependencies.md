---
title: "libc6-dev-amd64: Unmet dependencies"
date: 2013-09-15
forum: Any Other OS
---

### Post by SUMAN003 on 2013-09-15
**Hi, I have installed Ubuntu 12.10 in my machine(Intel corei7). ****I tried installing ****'libc6-dev-amd64' package**[B]. But I got the following error.

$ sudo apt-get install libc6-dev-amd64[/B]

[sudo] password for suman003: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libc6-dev-amd64:i386 : Depends: libc6-amd64:i386 (= 2.15-0ubuntu10.4) but it is not going to be installed
                        Recommends: gcc-multilib:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.



Please suggest a solution for this.

Thank you.

---

### Post by ubfan1 on 2013-09-15
The missing ap_fixed.h is not part of any system package, so why do you think the libc6-dev-amd64 is necessary?  Probabl the ap_fixed.h is a local file, and the makefile does not properly set up the include paths.

---

### Post by SUMAN003 on 2013-09-15
What should I do to rectify this?

---

### Post by jive-any on 2013-09-18
I can no longer install libc6-amd64:i386 on 12.04 well Elementary OS Luna to be precise ;) this package is needed for most of multi-lib so it breaks 32-bit compatibility packages for alsa which cause horribly distorted sound in wine.   Has anybody else had this issue with 12.04?  It seems to have just cropped up in the past few weeks, multilib and wine was working fine when I first installed eOS Luna, the reason I'm posting here is because this has to do with Ubuntu repos and eOS lacks forums.

Thanks

---

### Post by jive-any on 2013-09-18
I'm having exactly this same issue with Elementary OS Luna which is 12.04 based, I thought it was just my install.  This issue must be very common therefore somebody must have an answer?

---

### Post by jive-any on 2013-09-18
I've just filed a bug report for all those affected with this issue:

[https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/1227318](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/1227318)

---

### Post by sanderj on 2013-09-18
It would help if you would why you see happening when you try to install libc6-amd64:i386 

So, give the exact command (sudo apt-get installl ... ), plus it's output. And of course fist google the error message you get.

---

### Post by jive-any on 2013-09-18
It's no longer available in the repos for 12.04 but I've downloaded from 1 archive that still has it:

sudo dpkg -i Downloads/libc6-amd64_2.15-0ubuntu10.4_i386.deb 
dpkg: regarding .../libc6-amd64_2.15-0ubuntu10.4_i386.deb containing libc6-amd64:i386:
 libc6 conflicts with libc6-amd64
  libc6-amd64:i386 (version 2.15-0ubuntu10.4) is to be installed.
dpkg: error processing Downloads/libc6-amd64_2.15-0ubuntu10.4_i386.deb (--install):
 conflicting packages - not installing libc6-amd64:i386
Errors were encountered while processing:
 Downloads/libc6-amd64_2.15-0ubuntu10.4_i386.deb

---

### Post by sanderj on 2013-09-18
Ah. My gut feeling says: if it is not in the repos, there must be a reason for it. I would not dare to install some system package from a third source.
And I would expect that also works out-of-the-box.

I have no further advice.

---

### Post by jive-any on 2013-09-18
> **sanderj said:**
> Ah. My gut feeling says: if it is not in the repos, there must be a reason for it. I would not dare to install some system package from a third source.
And I would expect that also works out-of-the-box.

I have no further advice.

Well whatever that reason may be, they've broken large parts of 32-bit compatibility on the most recent LTS release, a major screw up when you consider that a large number of high-end cloud servers on the internet that run 12.04 due to the "stability" of long term support.  I would also assume the vast majority of such servers and workstations need 64-bit for performance and memory requirements but have 32-bit legacy apps that they need to run.

---

### Post by sanderj on 2013-09-18
So you mean you can't run 32-bit programs anymore on 64-bit 12.04?

I have 64-bit 12.04 servers, so which program is 32-bit? I can test that for you

---

### Post by oldos2er on 2013-09-18
Threads merged and moved to Other OS/Distro Support.

---

### Post by jive-any on 2013-09-18
> **sanderj said:**
> So you mean you can't run 32-bit programs anymore on 64-bit 12.04?

I have 64-bit 12.04 servers, so which program is 32-bit? I can test that for you
Try running anything in 32-bit wine and tell me if you get sound distortion, I don't know of anything else that this affects at the moment Steam games which are 32-bit seem to work fine.

Also, I don't why this thread was moved as it affects Canonical's 12.04 repositories and has nothing to do with the Elementary OS repos.

---

### Post by oldos2er on 2013-09-19
Mint and possibly other distros use Canonical's repos too, but Canonical doesn't officially sponsor or develop derivatives like Mint or Elementary, so in that sense they are "Other OSes".

---

### Post by jive-any on 2013-09-20
> **sanderj said:**
> So you mean you can't run 32-bit programs anymore on 64-bit 12.04?

I have 64-bit 12.04 servers, so which program is 32-bit? I can test that for you
Pretty much anything in WINE

---

