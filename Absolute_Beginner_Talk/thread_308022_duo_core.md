---
title: "duo core"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by new_foo on 2006-11-27
I just installed dapper on my laptop which has a centrino duo core thing.  Now I've read there is a special kernal which takes advantage of mutiple processors.  Have any of you given it a try?
Does it seem better than the kernal that doesn't support more than one procesor?  Just looking for a before and after opinion.

Thanks

---

### Post by cilynx on 2006-11-27
My experience:

On my true dual machine (2x PIII 750), using the SMP (symetric multi-processing) kernel makes a world of difference as one processor sits idle otherwise.  Multi-threaded compiles and such are substantially faster with SMP enabled.

On my hyperthreaded machine (1x P4 2.8GHz HT), the SMP kernel makes almost no difference.  All in all, I was disappointed with HT.

Based on my bad experience with HT as well as my general aminity to AMD, all of my new machines are AMD64.  I have not had a chance to test out a Core Duo with and w/o SMP.

---

### Post by richiewrt on 2006-11-27
I am interested in learning this also, as i have ubuntu on my desktop, and I am thinking of putting it on my laptop which has a core duo.

---

### Post by mcduck on 2006-11-27
yes, multi-core cpu's really benefit from using both cores ;)

To get that working, install package 'linux-686-smp' and reboot.

---

