---
title: "Ubuntu startup problem with F-J Amilo A"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by anttirl on 2008-01-15
Well hello there.

I truly am a beginner, but I'll try my best to give the necessary information for any helpers out there.

Downloaded the live-CD for Ubuntu 7.10 and it worked like a charm. After playing around with it I decided to Install Ubuntu to replace XP.

Heres's the starting specs:

Laptop - 
Fujitsu-Siemens AMILO A with AMD Athlon 2200+ (1,8 Ghz)
80GB
512MB RAM
ATI Radeon IGP 320M
Windows XP under the hood with NTFS

Alrighty, the installation went through without any problems. I let Ubuntu use the whole drive for it and it changed the file system to ext3. 

So, excited I booted the computer. It started the BIOS and began the GRUB countdown... then nothing, the whole system just froze with a black screen staring at me.

I booted again after searching some net with the Live-CD. A wiser man I booted again and got to edit some boot parameters. I inserted the whole lot of things I could find (only the last time did insert them all at once). Anyway, I used these:
- quiet=off(of this I'm not sure anymore how it should really be written),
- noapic, 
- nolapic, 
- acpi=off etc. 

With these the load went a bit further, at least past the point where the system makes the checks: 
something....OK
something....OK
...

All in all, the result was the same as in the first time the system tried to boot.

Now I'm back running XP, but am willing to try once moreif there's any chance of getting the thing to work.

---

### Post by anttirl on 2008-01-15
ummm... this was actually a question and I promise I won't be offended by any answers you might have to help me start my travels in the world of Ubuntu, thanks already.

---

