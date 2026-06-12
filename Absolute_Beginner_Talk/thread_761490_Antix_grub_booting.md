---
title: "Antix grub booting?"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by vinceUUUU on 2008-04-21
Hello

can anybody help me out with Antix linux distro...it is ubuntu based /debian

i boot thelive CD and then i install Antix and all goes well...

the last step of installation asks me if i want to use grub boot loader...

a) if i answer NO to grub install...then my machine will not boot into Antix

b) if i answer yes to grub install into the root....then Antix won't boot

b) if i answer yes to grub install into the MBR...then the machine boots to a grub prompt and gives no indication of how to boot into Antix itself...

i have tried everything including the listed grub commands from the help....nothing gets Antix to boot up

c) the third option is to install GRUB to the MBR and also click the INITRP setting checkbox....i don't know what this initrp setting is for....should i click this checkbox and try this?

it is mad how Antix boots to grub but then gives no indication of how to boot into the actual Antix OS..

my machine has no other OS's on it...and the linux partitions are totally standard

how do i boot Antix?

thanks

Vince.

---

### Post by zvacet on 2008-04-21
When you install grub on MBR what do you see when grub show up?Kernel number,nothing.......?

---

### Post by vinceUUUU on 2008-04-21
Hello

it just boots up to a senetence of text at the top of the screen...about grub..

and underneath that........ a grub prompt

grub>

nothing appears about how to boot Antix........i don't recall seeing any kernel numbers...no

there are no lists of operating systems installed..no mention of partitions...or anything

Vince.

---

### Post by anticapitalista on 2008-04-22
If you don't get my email reply:

Hello Vincent.

Try re-installing grub into the MBR.
Boot the livecd, go to Admin/Tools->Mepis Admin -> System.

If that doesn't work or gives an error message you may need to re-install.
Before you re-install, make sure you set up your partitions correctly 
beforehand using either gparted, qtparted or cfdisk (type the latter 
in a terminal).

Hope this helps.

Post on the antiX forums if you like, others may be able to help.

[http://antix.freeforums.org/](http://antix.freeforums.org/)

anticapitalista

---

