---
title: "686kernel won´t shutdown, 386 does"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by Jallu59 on 2006-09-28
Hey

I tried to update mu ubuntu(dapper) by loading 686kernel. Everything went Ok, but the new kernel brougt one problem alongside. When I try to shutdown the computer it remains in the state "will now halt" and never turns off the power. I tried again with the old 386 kernel, and with it the computer turns off its power autiomatically. Why this difference in behavior? Is there any other solution to this, but to throw the 686-kernel away ?

Motherboard MSI-6178, P3/400MHZ/256MB

Yours

Jallu59
having 28 years of computer work experience, but a linux newbie

---

### Post by petri on 2006-09-28
Terve Jallu!

Did you do like [this]("http://ubuntuforums.org/showthread.php?t=85917&highlight=386+686+k7") when you installed your 686-kernel? 
Or if you did install 686 with Synaptic you sure can uninstall it with Synaptic and then try the link above to install 686 again.

BTW what kind of hardware you have? Post the result of
```
lspci
``` here if the above doesn't help you. 
I think it might be something with your video drives...




EDIT: Here is a couple of threads about not shutting down 
[http://ubuntuforums.org/search.php?searchid=8477415](http://ubuntuforums.org/search.php?searchid=8477415) 
Maybe you find something there.

---

### Post by Jallu59 on 2006-10-02
Tjänare Petri

I did "sudo apt-get install linux-686" to get the kernel and it went OK.

I won´t be at homeby the computer mentioned, until next weekend, so I can´t use "lspci" , but here´s more info about the machine.

As said Motherboard is MS6178, processor Pentium III / 400MHz, display adapter is integrated Intel(915 I recall) with 4MB display memory, integrated AV97´ sound chip ... Very standard desktop PC of it´s time.

I didn´t get any help from the threads mentioned(the serach link didn´t work at all),but I did a survey with word "shutdown" on this forum and someone had alike problem after he had been switching to "Edgy". 

Still wondering
Jallu59

---

### Post by petri on 2006-10-02
I was hoping you had ATI graphics but not. And that is good for you.

I think though that 686 ain't giving any perfomance advantage... for 400MHz :rolleyes: 



But what do I know! I'm a Donkey! :mrgreen:

---

### Post by JayTee on 2006-10-02
With a Pentium III I don't think you need the 686 kernel. The 686 kernel is for newer intel cpus that have hyperthreading and or dual-cores.

---

### Post by Jallu59 on 2006-10-02
Hey JayTee

According to my previoius knowledge and according to Petris link "this", 686kernel should be valid to CPU:s from P2(~200Mhz). The hyperthreading, multiprocessor and dual-core features are utilized in kernel versions linux-686-smp and linux-k7-smp (smp=symmetrical multiprocessing).

Yours
Jallu59

---

### Post by po0f on 2006-10-02
> **JayTee said:**
> With a Pentium III I don't think you need the 686 kernel. The 686 kernel is for newer intel cpus that have hyperthreading and or dual-cores.

Wrong. A Pentium 3 is a 686 processor.  Vanilla Pentiums were 486, Pentiums with MMX were 586, Pentium 2s and up (I believe Pentium Pros are lumped in here), are 686s.

---

### Post by Jallu59 on 2006-10-03
This is getting off my original topic, but dear Po0f, you were only partially right by saying:

> Wrong. A Pentium 3 is a 686 processor. Vanilla Pentiums were 486, Pentiums with MMX were 586, Pentium 2s and up (I believe Pentium Pros are lumped in here), are 686s.
Reply With Quote

486´s were not yet Pentiums and the first Pentiums (60-166MHz)were aliased as 586´s. Even according to earlier references in this thread, 686´s are those wiht MMX instruction set extensions and Pentium Pros (~200MHz and up)

Yours
Jallu59
an elder PC-service consult

---

### Post by dmizer on 2006-11-09
i have the same problem on a 2.6ghz p4 desktop.  386 kernel shuts down fine, 686 kernel does not.

Jallu59, set them younguns right! lol, i was about to step in and say a word or two about that myself.

another elder PC-service rep.
... anyone remember the "turbo" button? ;)

edit to add: i believe this is our bug ... [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43961](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43961)

---

