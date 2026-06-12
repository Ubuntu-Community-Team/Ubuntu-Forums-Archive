---
title: "Dapper PPC installer issues"
date: 2006-07-19
forum: Apple PPC Users
---

### Post by king_arthur on 2006-07-19
Hi everybody,

I have been checking out Dapper and I am sorry to say that I found some (minor?) short comings.

Herewith following a few notes on my ppc experience on  G4 iMac.[LIST=1]
[*]The new installer does not allow installing on an internal partition. This used to work with Breezy and the old (debian style) installer but not anymore. You could wipe out a partition from the internal HD and let the installer fill the available space with bootloader, swap and ext3 all automatically. This is not possible anymore and I had to install Brezy first and upgrade to Dapper through the internet.
[*]Installing on external FW also does not work. This is an old issue and has been reported several times. It should be only a matter of adding FW support into the kernel image. I wonder why it has been overlooked again.. :(
[*]Once the install is complete and working, my HFS+ partitions are not accessible. Mind you, the kernel has HFS support but it seems to be a permissions problem as I can see my OSX partitions but cannot browse them.
[*]The splashscreen (during boot) is gone. The Breezy one was working albeit in (ugly) low resolution. Now, after Yaboot triggers the boot system, I get a short message stating that the kernel image is being loaded and nothing else for a few minutes untill the familiar GDM screen takes over again.
[*]Airport support is build in but not working on the live CD. I had to **$sudo mdoprobe airport** to get my WiFi into life.[/LIST]I wonder if it's just me experiencing those problems or somebody else is. 
I am grateful to the developing team but it is to say that regretfully the PPC version is still well behind it's 386 counterpart. 
What a pity...

/P

---

### Post by Skia_42 on 2006-07-19
I came across the same problems as well but they're easily solvable. Simply install Breezy and then upgrade.

---

### Post by king_arthur on 2006-07-20
> **Skia_42 said:**
> I came across the same problems as well but they're easily solvable. Simply install Breezy and then upgrade.

I was not asking for help, thank you. I have Dapper up and running. :)
[quote=king_arthur]This is not possible anymore and I had to install Brezy first and upgrade to Dapper through the internet.[/quote]

I just wonder why things have got worse instead of improving with the new release and if anybody else could confirm this...

/P

---

