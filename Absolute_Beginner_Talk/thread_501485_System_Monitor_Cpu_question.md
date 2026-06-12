---
title: "System Monitor Cpu question"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by whatevermortal on 2007-07-15
Hello,  
  
I'm very new to the linux/computing world and have been enjoying Ubuntu for the past few weeks. Looking at the System Monitor this evening and it states that I have two CPU's, just wondering what this may mean as I only consider my box as containing one?  
  
Thanks muchly.

---

### Post by mikewhatever on 2007-07-15
Is your CPU brand Intel CoreDuo or AMD 64x2?

---

### Post by whatevermortal on 2007-07-15
Nope, it is an Intel Pentium 4 2.80ghz.

---

### Post by mikewhatever on 2007-07-15
That is odd. Can you post a screenshot.

---

### Post by whatevermortal on 2007-07-16
Sure thing have attached a shot. I also notice that in the System tab there are two processors under hardware names 0 and 1. My system is randomly freezing up and I wonder if this may have something to do with it all.

---

### Post by 5-HT on 2007-07-16
Hyper-threading? If so, it would be doubtful that it's the cause of the freezing. Does the whole system lock up or just X: your video driver perhaps?

---

### Post by whatevermortal on 2007-07-16
I've not encountered the term Hyper-threading before, but after a quick search it seems doubtful. Is it something a user has to initiate or can it be out of the box on a processor?   
  
I think its the entire computer, a nice solid red light shows up on the hard disc light that shines from the front of the case. Often it isn't actually able to boot into linux at all.

---

### Post by mcduck on 2007-07-16
Some P4 models have hyperthreading, it's not anything you'd have to do anything about, it's a feature of the CPU itself.. That explains the 2 CPU's showing in the system monitor.

Anyway, Hyperthreading is very unlikely to be the cause for your freezing problem. If you have problems even at booting there's probably some other hardware issue. I'd say dying harddrive or either motherboards power cirquitry or the PSU are dying.

---

### Post by whatevermortal on 2007-07-16
Strangely enough the motherboard did die about 6 months ago and I have replaced it. The only reason I was thinking it could be an issue with Ubuntu stems from the fact that I've run win xp for the last 6 months with no breakdowns. The freezes have only occurred since installing Ubuntu a few weeks back. I shall open up the box and have a look around later tonight for any issues.

---

### Post by mcduck on 2007-07-16
> **whatevermortal said:**
> Strangely enough the motherboard did die about 6 months ago and I have replaced it. The only reason I was thinking it could be an issue with Ubuntu stems from the fact that I've run win xp for the last 6 months with no breakdowns. The freezes have only occurred since installing Ubuntu a few weeks back. I shall open up the box and have a look around later tonight for any issues.

Linux is generally less forgiving with hardware problems than Windows is. Linux will give you errors and stop working if there's something wrong with your system, while Windows keeps on going, probably crashing every now and then and perhaps doing errors in calculations and sometimes corrupting some files and so on..

---

### Post by whatevermortal on 2007-07-16
That would make sense then. Will have a look around later tonight and hopefully see if something is amiss. I did notice a CMOS error the other day so perhaps I need to replace the battery. Is there a way to check cpu temps and fan speeds via the terminal? I did attempt a sensors command recommended in another thread though nothing occurred.

---

### Post by mcduck on 2007-07-16
> **whatevermortal said:**
> That would make sense then. Will have a look around later tonight and hopefully see if something is amiss. I did notice a CMOS error the other day so perhaps I need to replace the battery. Is there a way to check cpu temps and fan speeds via the terminal? I did attempt a sensors command recommended in another thread though nothing occurred.
That depends on what your motherboard can do. On my laptop 'apic -V' gives fan speeds and teperatures, and on my older desktop machine I had to install lm-sensors (which provides the 'sensors'-command) to get any readings.

---

### Post by j2fraser on 2007-07-16
> **whatevermortal said:**
> Nope, it is an Intel Pentium 4 2.80ghz.
Are you sure you don't have a [Pentium D]("http://en.wikipedia.org/wiki/Pentium_D")? That would explain things...

---

