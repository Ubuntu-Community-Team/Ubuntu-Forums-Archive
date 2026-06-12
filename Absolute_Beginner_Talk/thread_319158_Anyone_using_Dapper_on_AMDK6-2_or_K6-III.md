---
title: "Anyone using Dapper on AMDK6-2 or K6-III"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by davd_bob on 2006-12-15
Is anyone sucessfully using Dapper Drake 6.06(any flavor) on a Super7 mother board.  I want to load it on a K6-II system with a Sis530 chipset?

I have been unsucessful in getting it to boot after install on 2 different  but simular systems and a friend tried but failed on one. ](*,)     I have gotten RedHat 6 to boot and shutdown sucessfully and my friend got Debian to load and run.  I did a bit of surfing the whole Internet and haven't seen a single sucess story with a Socket7 AMD cpu. :-k 

Thanks,
David

---

### Post by public_void on 2006-12-15
I just thought it was my computer. I have an AMD K6-2, socket 7, it installed Dapper fine, then when it restarts there is just a black screen after the progress bar completes. I've tried a couple of distros with varying success:

_Work_
Knoppix Live CD
Damn Small Linux
IPCop
Ubuntu Breezy

_Problems_
Gentoo: Takes two or three restarts to get the install CD to boot properly. After that the install went fine.
Ubuntu Dapper (DVD version, the CD version wasn't booting properly again): Again took two or three restarts for the DVD to boot. The text install when fine. However its the blank screen on restart.
Fedora Core 6: Install seems hangs with installing one of the packages (could be a dodgy DVD, haven't checked yet).

The booting problem is probably a loose IDE cable, I'll have to check sometime.

---

### Post by parkini on 2006-12-15
I was able to get Dapper to work on with my K6.  I didn't have to do anything special to get it to work it just took a while to load the live cd and install.

---

### Post by davd_bob on 2006-12-16
> **parkini said:**
> I was able to get Dapper to work on with my K6.  I didn't have to do anything special to get it to work it just took a while to load the live cd and install.Thanks both of you for answering.
Parkini, What chipset, and how much ram on your sucess?

public_void, same question.  I really want to find out which piece of hardware is causing the trouble.   BTW, both my boards(bios=one phenoex other award) have onboard video and I tried nvidia TNT2 cards, with no luck, before I saw that that card has a compatibility problem.
Its looking like the Sis530 chipset.

---

### Post by confused57 on 2006-12-16
I'm not sure about cheatcodes for Ubuntu, but you might try adding something like this to your boot options:
xmodule=sis

or  

xdriver=sis


I have a newer system with sis chipset and Ubuntu always assigns "vesa" as the video drive.

---

### Post by davd_bob on 2006-12-29
> **confused57 said:**
> I'm not sure about cheatcodes for Ubuntu, but you might try adding something like this to your boot options:
xmodule=sis

or  

xdriver=sis


I have a newer system with sis chipset and Ubuntu always assigns "vesa" as the video drive.

Thanks confused57.  When I get far enough along to figure out where/how to choose boot options I will try your suggestion.

---

