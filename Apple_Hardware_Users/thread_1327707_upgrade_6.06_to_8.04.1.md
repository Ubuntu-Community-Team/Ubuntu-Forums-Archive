---
title: "upgrade 6.06 to 8.04.1"
date: 2009-11-15
forum: Apple Hardware Users
---

### Post by natgab on 2009-11-15
I want to make sure my repos are ok so that i can upgrade from Xubuntu 6.06 to 8.04.1 without problems.

I decided to change my iMac, which had Debian, to Xubuntu.  I have a stable version of 6.06 now.  But yesterday I tried to upgrade to 8.04 and when i did, it stopped about 3/4 of the way saying something about xdm needing to be restared manually. It would stay frozen, and if I rebooted manually it would have a corrupt xorg.  I had all updates for 6.06 installed.

I redid my 6.06 install, making sure to add the community repos and running the updates. This time it offers me version 8.04.1, does this mean it will now update correctly?

Here are the current repositories in synaptic:

```
cdrom - main restricted

Ubuntu 6.06 LTS  (binary) - official supported restricted copyright

Ubuntu 6.06 LTS  (sources) - official supported restricted copyright

Ubuntu 6.06 LTS updates (binary)- official supported restricted copyright

Ubuntu 6.06 LTS updates (sources)- official supported restricted copyright

Ubuntu 6.06 LTS  (binary) - Community maintained (universe)

Ubuntu 6.06 LTS  (sources) - Community maintained (universe)

Ubuntu 6.06 LTS security updates (binary)- official supported restricted copyright

Ubuntu 6.06 LTS security updates (sources)- official supported restricted copyright
______________________________________
repos not selected:

Ubuntu 6.06 LTS backports (binary)- official supported restricted copyright/community/non-free

Ubuntu 6.06 LTS backports (sources)- official supported restricted copyright/community/non-free

Ubuntu 6.06 LTS security updates (binary)- community (universe)

Ubuntu 6.06 LTS security updates (sources)- community (universe)

``` 

Do I just need to activate all of them, or do some need to be edited.  I saw the PPC known issues says something about redirecting the repos since they are now community based.  I have not edited the repo URLs.

---

### Post by s3a on 2009-11-15
Isn't the powerpc architecture deprecated after 6.06 in Ubuntu?

---

### Post by natgab on 2009-11-16
> **s3a said:**
> Isn't the powerpc architecture deprecated after 6.06 in Ubuntu?

---Yeah, that it why I wanted to move to 8.04.1, but needed to make sure my repos are correct.  So that it doesn't mess up like the first time I did it.

I had Debian on it because I had trouble loading 9.04 on it. So I used the old 6.06 disc I had an decided to work my way up at least to 8.04 since its LTS.

I'm still a noob, and figure its easier to just learn one set of commands than go back and forth from sudo to root.  I first need to feel more comfortable in Ubuntu. :D

---

### Post by wilee-nilee on 2009-11-16
If you want to feel comfortable that is the hardest way to do it, a fresh install to a later setup will give the feel for what is available now.

---

