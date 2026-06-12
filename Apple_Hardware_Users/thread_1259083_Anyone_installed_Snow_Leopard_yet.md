---
title: "Anyone installed Snow Leopard yet?"
date: 2009-09-05
forum: Apple Hardware Users
---

### Post by vincebs on 2009-09-05
Hi everyone,

I'm thinking of updating Mac OS X from 10.5.8 to 10.6.0 but I'm worried that Mac might erase Ubuntu and reFIT.

Has anyone here installed 10.6 and been able to keep Ubuntu without having to reinstall it? Jaunty Jackalope works great now and I have it all configured so I would hate to have to reinstall it again.

Also, I heard that Apple made some changes to the HFS file system with 10.6, can Linux still read/write HFS (non-journalized)?

Thanks,
Vince

---

### Post by Bad Penguin on 2009-09-06
> **vincebs said:**
> Hi everyone,

I'm thinking of updating Mac OS X from 10.5.8 to 10.6.0 but I'm worried that Mac might erase Ubuntu and reFIT.

Has anyone here installed 10.6 and been able to keep Ubuntu without having to reinstall it? Jaunty Jackalope works great now and I have it all configured so I would hate to have to reinstall it again.

Also, I heard that Apple made some changes to the HFS file system with 10.6, can Linux still read/write HFS (non-journalized)?

Thanks,
Vince

Unfortunately I had to wipe my previous OSX and jaunty installation before I could get the snow leopard update to recognize my hard drive as "bootable".  To make a [long story short](http://discussions.apple.com/thread.jspa?threadID=2130966&tstart=300&messageID=10137663#10137663), the snow leopard upgrade requires 128MB of free space immediately proceeding the osx partition being upgraded.  This is not mentioned in any of the ubuntu mactel documentation yet.  A couple of users in the thread linked above have managed to free up 128MB after their osx partitions and get the upgrade to complete successfully.  I can only say I wish I had known that before hand, I would not have had to waste several hours wiping everything, restoring, upgrading, then re-installing jaunty from scratch ;)

---

