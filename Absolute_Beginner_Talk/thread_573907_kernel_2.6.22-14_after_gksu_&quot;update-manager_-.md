---
title: "kernel 2.6.22-14 after gksu &quot;update-manager -c -d&quot;"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by SabrinalovesUbun2 on 2007-10-12
hi
I wanted to give Gutsy a spin so I searched around a little and this seemed a simple way

gksu "update-manager -c -d" (its been about 2 weeks and everything expect Azureus seems to be working fine in Gutsy, oh and my fonts have become smaller!)

but now my kernel is on 2.6.22-14! (please see the pic below)

is that ok, I guess I'm stuck in the development mode, how do I get back to the normal version and how do I clean up properly, I dont want 5 versions of the same thing?

All I wanted to do was to upgrade my Feisty to Gutsy.

---

### Post by overdrank on 2007-10-12
> **SabrinalovesUbun2 said:**
> hi
I wanted to give Gutsy a spin so I searched around a little and this seemed a simple way

gksu "update-manager -c -d" (its been about 2 weeks and everything expect Azureus seems to be working fine in Gutsy, oh and my fonts have become smaller!)

but now my kernel is on 2.6.22-14! (please see the pic below)

is that ok, I guess I'm stuck in the development mode, how do I get back to the normal version and how do I clean up properly, I dont want 5 versions of the same thing?

All I wanted to do was to upgrade my Feisty to Gutsy.

Hi, and I have the same thing and will continue to updates to the kernel.  If you would like to clean up the grub this is a good link to do so
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
Good luck!

---

### Post by por100pre1 on 2007-10-12
You can remove the older kernels with Synaptic and just leave two or three, however I would suggest you to do a fresh Gutsy install. **Backup your user folder on removable media or external hdd before whatever you decide to do.**

---

### Post by Seisen on 2007-10-12
I honestly think it is a bug because the same thing happened to and the other kernels still booted up fine. Also I followed the same "update-manager -c -d" command so maybe this has something to do with it.

---

### Post by MozartlovesUbun2 on 2007-10-12
> **por100pre1 said:**
> You can remove the older kernels with Synaptic and just leave two or three, however I would suggest you to do a fresh Gutsy install. **Backup your user folder on removable media or external hdd before whatever you decide to do.**

Ouuf, I wanted user "SabrinalovesUbun2" to avoid a clean install!

um so can I ask why you are advising a clean install?

---

### Post by MozartlovesUbun2 on 2007-10-12
> **Seisen said:**
> I honestly think it is a bug because the same thing happened to and the other kernels still booted up fine. Also I followed the same "update-manager -c -d" command so maybe this has something to do with it.

Is this gonna be fixed by team ubuntu anytime soon? or what  does one have to do?

---

### Post by Seisen on 2007-10-12
I don't know I haven't filed a bug report but somebody else might have. I did look into my menu.lst file in grub that 7.10 has been added to each one of my kernels which might explain the development part. But really it is no big deal, the kernels should boot up fine, I think this problem is more cosmetic than anything else.

---

### Post by ThrobbingBrain66 on 2007-10-12
I agree with with Seisen.  There is no REAL problem here.  Whenever the kernel is updated to a newer version during the development cycle, the older kernel is kept.  This allows you to boot if something would be wrong with the newer kernel.  Anything pre- 2.6.22-14 will show up in Synaptic under the 'auto-removable' category.  Select them all and choose 'remove completely' and they will be gone.

---

### Post by MozartlovesUbun2 on 2007-10-15
> **ThrobbingBrain66 said:**
> I agree with with Seisen.  There is no REAL problem here.  Whenever the kernel is updated to a newer version during the development cycle, the older kernel is kept.  This allows you to boot if something would be wrong with the newer kernel.  Anything pre- 2.6.22-14 will show up in Synaptic under the 'auto-removable' category.  Select them all and choose 'remove completely' and they will be gone.

before sabrinas PC had 2 ubuntu choices and below the windowsXP, now the ubuntu choices just keep piling up to a long list!

---

