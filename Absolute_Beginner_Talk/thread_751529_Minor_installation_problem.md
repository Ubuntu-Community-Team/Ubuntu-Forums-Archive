---
title: "Minor installation problem"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Epedemic on 2008-04-10
Hello, I believe this is the help forum, if not, correct me. EDIT: I apologize, this is the help forum for the forum only, if someone may move it to the right section, i'd be grateful.

Well to get to the point, I have a old version of the ubuntu CD, version 6.06 LTS from awhile ago. I booted from the CD and i'm pretty much typing this from CD OS right now. I'm having trouble installing ubuntu. 

My issue is during Step 5 of 6. The step where I have to select a Disk partition and I've let it run for 10 minutes or so, and it never loaded. I have a more than capable computer to handle ubuntu and I have 2 hard drives. I've tried re-installing but still get stuck at the same spot. Any help? I was intending to partition my 320 gig HD for a 100 gig partition just for ubuntu. Thanks for the help.

---

### Post by R6V2 on 2008-04-10
Ugh, 6.06 isn't supported anymore. I suggest you get a newer version!

---

### Post by Epedemic on 2008-04-10
I don't believe it is the version that is effecting it, my computer hardware is still from around when 6.06 was released, perhaps even before.

---

### Post by bobbocanfly on 2008-04-10
You should probably try with a Gutsy (7.10) Live CD to see if that can detect your hardware any better. Hardware detection/compatibility has come a *long* way since Edgy so might be able to fix your problem

---

### Post by rjmoerland on 2008-04-10
> **R6V2 said:**
> Ugh, 6.06 isn't supported anymore. I suggest you get a newer version!

Hmmm, from the Ubuntu website: "Ubuntu 6.06 LTS - Supported to 2009" (for the Desktop Edition) and "Ubuntu 6.06 LTS - Supported to 2011" (for the Server Edition).

Now back to the original problem: can you access the hard disk at all?

(EDIT: I'd go with bobbocanfly. If the hardware can't do Ubuntu 7.10, I'd rather have Xubuntu 7.10 than Ubuntu 6.06)

---

### Post by Epedemic on 2008-04-10
I was planning on ugrading to 7.10, I intend to use Beryl, would I download 7.10 for that? or does that matter? I will attempt to download the iso and install 7.10 to see if that makes a difference.

---

### Post by bradwilliamson on 2008-04-10
6.06 is indeed supported, I use it for nearly all my servers for just that reason.

That said, hardware detection has indeed come a long way as bobbocanfly has said.

Does it ever get to the grey/blue partitioning screen or is it stuck at a blank blue screen?

I've had issues with some SATA controllers not showing up installing 6.06, and had to try different variations of:

boot with: linux acpi=off
boot with: linux noapic
boot with: linux acpi=off noapic
boot with: linux acpi=off nolapic
boot with: linux acpi=off noapic nolapic
boot with: linux acpi=off all-generic-ide

to get it to see any SATA disks, including the SATA DVD drive that it booted from itself.

I don't know if these will help you, but perhaps it will cough up some more info to go on.

And, if I were getting started with Beryl and killer 3D on a desktop machine, I'd go with Gutsy myself.
6.06.1 for Servers
7.10+ for Desktops
Come on Hardy!

---

