---
title: "Ubuntu 7.10 PPC bootloader problem?"
date: 2007-12-03
forum: Apple PPC Users
---

### Post by BSVIII on 2007-12-03
Hello everyone.

Im just trying linux for the first time so go easy on me.

The live cd runs great and installation appears to go without a hitch. When I reboot I hold down option to get the options available to me. The Ubuntu installation appears and I click it and then press the arrow to continue. The screen then says something like this.

Press l for GNU/Linux
Press X for OS X
Press C for CD

So I press l and it takes me back to the first selection screen. Its a never ending circle. :confused:

I have OS X on one hard drive and the Ubuntu install on another. Both internal hard drives. 

I think its a problem with the yaboot bootloader. But I dont know because Im so new at this.

Thanks for all your help!

---

### Post by SaltyCrak on 2007-12-03
have you tried swapping the boot sequence of your drives in the bios?

---

### Post by BSVIII on 2007-12-03
I dont even know how to access the bios. Never thought of that. Ill give it a try.

---

### Post by stmiller on 2007-12-06
PowerPC Macs don't have a bios. Sounds like your yaboot is all messed up.

Boot the PowerPC Alternative CD, and then choose rescue mode at the prompt. From there there is an option to 'restore yaboot.' That *should* fix the problem...

---

### Post by ppc_guy on 2007-12-06
It would also help a lot if you told us what kind of mac you have.. They are interesting beasts with a lot of issues with each model. Also it's a side note, but can also help what version of OSX are you running?
That could help trace the boot issue further.

~Nathan
----------------------------------------------------------------------------------------------------------------
When you are Sierra-Oscar-Lima. I'm Hotel-Tango-Hotel.
----------------------------------------------------------------------------------------------------------------

---

### Post by Melodius on 2007-12-09
i also have a problem like this


help!!!

---

