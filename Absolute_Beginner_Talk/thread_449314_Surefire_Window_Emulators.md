---
title: "Surefire Window Emulators"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by Architect on 2007-05-20
Good evening ladies and gents!

Not too long ago I was introduced into the world of Linux and I must say that my short stay has been wonderful! I am absolutely in love with Ubuntu; it's simplicity, it's design, and it's principles. 

Unfortunately, I require a plethora of software which does not run natively on Linux. Some applications and games I simply cannot live without. In my limited use of Ubuntu I have come across several references to Wine and have played with it a little, however I find that it is not very "beginner friendly" and is fairly difficult to use; I know only the basics of Shell commands, though me repertoire is growing quickly =)

Now, my question; is there a simpler, more powerful windows emulator available? I am willing to pay for it AND I have access to Window XP and Vista, so any various DLL's needed will be easily in reach. Even better, is it possible to partition my disk in such a way that I can directly interface with Windows from within Ubuntu?

Thanks very much for your time,
Architect

Edit- Forgot to add; I would prefer if the Emulator was graphical in nature =) I'm still quite "young" in my shell experience and it can be quite daunting, especially from a new Windows converts view =) If the most compatible/ best is shell based in nature, that's ok =)

---

### Post by fjf on 2007-05-20
Vmware server is free, and you can install it from synaptic.  It enables installing a full windoze system in a virtual machine.  If you want more features, you can buy the workstation version.  [www.vmware.com](www.vmware.com)

---

### Post by machoo02 on 2007-05-20
Well....there is no such thing as a Windows emulator.  WINE (which stands for Wine Is Not and Emulator) is more of a compatablility layer.  Think of it as a Rosetta Stone to translate between Windows system calls and Linux system calls.  Your best bet is a virtualization program, where you create a virtual mahchine and install windows into it.  fjf mentioned VMware server, also check out Qemu (in the repos) and [VirtualBox]("http://www.virtualbox.org").

---

### Post by starcraft.man on 2007-05-20
I agree with fjf the best emulator you can get is windows itself in a VM client. I also do endorse VMware, its a good solution with great support for windows and all linux OS. It will let you run windows XP (I wouldn't want Vista in vm >.>) and then you can run any of the apps like PS you need.

This is just a thought, but if you want to game heavily within Linux (you can't game within a VM client like vmware, they will not emulate a top of line video card) I would suggest [Cedega.]("http://www.transgaming.com/index.php?module=ContentExpress&func=display&ceid=2&meid=-1") There are of course, ways to get it with and without paying, whichever suits you.

If Cedega doesn't support your game very well though, you may be forced to dual boot to get it running well enough (i.e. some games are not popular enough to be top priority, some are not coded well, etc....)

Thats about it. If you like VMware server and want a bit more control, the workstation is a great platform.

---

### Post by Architect on 2007-05-20
Thank you for the links, everyone =) I will check them all out. I suppose if none of them suit me well enough, I *may* have to have duel-operating systems =P I hope one of those works with what I need =)

BTW- the games I'll be running are pretty top of the line. Gotta interface with my gfx card. I'll check out Cedega, sounds good =)

Thanks again!
Architect

---

