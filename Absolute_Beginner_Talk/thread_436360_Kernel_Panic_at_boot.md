---
title: "Kernel Panic at boot"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by jbor7755 on 2007-05-07
I was just thinking to myself last night that I was almost ready to launch off on my own away from Windows XP. I now know how I should get all my usual hardware up and running.

I recently did an install from a set of dvds from an online shop (which includes all repositories and an update dvd.  I installed and then added the dvd repositories to synaptic.
Then I ran update from the dvd and rebooted.

At grub I get two versions of linux (presumable becasue the update included a new kernel edition).  These are:
2.6.15-28-386
2.6.15-23-386
along with their associated recovery modes. I booted fine into the newer (-28-386) one and then proceeded to install network manager (It is a laptop with wireless card).  All worked fine after another reboot.

However when I went to start it up this morning (on battery) I selected the newer kernel again but this time I got a kernel panic:

Kernel panic - not syncing: IO-APIC timer doesn't work

Something like that.  It asked me to boot with "noapic".

I switched off and booted into the older kernel just fine.  Then I plugged in the power adapter and rebooted again into the newer kernel: It worked fine. Wierd
So I unplugged again and went back to reboot again in the newer kernel from battery. It worked fine !!!???? :confused: :confused: 

There is only one thing worse than a big problem: An intermitent minor problem with unknown cause and unknown effect.

But I guess it's back to business as usual.

Has anyone experienced similar?  I am running a Dell Inspiron 6000 with Dapper 6.06.1

Cheers

---

### Post by chalex on 2007-05-07
Have you tried running memtest overnight?  It could be a hardware problem.

---

### Post by jbor7755 on 2007-05-08
No It only just happened this morning.

Seems to work fine now though.

Do I run memtest at boot (GRUB)?

---

### Post by jbor7755 on 2007-05-08
Okay, it hsppened again (after the computer had been off for a while).

Here is the full message on the screen after selecting the opeating system with newer kernel

[17179572.776000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[17179572.852000] Kernel Panic - not syncing: IO-APIC + timer doesn't work!  Boot with apic=debug and send a report.  Then try booting with the 'noapic' option.
[17179572.852000]

The numlock light was also on.

I have been running memtest86 for 10 and a half hours now.  How long does it take (I need to go to work and don't want to leave it running)?

---

### Post by WilliamKB on 2007-05-09
It also happens to me (for the last two weeks). But if I do a hot reboot it is fine.

I have an Inspiron 9300. I have no idea why it happens.

---

### Post by jbor7755 on 2007-05-09
Hmmmm.
Yeah I rebooted (into the same kernel) and there was no problem this time. Very strange.

I ran memtest for 20hrs and found no problems.

I will probably look to reinstall Dapper or to install Feisty once I know I can get all my hardware bits up and running. Removing windows in the process. Maybe that will do it.

---

### Post by mbs348 on 2007-05-18
> **jbor7755 said:**
> Hmmmm.
Yeah I rebooted (into the same kernel) and there was no problem this time. Very strange.

I ran memtest for 20hrs and found no problems.

I will probably look to reinstall Dapper or to install Feisty once I know I can get all my hardware bits up and running. Removing windows in the process. Maybe that will do it.

I get the same error message (intermintily) with feisty.  I really dont know what the issue is, but we all seem to have dells

dell inspiron 6000

---

