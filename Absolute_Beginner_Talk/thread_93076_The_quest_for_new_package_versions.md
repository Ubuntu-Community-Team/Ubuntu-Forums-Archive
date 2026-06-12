---
title: "The quest for new package versions"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by Erwin Van de Velde on 2005-11-21
(Posted in Ubuntu Repository Support too, perhaps better in place here)

Dear all,
 
 First of all, I'm new to the Ubuntu community, leaving the Mandriva Cooker community due to some annoying issues (not in the least broken repositories and some weird package choices). I was attracted by some reviews and the very lively community.
 
 I'd like to have a system that has new software (hence the former use of Cooker), but in combination with a working system: e.g. the new KDE 3.5 would be nice when it is officially released as KDE is most of the time really stable on official release but the new Xorg 6.9 before it has been declared stable by the Xorg people (as Cooker and even Mandriva 2006 did) can (and in fact did) break working systems... and even on a shiny new system I still have some work to do too you know  :)
 
 So I'd like to know something more about the Ubuntu update policy and all I found was fragmented and confusing.
 I found about the Ubuntu update policy that a released distribution like Breezy only gets security updates and really zero feature updates, is this correct?
 What about the backports? What is backported, when (no Breezy backports yet), etc?
 How stable is Dapper? Is it really bleeding edge like in beta software or is it bleeding edge as in the newest releases?
 
 Last question:
 Is it easy to maintain a mixed system (e.g. Breezy-Dapper)? Howto's? And is this recommendable for my needs? This of course only in the case that Dapper is to unstable and Breezy+backports to old for an adventurous guy like me ;)
 
 Thanks a lot!
 Erwin

---

### Post by Gustav on 2005-11-21
Ubuntu is released every 6th month and after the release it only gets security updates, no feature upgrades.

The backports are programs from the next release (now Dapper) that are tested tp run on the current release (Breezy). It's a somewhat community driven project where you can ask for programs to be backported (although they must exist in Dapper) and then, hopefully, they will be backported after maybe a week of testing.

Dapper is not stable at all and will break several times. Don't use it if it's not acceptable that you won't be able to use your computer for a while. But it might be good to try out when it's release is becoming closer (maybe february, march)

A mixed system is even worse than Dapper since there will be lots of stuff that conflicts with each other (if you're a super hacker you'll might be able to pull it off :))

---

### Post by Erwin Van de Velde on 2005-11-21
[QUOTE=Gustav]
The backports are programs from the next release (now Dapper) that are tested tp run on the current release (Breezy). It's a somewhat community driven project where you can ask for programs to be backported (although they must exist in Dapper) and then, hopefully, they will be backported after maybe a week of testing.
[/QUOTE]

What will be backported? Most important packages like KDE packages? Almost everything/nothing? What can I expect?

[QUOTE=Gustav]
Dapper is not stable at all and will break several times. Don't use it if it's not acceptable that you won't be able to use your computer for a while. But it might be good to try out when it's release is becoming closer (maybe february, march)
[/QUOTE]

What do you call break? Really making it impossible to use the system or stuff like small annoyances? What has been the experience with unstable Ubuntu releases till now?

[QUOTE=Gustav]
A mixed system is even worse than Dapper since there will be lots of stuff that conflicts with each other (if you're a super hacker you'll might be able to pull it off :))[/QUOTE]

Okay... no fun there :)

Best regards,
Erwin

---

### Post by Gustav on 2005-11-21
If there is a program where the breezy version is to old (in your opinion) and a new version is included in dapper you can ask for it to be backported. This goes for any app (but some might be to hard to backport because of conflicting libs and such). The most common apps to be backported are games, firefox and other stuff where you notice that there is a new version.

Dapper will break so that your system is unusable from time to time. Don't use it on your primary computer (unless you don't use your computer for stuff that you need to do)

---

### Post by lhtown on 2005-11-21
Don't expect packages like Xorg or KDE that have huge numbers of dependencies to be backported. 

Backports seems to be mostly for programs that either have few or simple dependencies or very minor upgrades to packages that don't affect dependencies, but might fix an annoying bug or add a really important feature.

I would be shocked for days to see a new version of KDE since it would change everything with its new dependecies. 

I would be surprised NOT to see OpenOffice.org 2.0 stable since a late beta version is included in Breezy. It would be a simple upgrade that would have little or no chance of breaking anything and a lot of people would use it.

---

### Post by Erwin Van de Velde on 2005-11-21
Okay... I'm testing Dapper now on another machine... if it runs stable enough, I think I'll try and switch. In fact, you would think that if the KDE people are able to release a stable KDE that packaging it would not break everything. However this seems a huge problem in many distributions.

Apart from that, they said that Cooker was unstable too and it was often as stable or even more stable than the stable releases. Only a few things were messed up in the year I used it, mostly missing buttons or minor issues. The only real problem was a printing problem that lasted two weeks. I do understand that these minor problems can happen and most of the time I know enough of Linux to fix it myself anyway.

Let's hope the test machine keeps on running nicely :)

Best regards,
Erwin

---

### Post by tokyovigilante on 2005-11-22
KDE 3.5 RC1 is available now for the current stable release (Breezy 5.10), see [http://www.kubuntu.org/announcements/kde-35rc1.php]("http://www.kubuntu.org/announcements/kde-35rc1.php"). I can vouch for the stability of these packages based on a week's reasonably heavy use without a crash.

It will be available in Dapper shortly (within the next week or so). As others have mentioned the Stable release in Ubuntu is reasonably cutting edge, being based on Debian Sid. Dapper is intended primarily for developers to work with a live system, and for those braver members of the community to test and provide feedback. It's not really for those who want an easy stable system.

Currently Dapper is at the stage of integrating new versions of software from the past 6 months, and as these have varying dependencies which are at this stage only somewhat resolved, most problems you'll strike relate to versioning and dependencies.

---

### Post by Erwin Van de Velde on 2005-11-22
[QUOTE=tokyovigilante]KDE 3.5 RC1 is available now for the current stable release (Breezy 5.10), see [http://www.kubuntu.org/announcements/kde-35rc1.php]("http://www.kubuntu.org/announcements/kde-35rc1.php"). I can vouch for the stability of these packages based on a week's reasonably heavy use without a crash.
[/QUOTE]

It is great that those packages have been released, but how long will they continue to work? I can imagine that an update in Breezy could break these packages accidently and there is no guarantee that new KDE 3.5 packages will be released.

[QUOTE=tokyovigilante]
It will be available in Dapper shortly (within the next week or so). As others have mentioned the Stable release in Ubuntu is reasonably cutting edge, being based on Debian Sid. Dapper is intended primarily for developers to work with a live system, and for those braver members of the community to test and provide feedback. It's not really for those who want an easy stable system.
[/QUOTE]

It does not have to be completely easy and stable, but neither hard and crashing all the time :)

---

### Post by tokyovigilante on 2005-11-23
> I can imagine that an update in Breezy could break these packages accidently and there is no guarantee that new KDE 3.5 packages will be released.

The fact that these packages are released for the stable version implies that they will be maintained and supported. Once 3.5 final is released I would imagine that they would recieve bug-fix and security updates only, in the same way KDE 3.4 is supported. 
> 
It does not have to be completely easy and stable, but neither hard and crashing all the time.
Again it's likely you will run into severe bugs and incompatibilities with Dapper, it's really not intended for desktop use at the moment. As an example, yesterday's gcc-4.0.1->4.0.2 transition introduced an inadvertent ABI breakage, leaving half my software unable to execute (including Firefox and Firestarter). These will be rebuilt and fixed over the next few days, but it's not really a solution for people who want things to Just Work. 

If you're really keen to try Dapper over Breezy, set up a separate /home partition and run both, so if Dapper breaks you can reboot into Breezy and keep working.

I hope I haven't put you off, running Dapper is fun ;), but if you just want to get some work done, I'd recommend you run the stable Breezy release. KDE 3.5 will get support through the Backports, and I'm sure dapper will be a lot more stable over the next couple of months.

---

