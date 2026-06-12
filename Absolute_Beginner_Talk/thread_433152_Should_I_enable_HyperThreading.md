---
title: "Should I enable HyperThreading?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by noob12345 on 2007-05-04
I have a HP Pavilion a340n 
it has a Pentium 4 2.6Ghz processor with hyper-threading
(more info at [http://h10025.www1.hp.com/ewfrf/wc/prodinfoCategory?lc=en&cc=us&lang=en&product=374776&dlc=en](http://h10025.www1.hp.com/ewfrf/wc/prodinfoCategory?lc=en&cc=us&lang=en&product=374776&dlc=en))
I've read that hyperthreading is disabled on ubuntu by default, because of a security flaw concerning servers and computers with multiple users
I only have one, so I don't think that applies to me

My question is, what kind of performance increase can I expect? (I only want faster start up times on applications such as firefox, synaptic, terminal, networking, etc.) 

And, is there any other issues with ht on Ubuntu? Will it cause instability? Can it possible cause my computer to not start up or crash more often?

all i need to know is if ht is worth it.
thanks for your opinions


O, and is there an easy way to overclock the cpu or other devices on Ubuntu?

---

### Post by powder on 2007-05-04
Hyperthreading is enabled and disabled at the BIOS level so I don't see how it could be disabled by default in Ubuntu.  The only change it will make in Ubuntu is whethor or not SMP will be enabled in the kernel.  If I were you I would leave HT on.

Overclocking must also be done at the BIOS level.  There is no software that's going to help you accomplish this.

---

### Post by noob12345 on 2007-05-05
then what's this for?: [http://ubuntuforums.org/showthread.php?p=895077](http://ubuntuforums.org/showthread.php?p=895077)

---

### Post by powder on 2007-05-08
The information in that post is outdated and quite hard to believe in my opinion.  You wouldn't get a performance increase by just editing GRUB (the boot loader).  If you have HT enabled in the BIOS, the new generic kernel will enable SMP automatically.  Off you go.

---

### Post by GhettoFish on 2008-01-31
Well if you run "dmesg | grep CPU" you get this little line.
> [   14.568208] CPU: Hyper-Threading is disabled
This should indicate that HT isn't enabled as deafault, right? :)

---

