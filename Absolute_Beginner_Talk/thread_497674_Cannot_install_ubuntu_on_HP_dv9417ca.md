---
title: "Cannot install ubuntu on HP dv9417ca"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by o.besner on 2007-07-10
Hi, 

I am a Vista User that is trying to switch to Ubuntu, but it seems I can't. I have a friend currently running Feisty Fawn, and he said he never saw something like that.


I managed to install Ubuntu from the DVD (64 bit release) , but only using text mode. Once installed, the OS won't boot : It will freeze, but not always at the same moment. There is 3 possible "Freezing Point"

- During " Loading Hardware Drivers"
- During "Setting up Network"
- If it finally manages to boot, I get a Black Screen of Death.
Quite odd, isn't it ? 

This is the entire hardware inside my HP 9145ca :

- AMD Turion 64 Tl-56
- 2 Gb of Ram
- 160Gb HD
- Geforce 6150 (559 Mg Shared)
- My wireless card is a Broadcom 4320 G and Draft-N

It's my first time running Linux, but I know Windows by heart, so any comparisons would be useful. 

Anything else you need to know, I'll try to salvage it. I used the Ubuntu 7.04 DVD for X86-64. I also tried with the Ubuntu CD for X86-64.

Vista was running fine, so it's not the hardware. I just like to try new things, and break what's already working.

---

### Post by thefoolisme on 2007-07-10
> **o.besner said:**
> Hi, 

I am a Vista User that is trying to switch to Ubuntu, but it seems I can't. I have a friend currently running Feisty Fawn, and he said he never saw something like that.


I managed to install Ubuntu from the DVD (64 bit release) , but only using text mode. Once installed, the OS won't boot : It will freeze, but not always at the same moment. There is 3 possible "Freezing Point"

- During " Loading Hardware Drivers"
- During "Setting up Network"
- If it finally manages to boot, I get a Black Screen of Death.
Quite odd, isn't it ? 

This is the entire hardware inside my HP 9145ca :

- AMD Turion 64 Tl-56
- 2 Gb of Ram
- 160Gb HD
- Geforce 6150 (559 Mg Shared)
- My wireless card is a Broadcom 4320 G and Draft-N

It's my first time running Linux, but I know Windows by heart, so any comparisons would be useful. 

Anything else you need to know, I'll try to salvage it. I used the Ubuntu 7.04 DVD for X86-64. I also tried with the Ubuntu CD for X86-64.

Vista was running fine, so it's not the hardware. I just like to try new things, and break what's already working.

Did you run the CD checks before installing?  You have to burn the CD/DVD at a really low speed (4x) to ensure it's integrity.  

FYI - don't look for comparisons between Windows and Linux.  They are 2 completely different systems, and if you are always looking for comparisons, it will be harder for you to get.  Look at Ubuntu with a "blank slate" open mind.  :-)

---

### Post by benjamin1254 on 2007-07-10
that to me seems strange. You should have more then enough of everything. I know when i had my system an amd 1800+ xp processor with 256 megs of ram my system was stable and i was in love with the OS. So hearing it freak out like that could mean its just having driver freak outs. I had another system which did that as well. I just had to disable drivers on boot up. It was my wireless card that freaked on me after a while of figuring out what it was. Ubuntu works better wired in my opinion so it would be best to try that rather then a wireless configuration. But to answer your question yeah it is odd for Ubuntu to act the way it is and it should be fine. I would try a cd version of the latest and see if it screams at you again and if it does let me know. :biggrin:

---

### Post by buzzmandt on 2007-07-10
had very similar problem, here's what i had to do
download iso for alternate cd...when booting the alternate cd at the first screen press F6, at the end of the line that comes up enter the following code at the end of the line after the --
"noapic nolapic" (without the quotes)

press enter and install

you could also try the safe graphics mode on the dvd installer you have now, and you can also F6 and add noapic nolapc to that attempt

---

### Post by o.besner on 2007-07-10
Thefoolisme : yes, I did check the integrity of both the DVD and the Cd... I think it's a driver problem.

The alternative install seems like a good idea... I will give it a try. 

Meanwhile, I've installed Opensuse 10.2 and it works almost well (freezing often), but at least I have something showing up on my screen ! 

I'll try the alternative install, and see what it gives. Still, are you sure that by simply adding a command line I won't get another black screen of death once the OS is installed ?

Another question : where can I learn the basic commands for Ubuntu ?

---

### Post by buzzmandt on 2007-07-10
> **o.besner said:**
> 

I'll try the alternative install, and see what it gives. Still, are you sure that by simply adding a command line I won't get another black screen of death once the OS is installed ?

nothing is for sure, it's trial and error, took me about a week and 70000 installs to find the solution to my install problems.....but the more you can narrow it down, the more likely someone else has had and fixed the issue at hand

---

### Post by stepan2 on 2007-07-10
try choosing the option of vesa for raphic roblem fixing , then as bazzmant said ,  use the following commands. You wont have to  ue the alternate cd .  Also , where it says acpi=on , turn it to off

---

### Post by o.besner on 2007-07-10
Jesus, the noapic nolapic line worked !!!! I am installing ubuntu now !!! I'll probably have some new problems later, but still...

I need to know, what does noapic nolapic means ???

---

### Post by nixego on 2007-07-11
o.besner!

I have also just bought this EXACT laptop (dv9417ca from Futureshop, right?) and I also have the need to break things that are already working! As soon as I bough the laptop I wiped the while thing clean. Now I am typing this from a up and running version of kubuntu after the noapic nolapic commands worked magic on my computer. 

I was VERY surprised to see that my LAN card, quick volume controls, and sound were all working RIGHT OUT OF THE BOX. Did you find the same? It was easier to install than XP!

It's cool to see another guy struggling with the exact same linux installation with the exact same laptop at the exact same time. The internet is funny. 

Good luck in your linux future,

-nix

---

### Post by g33kdotinfo on 2007-08-26
good to see it works but won't install ubuntu until i make my back up disc.

was happy to see that the guy got it working cause I have the same laptop I just bought yesterday.

maybe he can come back an update how ubuntu is working on his machine.

I plan on not using vista at all, even though it looks pretty nice, i love ubuntu better.

i use ubuntu on my main pc at home. and want to stick with the greatest nix distro imo.

update us on your ubuntu installation on the laptop guys / gals.

Thanks

---

