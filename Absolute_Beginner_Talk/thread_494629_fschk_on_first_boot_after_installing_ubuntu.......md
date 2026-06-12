---
title: "fschk on first boot after installing ubuntu......"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-07-07
this is kind of a strange but true thing, it doesnt cause any problems, least i dont think it does, but when i re-boot the system after installing ubuntu the fschk runs.
now the strange thing is that it says that it needs to run as the drive has been mounted for 49700 days with out being checked, now thats roughly 136 years ? strange but as far as i now my hard drive is only a year or 2 old.
ive had to re-install ubuntu a few times and it does it every time, but like i said it doesnt cause any problems, its just a strange thing.
cheers

---

### Post by Skrynesaver on 2007-07-07
On first boot the drive hasn't been checked ever, hence the max value is displayed.  I presume it checks every few boots with a more logical message.

---

### Post by techno-mole on 2007-07-07
it normally checks the drive every 24 mounts i think, it was just an odd thing, that i thought i would share.
:D

---

### Post by atria on 2007-07-07
That is because your system bios time is set to your local time instead of UTC. This is why your ubuntu installation thinks it was installed in the future when it really isn't.

Try setting your system time to UTC and reinstall, you shouldn't see the error message again.

In any case this should not have any impact on your ubuntu installation.

---

### Post by Jimmyfj on 2007-07-07
Woow - I must be a real old-timer then :) 136 years continuously mounted volumes :):)

I've seen that message a lot of times when installing Ubuntu on different machines. None of those computers have had any troubles since, although they now do a fschk every 21 time the fs has been mounted. LoL message though.

---

