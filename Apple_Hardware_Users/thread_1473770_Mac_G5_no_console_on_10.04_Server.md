---
title: "Mac G5 no console on 10.04 Server"
date: 2010-05-05
forum: Apple Hardware Users
---

### Post by fatedsnowfox on 2010-05-05
I really don't know what to make of this.  I have just installed Lucid Server onto my first generation Mac G5 (1.6 uni).  The install went fine & the system rebooted...

The first problem:

Fatal errors encountered installing thermal control.  All the windfarm modules failed, but judging by the fact the mac doesn't sound like a jet engine, thermal control /is/ working. 

The second problem:

After this, it brings up the splash screen & then the console goes dead.  No keyboard, no display, no nothing; it looks like the system has hung.  But...  SSH is working.  The system is up and as responsive as it should be!

I've tried adding video=ofonly to yaboot.conf and zapping the pram, but it made no change.  I'm stuck for options now.

---

### Post by barbaGNU on 2010-05-06
you should compile as builtin your own fb module.

---

### Post by fatedsnowfox on 2010-05-06
> **barbaGNU said:**
> you should compile as builtin your own fb module.

You mean compile a new kernel module?  And if so, which one?  I'm not overly familiar with linux on PPC, and this early model G5 is one fussy SOB.

---

### Post by barbaGNU on 2010-05-06
if your one is a Power Mac G5 (year 2003) then it should be "video=nvidiafb" as your one is equipped with a NVIDIA GeForce FX 5200 Ultra.

Anyway try to boot your machine with a CRUX PPC 2.6 64bit install ISO and then, if it works fine, try to understandtheir methods.

---

### Post by fatedsnowfox on 2010-05-06
I found the solution.  I should have thought of it myself. 

/etc/config.d/blacklist.conf

add the line:

blacklist nouveau

I swear, nouveau is the biggest, stinkiest, most steaming pile of faeces I've ever had the misfortune to encounter.  

Thanks for your help though, it got me thinking in the right way at least.:lolflag:

---

### Post by linuxopjemac on 2010-05-07
> I swear, nouveau is the biggest, stinkiest, most steaming pile of faeces I've ever had the misfortune to encounter. 

:lolflag:

---

### Post by SpaceBas on 2010-10-24
Thanks for this thread. Adding 'blacklist nouveau' got me a little further in 10.10, but still no video. 

Prior to adding it, the screen was totally blank after the boot loader. 

After adding it, I see the errors about windfarm and briefly see the Ubuntu logo - then blank again. 

Anyone solved this one?

---

