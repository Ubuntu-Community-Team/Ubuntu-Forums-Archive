---
title: "only 50% load on cpu in gimpshop?"
date: 2008-02-10
forum: Art &amp; Design
---

### Post by secondstage on 2008-02-10
I've been using gimpshop for about a month now and have only gotten around to posting this now. As you can probably tell for the title, whenever i am doing major processes in GIMPshop the CPU load is running from 50 to 55 percent of a load. To get to the point is there anyway to get gimpshop to use more of my cpu.I have a core 2 duo e6550. Is it just that it wasn't coded for dual cores?

---

### Post by red_Marvin on 2008-02-10
That is the most likely answer, yes...

---

### Post by SpiderGorilla on 2008-02-10
I have the latest GIMP via Add/Remove... on my dual-core 64-bit and it shows under File -> Preferences -> Envivornment:

Processors to use: 2

So I'm not sure if it's actually using it, but it's showing the option.

---

### Post by secondstage on 2008-02-10
I went to File>Preferences>Environment, and said that it was to use 2 processors:confused:

---

### Post by red_Marvin on 2008-02-11
Well it can only utilize both cores when it does processing that can be separated into two threads, one for each core, otherwise it won't work.
This is the reason for the common misconseption that more cores => faster computer,
it will only be faster in cases where you want to spread the performance on multiple programs,
or use threaded programs.

---

