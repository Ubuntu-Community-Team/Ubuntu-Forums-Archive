---
title: "Dualboot Frying XP?"
date: 2005-09-02
forum: Absolute Beginner Talk
---

### Post by red_Marvin on 2005-09-02
I'm dualbooting XP and Hoary with GRUB (of course) and It has worked almost seamlessly
until recently:

Symptoms:

> When GRUB starts the computer beeps two times those two beeps are also directed
through the speakers, same goes for the POST beep.

> Xp refuses to start. When I choose XP on the Grub menu it says something about
problems during the previous boot and asks if I want to start in failsafe mode.
If I do it goes through some seem-to-be-config files at the bottom of the screen,
and then the screen goes blank with the little white text cursor blinking at the upper
left.
If I don't it goes to the cursor thing immedeately.

Note that Ubuntu and XP are on two different hdd's and I haven't tried to read the
ntfs partition or anything, the only interfering should be done by GRUB.

Previously I have downloaded bzflag and vegastrike for linux and they do occasionally
freeze the computer, forcing a cold reboot. This has once messed up the GRUB
which therefor didn't work and only gave "error 16" or if it was 13. A reinstallation of
ubuntu (and therefor GRUB) did the trick then, but not now.

---

### Post by Kapre on 2005-09-02
[QUOTE=red_Marvin]I'm dualbooting XP and Hoary with GRUB (of course) and It has worked almost seamlessly
until recently:

Symptoms:

> When GRUB starts the computer beeps two times those two beeps are also directed
through the speakers, same goes for the POST beep.

> Xp refuses to start. When I choose XP on the Grub menu it says something about
problems during the previous boot and asks if I want to start in failsafe mode.
If I do it goes through some seem-to-be-config files at the bottom of the screen,
and then the screen goes blank with the little white text cursor blinking at the upper
left.
If I don't it goes to the cursor thing immedeately.

Note that Ubuntu and XP are on two different hdd's and I haven't tried to read the
ntfs partition or anything, the only interfering should be done by GRUB.

Previously I have downloaded bzflag and vegastrike for linux and they do occasionally
freeze the computer, forcing a cold reboot. This has once messed up the GRUB
which therefor didn't work and only gave "error 16" or if it was 13. A reinstallation of
ubuntu (and therefor GRUB) did the trick then, but not now.[/QUOTE]
 red_Marvin,

Is your Ubuntu still booting normal (meaning when you select it from GRUB, it is still doing fine)? If this is the case, then maybe your XP is screwed up.

Try to scan the XP Hd for errors. Also try to check the the BIOS screen if your Hdds are detected correctly.

K

---

### Post by poofyhairguy on 2005-09-02
[QUOTE=red_Marvin]I'm dualbooting XP and Hoary with GRUB (of course) and It has worked almost seamlessly
until recently:

Symptoms:

> When GRUB starts the computer beeps two times those two beeps are also directed
through the speakers, same goes for the POST beep.

> Xp refuses to start. When I choose XP on the Grub menu it says something about
problems during the previous boot and asks if I want to start in failsafe mode.
If I do it goes through some seem-to-be-config files at the bottom of the screen,
and then the screen goes blank with the little white text cursor blinking at the upper
left.
If I don't it goes to the cursor thing immedeately.

Note that Ubuntu and XP are on two different hdd's and I haven't tried to read the
ntfs partition or anything, the only interfering should be done by GRUB.

Previously I have downloaded bzflag and vegastrike for linux and they do occasionally
freeze the computer, forcing a cold reboot. This has once messed up the GRUB
which therefor didn't work and only gave "error 16" or if it was 13. A reinstallation of
ubuntu (and therefor GRUB) did the trick then, but not now.[/QUOTE]


Sounds like your XP install got a little borked. I had to fix something like this a few months ago. Reinstall XP, then reinstall Ubuntu. XP HAS to go first!

---

### Post by red_Marvin on 2005-09-04
The thing is that when GRUB went bonkers the first time it was without XP involved
- only using ubuntu before it stopped working that time.

Fact: The computer has frozen more than once while running bzf.
Fact: After rebooting the computer after said lockup GRUB stopped working.

Conclusion: The lockup has in some way made the computer write to the GRUB
part of the hdd.

Speculation: A lockup of the same kind has in some way made the computer write to the winXP part of the hdd.

---

### Post by ubuntme on 2005-09-05
you can 'repair' your XP using the XP instalition disk.

But this will also kill your grub.  In which case you will have to repair grub with the ubuntu instalation disk.  There is a how to on this somewhere....

---

