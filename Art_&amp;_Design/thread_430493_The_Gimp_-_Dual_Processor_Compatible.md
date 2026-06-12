---
title: "The Gimp - Dual Processor Compatible?"
date: 2007-05-02
forum: Art &amp; Design
---

### Post by Ted_Smith on 2007-05-02
Hi

Does The GIMP utilise dual processors (specifically two seperate processors as opposed to a dual core single processor - similar, but not the same). 

I don't mean if I open one file and while waiting for that to load I do something else with the Gimp and it use a different processor. What I mean specifically is, say I am applying a filter that's going to take ages and is quite intensive, will The GIMP spread the load across the two CPU's to speed it up or will it just use the one to conduct that specific task? 

Any other info about this is also welcomed. 

(NB - I realsie that you have to ensure the appropriate kernel is installed for dual core technology to be utilised. This is not an issue with Edgy or the Fawn as the generic kernel uses dual core. Dapper however requires the K7 or 686-SMP kernel. )

Thanks 

Ted

---

### Post by zgornel on 2007-05-04
> **Ted_Smith said:**
> Hi

Does The GIMP utilise dual processors (specifically two seperate processors as opposed to a dual core single processor - similar, but not the same). 

I don't mean if I open one file and while waiting for that to load I do something else with the Gimp and it use a different processor. What I mean specifically is, say I am applying a filter that's going to take ages and is quite intensive, will The GIMP spread the load across the two CPU's to speed it up or will it just use the one to conduct that specific task? 

Any other info about this is also welcomed. 

(NB - I realsie that you have to ensure the appropriate kernel is installed for dual core technology to be utilised. This is not an issue with Edgy or the Fawn as the generic kernel uses dual core. Dapper however requires the K7 or 686-SMP kernel. )

Thanks 

Ted

Yes, the Gimp should use BOTH processors for a single task, otherwise it would use only one core. You might try some benchmarks (trivial ones) on some very big images (50-100 Meg). However, the dual processor/core support is available only in the 2.3.x branch of gimp from what I know. Good luck.

---

### Post by stmiller on 2007-07-05
Gimp only uses one CPU for heavy filtering here, unfortunately. Gimp 2.2.13. Looking forward to the SMP branch.

---

### Post by Hairy_Palms on 2007-07-06
yes 2,2,13 will use only 1, the dual core support is in the development 2.3.x branch.

---

### Post by Half-Left on 2007-07-06
Yep and it's way faster, a few seconds to do iwarp filter instead of over a minute.

---

### Post by zgornel on 2007-07-09
> **Half-Left said:**
> Yep and it's way faster, a few seconds to do iwarp filter instead of over a minute. Excellent ! Provided you have a dual core/dual processor system :(

---

