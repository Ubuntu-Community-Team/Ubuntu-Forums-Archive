---
title: "Dual Boot Query"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Manstein on 2007-01-07
Bit of a mystery one here. With assistance from a friend I've rebuilt my PC as dual boot. XP Pro and as an introduction to Linux Ubuntu 6.10. Ubuntu worked fine at the friends house so I hauled the PC back to the office. I installed a couple of external hard drives via USB and set up my dual monitor for PS work. AV and Firewall also.

After getting the above running ok I booted Ubuntu which promptly refused to load and I got this message..

[17179571.224000] ACPI Looking for DSDT.. Not found.

Presumable something I've done in XP has affected Ubuntu. I've had a look in the Ubuntu support and can find mention of DSDT but apart that its some sort of table little else.

Any clues please.

---

### Post by Manstein on 2007-01-08
Seems to have left the guru's baffled!

---

### Post by tchoklat on 2007-01-08
[http://bugzilla.kernel.org/show_bug.cgi?id=7089](http://bugzilla.kernel.org/show_bug.cgi?id=7089)

---

### Post by rbhigday on 2007-01-08
> **Manstein said:**
> Seems to have left the guru's baffled!

congrats on stumping the masters, unfortantly that is also not good for fixing your problem :(

---

### Post by Efwis on 2007-01-08
I would say the issue stems from the external Hard drives. Can you try unplugging them, 1 at a time, and rebooting to see if one of them might be the problem.

also could you tell the specs of the external HDD's in the next post.

---

### Post by Manstein on 2007-01-09
Thanks for the responses. The two hard drives are a Western Digital 250gb which is a firewire connection and a 200gb Maxtor which is USB. I've tried all sorts of connection permutations, swapping sockets, one switched on one off, one unplugged etc but the only constant is that Ubuntu doesnt boot if the hard drives are plugged in and either switched on or off.

If the drives are plugged in when the OS has booted up they are recognised and work perfectly.

Thanks

---

