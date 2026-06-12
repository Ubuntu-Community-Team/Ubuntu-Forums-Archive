---
title: "Windows not Booting"
date: 2013-01-24
forum: Any Other OS
---

### Post by kc100 on 2013-01-24
Hi guys,
I hope this is the right way to do this and I'm not jacking this thread.

I have windows 8 and linuxmint installed dualbooted. I've tried heaps of different things to fix my issue of windows now failing to boot 0xc00000f error etc. So I can't tell you exactly my steps to my current dilemma. I have since deleted all the linux repairs. So I have the 200mb boot partition and the main ntfs drive which I can still acess from linux live boot just dandy. I have a windows 8 RC disc, so I tried automatic repair and a few other things in the command prompt there but to no avail.

 I have one of these, [http://paste2.org/p/2793336](http://paste2.org/p/2793336). If you need anymore information I can probably answer. Thanks so much for your time.

---

### Post by howefield on 2013-01-24
Post split off to its own thread and also moved to the "*Other OS/Distro Talk*" forum.

---

### Post by offgridguy on 2013-01-24
You probably won't get much response in this sub-forum considering your choice
of title.  A new thread in Installation and Upgrades, with a title that describes
your problem, example; Failure to Boot;  would probably do better.

---

### Post by oldfred on 2013-01-24
Changed title. 

Windows boot loaders boot only the partition with the boot flag. But you have boot flag on the 200MB partition but it has no boot files. It normally has bootmgr & /boot/BCD.

But you have the bootmgr &  BCD in your main install in sdb2, so move boot flag to that partition.

Windows often only auto repairs the partition with the boot flag, so you may need to run repairs again.

---

### Post by kc100 on 2013-01-25
Thanks, I didn't know about the boot flag thing. The boot flag was on the 200mb partition, but for some reason moving it to my main C partition was enough to finally allow the automatic repair off the boot dvd to work. it took a few times and a few hours to do its thing. Thankyou.

---

### Post by oldfred on 2013-01-26
Glad it worked. 

Generally the first small partition is hidden in Windows (no drive letter) and is just boot files and a repair console, so if you have issues in the main install you may be able to repair from boot/recovery partition. As long as you have a repairCD or flash drive you should be fine.

---

