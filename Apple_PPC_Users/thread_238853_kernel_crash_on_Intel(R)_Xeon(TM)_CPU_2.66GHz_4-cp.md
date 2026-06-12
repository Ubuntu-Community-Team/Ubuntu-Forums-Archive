---
title: "kernel crash on Intel(R) Xeon(TM) CPU 2.66GHz 4-cpus machine"
date: 2006-08-18
forum: Apple PPC Users
---

### Post by andrea.puglisi on 2006-08-18
Hi everyone,

I've installed ubuntu breezybadger and upgraded up to Ubuntu 6.06 LTS a couple of days ago, on my machine with 4 Intel Xeon cpus (2.66Ghz); just yesterday I've upgraded the kernel (which was originally -386) to 2.6.15-26-686 in order to exploit the multiprocessor architecture

everything was working very well; SO well that I finally launched the execution of four numerical simulations (scientific work) 

:D 

a couple of hours ago I was working on the machine (while the four jobs were running smoothly since 20 hours) when it suddenly froze up completely

:( 

screen frozen, keyboard frozen, mouse pointer frozen, alternate screens inaccessible, network interface frozen (no ping from remote): death of the system

I've never seen such a horrible freeze in many years of heavy work with linux&c

](*,) 

I rebooted (simulations to be started again, sob!!) and then browsed carefully all log files; I've found no message at the time of the freeze, nothing to be used as the smallest hint

my machine contains: 1Gb of physical ram, 2 ide hard disks (master/slave) with 80Gb each, an external usb disk with 150Gb (used to store the data from the simulation), and an energy backup apc (ups pro 650)

as I told you, the installation was done two or three days ago and the new 686 kernel was installed just yesterday; before this freeze the system was up since 20 hours, perhaps more; this is why I have NO IDEA of which has been the critical event triggering the crash

note that this machine has been working well since three years with FreeBSD, I would exclude hardware problems

Please, give me any kind of idea, a test or a place/file where I can find a track to follow and understand what happened. I cannot stand it happens again, otherwise I will be forced to go back to free-BSD

Thanks everybody!

 Andrea

---

### Post by avtolle on 2006-08-18
Hi, and welcome to the Forums. Are you aware that you posted in the Mac forum (yeah, I know the heading is a bit misleading)? You should probably be in another one, best of luck.

EDIT: OK, I'm ignorant, and the above amply displays it. With that said, have you looked at the SMP kernel?

---

### Post by andrea.puglisi on 2006-08-21
Thanks avtolle for your reply, anyway I do not understand: the header says "intel" too. And there are no any other forum on intel. What does it mean? Where do intel-users post their messages?

Concerning "smp", the kernel I've installed (686) is in fact the smp version of the normal kernel. It appears that recently the old "smp" suffix has been removed leaving only 686 which is sufficient. 

 Thanks

 Andrea

---

### Post by avtolle on 2006-08-21
This is the correct forum for intel Mac users; as I tried to convey in my earlier post, my ignorance outran my knowledge. :) Perhaps posting in the installation/support forum might also be of help to you, I don't know that there are many intel Mac users out there who regularly post to this forum. Thank you for the update on SMP; I didn't know that.

As a final thought, did you install the latest 6.06.1 release, with the kernel updates? This has seemed to "cure" many outstanding issues with the installation from the original kernel, both in PPC and in e.g., 64-bit users. Best of luck.

---

