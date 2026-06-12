---
title: "Un-fry MBR"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by m.musashi on 2006-01-25
Okay, after many successful installs I'm stuck. Ubuntu won't install on a new AMD64 system (various problems that I won't go into here). I did get far enough to install GRUB to dual-boot with Windows. However, GRUB was somehow corrupted and I used my Windows CD to fix the MRB (via fixmbr) and now it is just fried. Windows is still there but I can't boot.

My questions, therefore, is how to do I repair the MBR (fixmbr doesn't work btw) so I can at least use Windows until I figure out how to get Breezy to install? I'm assuming I need to boot dos or something and manually rewrite the MBR but I don't have a clue how to do that.:confused: 

Thanks.

---

### Post by Zahrber on 2006-01-25
Well do you have a restore disk for the computer, but you will loose all your data.

You can use the Windows disk to reinstall window and this most likely will fix the problem and will keep your data if you don't format or repartition.

Also there is a website about GRUB that may have some info that will allow you to fix GRUB so you can boot Windows from GRUB. 

GRUB is just a BOOTLOADER that will transfer information to the kernel. So it can be used with Windows easily.

Search Google for the website for GRUB and see what you can turn up or do a search for GRUB problems on GOOGLE and see what you can find.

---

### Post by Dragonbite on 2006-01-25
It may be a hassle, but what about going through the complete Breezy install again including grub so it can re-write over everything that's screwed up?

If you can run fdisk (Windows CD? another Linux install CD?) I think the command is ```
fixmbr
```Google found me this link [http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php]("http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php") which I don't know how helpful may be for you.

Here is a another link to a forum talking about removing Grub [http://www.ntcompatible.com/thread28242-1.html]("http://www.ntcompatible.com/thread28242-1.html")It sounds promising since it covers what I think is your problem.

Hope these help.

---

### Post by m.musashi on 2006-01-25
[QUOTE=Dragonbite]Here is a another link to a forum talking about removing Grub [http://www.ntcompatible.com/thread28242-1.html]("http://www.ntcompatible.com/thread28242-1.html")It sounds promising since it covers what I think is your problem.

Hope these help.[/QUOTE]

Thanks, the other forum you pointed to seems promising. However, I have tried the "fixmbr" option and if anything it made it worse (typical Windows). The other forum sugested using the XP install CD and choosing "repair" and then running bootcfg /repair. I did that to no avail. Perhaps I did something wrong or perhaps in my tweaking around I goofed it up even more.

What I'm wondering is how to rewrite an entirely new MBR and have it point to Windows. I thought that is what the bootcfg /repair was supposed to do but it didn't (or I didn't do it right).

Reinstalling Breezey is probably the easiest option but so far I can't get it to install successfully. I have nothing to loose on this machine as it's new and I just got Windows installed (had to because Breezey wouldn't) so reinstalling is an option but it takes at least an hour and if I can fix it I learn something.:p

---

### Post by dueY on 2006-01-25
[QUOTE=m.musashi]Thanks, the other forum you pointed to seems promising. However, I have tried the "fixmbr" option and if anything it made it worse (typical Windows). The other forum sugested using the XP install CD and choosing "repair" and then running bootcfg /repair. I did that to no avail. Perhaps I did something wrong or perhaps in my tweaking around I goofed it up even more.

What I'm wondering is how to rewrite an entirely new MBR and have it point to Windows. I thought that is what the bootcfg /repair was supposed to do but it didn't (or I didn't do it right).

Reinstalling Breezey is probably the easiest option but so far I can't get it to install successfully. I have nothing to loose on this machine as it's new and I just got Windows installed (had to because Breezey wouldn't) so reinstalling is an option but it takes at least an hour and if I can fix it I learn something.:p[/QUOTE]


You tried "fixmbr"... did you try "fixboot" ?

---

### Post by m.musashi on 2006-01-25
[QUOTE=dueY]You tried "fixmbr"... did you try "fixboot" ?[/QUOTE]

To be honest, I don't remember. It was last night (I'm at work now) and I tried several things with "fix" in them and nothing got fixed. Fixboot was probably one of them. I'll try these other suggestions when I get home. I certainly can't make it any worse. Of course, fixboot or fixmbr asked for some feedback from me and I had no idea what to say and that is where it probably made things worse. I know that bootcfg /list now shows three entries with number 2, I think, being Windows. However, at boot I don't get a choice of these three - just an error about inserting bootable media.

UPDATE: Well, it's all a moot point now. I got tired of trying to figure it out and just reformatted the whole thing and started over. Thanks for the help. Clearly the Ubuntu community has a lot going for it.

---

