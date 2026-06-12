---
title: "What are Ubuntu's hardware limitations?"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Dawn Light on 2007-03-01
I am trying to decide on what hardware to purchase for my new computer. What are my limitations assuming I will want to run Ubuntu? I read something about Linux not supporting [SMP]("http://en.wikipedia.org/wiki/Symmetric_multiprocessing"). Does that mean I should not buy a [dual core]("http://en.wikipedia.org/wiki/Multi-core_%28computing%29")? This is confusing me, please help!

---

### Post by SunnyRabbiera on 2007-03-01
I have heard some folks here having luck with intel dual cores, but the results are mixed.

---

### Post by sloggerkhan on 2007-03-01
I had always thought Unix/Linux based systems were good for SMP. But I guess SMP isn't quite the same as dual-core... I'd be interested on info about this, too.

---

### Post by SunnyRabbiera on 2007-03-01
the best way to find out is to do a search on here, as I said there are reports that dual cores semi work on ubuntu

---

### Post by Steel Bovine on 2007-03-01
fwiw, my dual core works fine in Ubuntu.

---

### Post by annda on 2007-03-01
i just discovered this info in synaptic:

linux-686-smp   Obsoleted by: linux-image-generic

btw: ubuntu properly discovers both processors for me, and they are both scalable (i haven't tried scaling them separately). 

@SunnyRabbiera: what do you mean by "dual cores semi work"?

---

### Post by mcduck on 2007-03-01
My Core Duo works perfectly. So does my friends Core 2 Duo, and the Athlon 64 X2 setup I built for my friend. In general Linux supports multi-core/multi-CPU setups very well, far better than Windows does.

Some people have had problems with Core 2 Duos, but as they seem to work for most people I believe it's more a problem with some motherboard chipsets or something like that.

Hey many of the fastest supercomputers run Linux, you wouldn't think they run on a single CPU, would you?  Current fastest supercomputer, BlueGene/L runs SuSE SLES 9 on 131,072 IBM PowerPC CPUs ;) [http://www.top500.org/system/ranking/7747]("http://www.top500.org/system/ranking/7747")

---

### Post by Dawn Light on 2007-03-01
Thanks! I've also found [this discussion on the subject]("http://www.linuxhardware.org/article.pl?sid=06/10/03/2011238&mode=thread") which is pretty helpful

---

