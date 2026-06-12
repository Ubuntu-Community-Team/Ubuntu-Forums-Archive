---
title: "Dualboot OSX and Ubuntu on a Powermac?"
date: 2009-06-28
forum: Apple Hardware Users
---

### Post by Cam42 on 2009-06-28
I'll be picking up a ppc powermac in a few days, and was wondering if it would be possible to dual boot Ubuntu and OSX.
If so, how would I set this up?
I know I'll have to get the PPC version of Ubuntu, how will that change software availability/compatibility. Anything else I should look out for?

---

### Post by igor_av on 2009-06-28
> **Cam42 said:**
> I'll be picking up a ppc powermac in a few days, and was wondering if it would be possible to dual boot Ubuntu and OSX.
If so, how would I set this up?
I know I'll have to get the PPC version of Ubuntu, how will that change software availability/compatibility. Anything else I should look out for?

It's quite easy. Look for "yaboot" on Google. It allows you to choose between OS X, OS 8-9, Linux and the CD Drive on startup.

The simplest way to get OS X and Ubuntu on the same disk is to partition your HD with the Mac OS X install disk during installation, leaving as empty whatever portion of the HD you want to give to Ubuntu. Then, install Ubuntu. It will automatically install and configure yaboot.

---

