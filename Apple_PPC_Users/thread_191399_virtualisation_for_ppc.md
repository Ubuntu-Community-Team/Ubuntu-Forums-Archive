---
title: "virtualisation for ppc?"
date: 2006-06-07
forum: Apple PPC Users
---

### Post by ubuntubrian on 2006-06-07
Are there any new virtualisation options for the ppc? Qemu doesn't work on my TiBook and I noticed Synaptic shows some VMWare-player modules and kernels but no player itself.

---

### Post by dpny on 2006-06-07
[QUOTE=ubuntubrian]Are there any new virtualisation options for the ppc? Qemu doesn't work on my TiBook and I noticed Synaptic shows some VMWare-player modules and kernels but no player itself.[/QUOTE]

I just asked a similar question. For now there don't seem to be any. Q, a cocoa version of QEMU, hopes to have PPC vistualization in the future.

---

### Post by onehotcutey on 2006-06-08
Try Mac on Linux - it's in the Repos and let's your run MacOS or OS X with in linux.

I have it running on my TiBook G4

---

### Post by swartzfeger on 2006-06-08
[QUOTE=onehotcutey]Try Mac on Linux - it's in the Repos and let's your run MacOS or OS X with in linux.

I have it running on my TiBook G4[/QUOTE]

Pardon my ignorance -- what's 'Repos'?

---

### Post by projectle on 2006-06-08
If I remember correctly, MOL should be in the Dapper "multiverse" repository.

Just add "universe multiverse" to the end of your Dapper line into your /etc/apt/sources file and you should be fine.

---

### Post by onehotcutey on 2006-06-08
Sorry, repo=repositories...

---

### Post by ubuntubrian on 2006-06-08
2 things for "onehotcutey":
1. are you?
2. I have MOL installed and working great. My question was are there any virtualisation options for the ppc/linux platform that is UbuntuPPC-like VMWare-player. I'd like to run x86 distros of linux and BSD on my TiBook.

Thanks for the response though!

---

### Post by hentaidan on 2006-06-08
I have QEMU (from the repos) working fine on an iBook G4.

Any specific problems you are having?

---

### Post by ubuntubrian on 2006-06-08
Hi there. I had posted and you replied to this:
[http://ubuntuforums.org/showthread.php?t=160735](http://ubuntuforums.org/showthread.php?t=160735)
regarding my inability to get qemu working. If you have new insight I waould much appreciate it.
Thanks

---

### Post by onehotcutey on 2006-06-08
Well to answer the first question my wife seems to think so that makes my believe it enough to keep the alias.

For the second question, for what you want I think QEMU is really your only option, as far as I know it's the only setup for PPC linux that will emulate x386 hardware.  

And just to clarify - 

VMWare-player isn't emulate hardware, it create a sudo machine based on the machine's hardware, and currently  it only runs on x86 hardware.  So in essence MOL is the VMware of PowerPC's.  I use VMware at work and run WinXP, Fedora, Ubuntu, Win95, Win98 and EliveCD.

---

### Post by hentaidan on 2006-06-09
[QUOTE=ubuntubrian]Hi there. I had posted and you replied to this:[/QUOTE]

Heh, thought I recognized the name :rolleyes: 

As for new insight, wipe your computer and start again? That usually works for me...

Are you using Dapper? What version of QEMU are you running?

---

### Post by ubuntubrian on 2006-06-10
0.8.0-3 Qemu, Dapper. Don't really want to wipe my install....... but thanks

---

### Post by ubuntubrian on 2006-06-12
Reinstalled QEMU with Synaptic and it works just fine! Have booted several live cd's.
Thanks

---

### Post by dpny on 2006-06-12
Has anyont tried running QEMU, emulating PPC, as a virtual machine? Is it even possible?

---

### Post by EuroCity on 2006-06-12
The big problem with Qemu PPC is that it only emulates Linux 2.4 guests, sofar; and Mac OS X emulation is even worse (MOL is much better, on this front). So, we'll have to wait until Linux 2.6 emulation is fixed and fully supported - which might, maybe, be never, regrettably, now that Apple has moved to the x86 platform (see also the sad story of Mac-On-Mac, alias MOM, which could have been a very good option on Mac OS X!)...

BTW, can one run an up-to-date Linux 2.6 (PPC) guest in MOL? If so, MOL could be a better option than Qemu, at least for the time being...

---

### Post by dpny on 2006-06-12
[QUOTE=EuroCity]The big problem with Qemu PPC is that it only emulates Linux 2.4 guests, sofar; and Mac OS X emulation is even worse (MOL is much better, on this front). So, we'll have to wait until Linux 2.6 emulation is fixed and fully supported - which might, maybe, be never, regrettably, now that Apple has moved to the x86 platform (see also the sad story of Mac-On-Mac, alias MOM, which could have been a very good option on Mac OS X!)...

BTW, can one run an up-to-date Linux 2.6 (PPC) guest in MOL? If so, MOL could be a better option than Qemu, at least for the time being...[/QUOTE]

MOL still doesn't help me, though, as I want to keep OS X as my main OS. The old laptop I was running Ubuntu on died, os my only choice is to use VPC to run Ubuntu i386, which is slow. I've searched high and low for a PPC virtualization solution with no avail.

Hmm. . . Maybe I could run MOL under fink/X11 in OS X, running Ubuntu in a Virtual Machine. . . The mind boggles!

---

### Post by n00bWillingToLearn on 2006-06-17
[quote=dpny]MOL still doesn't help me, though, as I want to keep OS X as my main OS. The old laptop I was running Ubuntu on died, os my only choice is to use VPC to run Ubuntu i386, which is slow. I've searched high and low for a PPC virtualization solution with no avail.

Hmm. . . Maybe I could run MOL under fink/X11 in OS X, running Ubuntu in a Virtual Machine. . . The mind boggles![/quote]

I don't know if you are still there but I have heard that you can actually run gnome / KDE / whatever in OSX. Not just Apples default X11 interface (which is ugly IMHO) but full on gnome. On top of that I think you can also install all of the other applications and libraries (including synaptic) that make ubuntu what it is and that way you can have a solution supior to virtualization and with full hardware support (including accelerated 3D!!). I have never spent the time to actually research this myself but I have been meaning to for a while so if you do it could you post on how it goes?

---

### Post by ubuntubrian on 2006-06-18
I have run MOL on my PowerBook in Ubuntu and then run XOrg and Fink ported apps in MOL. I only do this when I need to access some older files that i created in OS X/Fink ports. I needed to run FLuxbox as the standard KDE or Gnome WM's were to slow in virtualization. It gets a bit nuts with the performance loss. There are some efforts by Ben Reed to port KDE to run native on OS X but the results are still alpha and really pale in comparison to the Fink project. If you don't like Apple's X11then run XOrg or xFree86. Identical to Linux/Unix look, tho Gnome is only at 2.8 while KDE is current. No shadows, transparency in KDE yet and probably never.

---

### Post by dpny on 2006-06-19
[QUOTE=n00bWillingToLearn]I don't know if you are still there but I have heard that you can actually run gnome / KDE / whatever in OSX. Not just Apples default X11 interface (which is ugly IMHO) but full on gnome. On top of that I think you can also install all of the other applications and libraries (including synaptic) that make ubuntu what it is and that way you can have a solution supior to virtualization and with full hardware support (including accelerated 3D!!). I have never spent the time to actually research this myself but I have been meaning to for a while so if you do it could you post on how it goes?[/QUOTE]

I interested in this more for curiosity than anything else: OS X is my main OS, but I had fun mucking around with Ubuntu before my laptop died. From what I've been able to find, there are no options for what I want to do right now. There are two possibilities in the future, Q, a cocoa port of QEMU which hopes to have PPC virtualization in the near future, and Mac on Mac, an OS X port of Mac on Linux, which is still very early aplha software. How the announcement of Apple's switch to x86 will affect these is anyone's guess.

---

