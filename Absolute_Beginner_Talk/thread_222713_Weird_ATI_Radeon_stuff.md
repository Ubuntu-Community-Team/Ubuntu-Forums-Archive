---
title: "Weird ATI Radeon stuff"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by TheodoreWard on 2006-07-25
Hi all. I have a Dell notebook D810, with an ATI radeon mobility X600 running Dapper

I have had XGL/Compiz working fine for sometime with the standard fglrx
stuff installed via apt-get.

So the other day I go to boot (the 2.6.15-26 kernel) and out of nowhere
I get a weird lilo message about the wrong size for vmlinuz and the
thing just hangs. So I boot the previous kernel (-25) and everything is
fine. I go into synaptic and tell it to re-install -26 and it does, but
I get the same message. I go back in and rerun lilo and voila it boots
just fine. Except now I have no video acceleration my video just
absolutely crawls.

If I do sudo /etc/init.d/gdm stop
and then login as my user (not root) and type startx everything starts
and works fine and accellerated and all.

Also if I boot the 2.6.15-25 kernel, everything still works fine.

Basically I have no idea what gdm does differently than simply typing
"startx" or where to start looking.

Any ideas?

Ted

---

