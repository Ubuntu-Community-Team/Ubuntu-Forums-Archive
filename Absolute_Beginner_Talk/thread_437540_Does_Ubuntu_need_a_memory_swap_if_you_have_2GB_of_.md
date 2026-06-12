---
title: "Does Ubuntu need a memory swap if you have 2GB of ram"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by jonward0690 on 2007-05-08
I have a Dell Dimension E520 with 2GB of ram,does it even need a memory swap, I never use the ram I have so why would need the memory swap when I will never  use it eather

---

### Post by johnnymac on 2007-05-08
Your performance will suffer without some swap...you don't need to equal your memory but you do need some - maybe 512MB or so...

[http://en.wikipedia.org/wiki/Virtual_memory](http://en.wikipedia.org/wiki/Virtual_memory)

---

### Post by tgalati4 on 2007-05-08
A swap partition is handy if you boot with a Live CD (say to rescue a broken system).  It's also handy to test new Live Distros as most will pick up and use the /swap partition if it is available.

More important, what are the speed differences on your system between running with 1 GB vs 2 GB?  Try some different benchmarks (like reindexing your music collection in Rhythmbox) and see if there is an overall speed difference between 1 and 2 GB.  Some folks on the forums would be interested to know.

---

### Post by jonward0690 on 2007-05-08
Well that was handy to know that i should keep that memory swap because the pc never uses it and I thought it was  unnecessary.All see how different my pc runs with 1GB of ram verses 2GB of ram.

---

### Post by vikasrawal on 2007-05-08
Correct me if I am wrong. Hibernate and suspend functions also need swap. 

VR

---

### Post by JesterGr on 2007-05-09
how big swap need to be, for a pc with 1.5 Gb memory to hibernate and suspend properly?

---

### Post by dptxp on 2007-05-09
If you are not really short of Disk space, use swap 1-2 GB.
You can study and change/remove once you are sure of the consequences.

---

### Post by jonward0690 on 2007-05-09
> **tgalati4 said:**
> A swap partition is handy if you boot with a Live CD (say to rescue a broken system).  It's also handy to test new Live Distros as most will pick up and use the /swap partition if it is available.

More important, what are the speed differences on your system between running with 1 GB vs 2 GB?  Try some different benchmarks (like reindexing your music collection in Rhythmbox) and see if there is an overall speed difference between 1 and 2 GB.  Some folks on the forums would be interested to know.

Well I ran my pc with just 1GB of ram there is realy no difference,computer boots a littole slower with just 1GB of ram but it didnt realy run any slower.

---

### Post by 71CH on 2007-05-09
pardon my noobiness but what is a memory swap?

---

### Post by mcduck on 2007-05-09
If you wish to use Suspend To Disk you need to have at least as much swap as you have RAM on your machine.

---

### Post by jonward0690 on 2007-05-09
I have a 5.7 GB memory swap partion don't know why the installer made it so large but I have a 250GB drive so I don't care.

---

### Post by dcstar on 2007-05-10
> **jonward0690 said:**
> I have a Dell Dimension E520 with 2GB of ram,does it even need a memory swap, I never use the ram I have so why would need the memory swap when I will never  use it eather

Unless your loaded processes and programs use up your available RAM, it is doubtful your system will ever use swap space (in any meaningful way).

People still quote the "1.5 to 2 times RAM" swap space mantra, but that dates from a time when RAM was far less used than it is now - you can ignore them and set up your system with either no swap, or just a token amount.

There may be some ill-behaved processes/programs that always try to use Swap space (because they don't trust the O/S to do the Virtual memory management), but in general Virtual Memory (VM) can be considered one entity, and if you have sufficient fast VM (RAM), then you don't need additional slow VM (Swap space).

---

