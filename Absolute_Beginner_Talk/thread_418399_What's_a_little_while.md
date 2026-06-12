---
title: "What's a little while?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by soul_motor on 2007-04-22
Th GraphicInstall help page says it may take a "LITTLE while" to load the boot disc.  Mine has been running for two hours now...  Is that normal?  Should I stop it and restart?  I'm leaving in a little bit, so I'll probably leave it running while I'm gone, but if it's not done in the next two hours, should I give up?  Thanks.

---

### Post by Kobalt on 2007-04-22
A LiveCD can take up to 7min to boot on an old computer, a couple of hours is certainly way too long. 
What are your hardware specs ?

---

### Post by soul_motor on 2007-04-22
I have a Celeron D with 2.8 Ghz, 512Mb Ram, and I have about 20 Gb unused space set aside for linux...  It never did start.  In all it ran for five hours without doing anything substantial.  I redid it and it hung up on me again...

---

### Post by n3tfury on 2007-04-22
did you verify the .iso with the md5checksum?  you also might need to burn at a slower speed (4x).

---

### Post by bobplano on 2007-04-22
> **n3tfury said:**
> did you verify the .iso with the md5checksum?  you also might need to burn at a slower speed (4x).

well if you check the cd and it's fine it doesn't really matter what speed you burn at, but generally yes if you burn at a fast speed or the .iso is messed up then it might not work. your specs are fine btw, i'm running dapper at about your specs and the hardware requirements shouldn't change too much for different versions

---

### Post by soul_motor on 2007-04-22
thesum check was pretty groovy, I had a bad copy already.  I did the check disk tool, and it said it was fine.  right now it's hanging in the lines instead of looping.  What I have now is:

call Trace:
  smp_apic_timer_interupt
  apic_timer_interupt
  __sced_text_start
  cond_resched
  __mutex_lock_slowpath
  Mutex_lock
  sys_init_module
  iTCO_wdt_unset_NO_EBOOT_bit
  sys_mmap2
  sysenter_past_esp
=======================
some really lnog string of code...
native_apic_write_atomic

next line is empty.  There's a whole bunch of numbers before the call trace, but I'm not sure if they're important...

---

