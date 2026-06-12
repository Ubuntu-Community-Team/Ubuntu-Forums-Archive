---
title: "G5 iMac and stable kernel 2.6.19 working!"
date: 2006-12-01
forum: Apple PPC Users
---

### Post by stream303 on 2006-12-01
Just compiled the latest vanilla stable kernel 2.6.19 and all is well on Edgy. (except for one thing)

**[COLOR="Red"]Linux G5iMAC 2.6.19 #1 Fri Dec 1 00:17:45 PST 2006 ppc64 GNU/Linux[/COLOR]**

The nice thing is that I didn't have to worry about adding stack protection by editing the Makefile with -fno-stack-protector anymore.  Yup, fixed in 2.6.19

I read through the changelog and rejoiced to see so much PPC support!

The only thing broken seems to be Firestarter - even though I compiled Xtables and IP Tables support as built-ins (not modules), firestarter complains that IP-Tables support is not enabled in the kernel.  It also can't be removed now with casual Synaptic removal.

Not a big deal as I'm behind a nat-router with built-in firewall, but just testing out iptables.  I'll have to do more research on this later to see what I did wrong.  No worries.

---

### Post by stream303 on 2006-12-02
Removal of the broken firestarter was easy - just had to boot into old stock edgy kernel, and remove it that way.

UPDATE 11 DEC 2006 - I found a way to get my iptables to work - I was just configuring it wrong.  HOWEVER, I can't seem to find a way to get user-switching to work with the custom kernel without the screen just locking up.

Well, everything works with the standard stock edgy kernel on a g5 iMac as long as you fix the screaming fans by applying the windfarm modules once and don't need specialized customizations.  My custom kernels were faster, but at the expense of user switching until I find a way to fix that...

---

