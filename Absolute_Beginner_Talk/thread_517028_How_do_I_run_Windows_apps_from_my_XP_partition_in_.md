---
title: "How do I run Windows apps from my XP partition in Ubuntu (aka wine sucks)"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by jonsayer on 2007-08-04
I have tried to use WINE to run various windows programs in Ubuntu, but they just seem to refuse to work. The only program i have gotten to work is Sim City 2000, and even that broke after a while. 

I have read about people using programs like VMWare and Virtualbox to do the same thing (I don't mean running the whole OS in a window, I mean just running a program). I tried to boot my Windows partition in VMWare, but all I got was a blue screen of death... 

how do I do this? All I want to do is play Civ 3 in Ubuntu...

---

### Post by splintercellguy on 2007-08-04
You would be better off dual-booting XP. Running a VM = degraded performance.

---

### Post by jonsayer on 2007-08-04
I already have a partition. 

I know there is a way to do this. Anyone out there? Please. I've been trying hard for months, but i can't figure it out.

---

### Post by bodhi.zazen on 2007-08-04
What have you tried ?

Error messages ?

[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

Only I would NOT use Ax ...

---

### Post by callan79 on 2007-08-04
> **jonsayer said:**
> I already have a partition. 
I know there is a way to do this. Anyone out there? Please. I've been trying hard for months, but i can't figure it out.


I'm in a similar position, where I need to occasionally run apps that just won't work under WINE.

For the basic apps I have VirtualBox installed and I just boot WindowsXP inside Ubuntu and it works fine. But I have not tried games in there.

For larger games and apps, I just reboot my machine into Windows (dual boot) and I have the driver from [www.fs-driver.org](http://www.fs-driver.org) installed in Windows so I can read my ext3 partitions.

I don't really think there is any other way...

Callan

---

### Post by asmoore82 on 2007-08-04
> **jonsayer said:**
> I already have a partition. 

I know there is a way to do this. Anyone out there? Please. I've been trying hard for months, but i can't figure it out.

it's actually much easier to virtualize when you don't already have a partition.

if you wish to force the use of an existing partition you have to setup multiple hardware profiles
on the Winders "OS" because it will see an almost completely different set of hardware inside
the virtual machine.

after you play around with WINE setups a few times you learn to use the Cedega trick ...
give each major app you want to run its own environment...
```
~ $ rm -rf .wine
~ $ mkdir .wine-base
~ $ ln -s .wine-base .wine
```

then get WINE configured to your liking with usable fonts and base software - no games -
and change environments ...
```
~ $ cp -rv .wine-base .wine-simcity
~ $ ln -sf .wine-simcity .wine
```

then install simcity and get it working and change again ...
```
~ $ cp -rv .wine-base .wine-civ3
~ $ ln -sf .wine-civ3 .wine
```

then install civ and get it working.

now you can run whatever you want just as long as you point .wine to the right place first
and there is no chance that either will interfere with the other. If all else fails you can always
re-copy wine-base and re-install just the game that screwed up.
and you can re-copy wine-base to experiment to get another game running without worrying
about breaking the games you already have working.

---

