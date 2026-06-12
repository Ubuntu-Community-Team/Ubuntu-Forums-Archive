---
title: "computer hangs looking for network, then stops booting"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by Peacepunk on 2006-05-11
Hi All

Brand new PC, Kubuntu "Breezy", 4th install for my office (the three other runs well...

This computer isn't connected to a network - I did not disabled the included eth card to be able to upgrade it "once for all" then intall it in our accountants office. Now, actually, I HAVEN'T GOT THAT FAR: after install, the "waiting for net interface to come up" hangs for ages, then switch to a terminal-type login that is not "far" enough in the booting process to allow me to switch to kdm & log in.

PC is a 2.1 Celeron, dual boot, 256 ram, dual HDD basic desktop ... intended for virus-free accountancy !

Any idea on how to semi-permanently disable the Network Lookup - without recompiling the kernel: I did look here & there on the forum, and, err.. it looks a bit complicated. Boot Speed-Up advices for instance involves apt-get stuff. Rather inappropriate when you do not have a connection & want to get rid of the Eth Card !

Thanks

..

---

### Post by louis_nichols on 2006-05-11
When you see the prompt about bringing up network interface, press Ctrl+C. Then, you might have to do the same when it says "trying to sync clock with ubuntulinux.org"... Well... you can press Ctrl-C for pretty much anything that hangs for more than  a while. Don't worry if, in the meantime, the black screen comes up. The boot process will go on correctly.

---

### Post by Peacepunk on 2006-05-11
Thanks

I'll look like shit if I enter the Accountancy office with a brand new Computer / Brand new OS, and explain people they should watch over & ready the Ctrl+C command...

Hum.

This will allow me to step in, and disable the net card from the Net setup - This is what I do with the Laptops, and it's fine so far. Hope this works as well on this box. 

Well, they're happy to switch to a Virus-Free World anyway.

Any other Very Basic Recommendation appreciated - Try to do Linux @ 5 hours drive from the capital city in... Cambodia.

:-?  We do lack a bit of support, actually.  :-? 


.

---

### Post by louis_nichols on 2006-05-11
The Ctrl+C thing is only to get you to boot the OS, as you said. So, noone else will have to press ctrl+c again.

I think ubuntu does come with professional support from Canonical. I mean, these ppl have to get their money from somewhere, right? :)

EDIT: I mean, professional support AVAILABLE. For a fee. Just in case I wasn't clear enough

---

### Post by confused57 on 2006-05-11
You might try going to Synaptic Package Manager and installing "sysv-rc-conf"

After installing, open terminal and enter:

```
sudo sysv-rc-conf -s 2S
```

No guarantees, never tried it myself, but you may be able to select what starts at bootup...be careful what you disable.

May be able to use BUM:

[http://www.ubuntuforums.org/showthread.php?t=174345](http://www.ubuntuforums.org/showthread.php?t=174345)

---

