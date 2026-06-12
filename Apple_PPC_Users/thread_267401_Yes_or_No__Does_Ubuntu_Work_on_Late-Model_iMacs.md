---
title: "Yes or No:  Does Ubuntu Work on Late-Model iMacs?"
date: 2006-09-28
forum: Apple PPC Users
---

### Post by wagerrard on 2006-09-28
Does Ubuntu -- Dapper or Edgy -- work on late-model iMac iSight G5's?

Does any Linux?

By "work" I mean install from CD/DVD without building a new kernel.  I've seen several threads here discussing how to build a new kernel on a PowerMac or early iMac in order to deal with the fans or the aound card.  But that guidance is useless if you can't get a bootable kernel installed in the first place.

I've tried booting the install disk of just about every PPC version I can find on my iMac and none, as in zero, can manage  to load their kernel.

---

### Post by lonce on 2006-09-28
I have never tried it but if you search the forums I am pretty sure its easily possible.  It has been done many times.  Just do a search and you will find out anything you need.

---

### Post by wagerrard on 2006-09-28
I have searched these forums, and several others.  Everything I've found pertains either to PowerMac G5's or the earlier model iMac G5 machines.  I've never seen anyone, anywhere, report a successful install of Linux on the last revision of the iMac iSight machine. I have seen several reports outlining how people installed on one of those earlier machines, and then rebuilt the kernel to bring in the fan drivers and, sometimes, audio.  But, of course, you can't rebuild the kernel unless you can get one installed on the machine in the first place. 

I'll repeat to be clear:  Every kernel on every PPC distribution install CD/DVD I've tried has failed to boot. It's pointless to talk about kernel rebuilds if the kernel on the install medium fails.

---

### Post by stmiller on 2006-09-29
> I'll repeat to be clear: Every kernel on every PPC distribution install CD/DVD I've tried has failed to boot. It's pointless to talk about kernel rebuilds if the kernel on the install medium fails.

This has been discussed here in the past. Boot with the alternate CD (goes to text mode). After it installs, you then have to fetch and compile the latest kernel from kernel.org.

The default kernel on the ubuntu CD is just a generic powerpc kernel, which works for G4 machines. That kernel image does not support G5 machines. No sound, no video (on iMacs), and no thermal support (fans out of control).

I imagine future versions of ubuntu will work 'out-of-the-box' on mac G5 machines. Until then, you have to compile.

Ask or browse on the gentoo PPC forum. Lots of kernel hackers/developers for PPC Linux read and post there. They know their stuff.

---

### Post by kulath on 2006-09-29
There are three problems with Dapper for the iMac iSight G5:

(1) sound causes the machine to hang. This is common to all the G5s. It can be circumvented by commenting out the sound driver in /etc/modules. It can be solved by a newer kernel.

(2) the graphics don't work (e.g. in X). This is specific to the iMac iSight G5. The other G5s are OK. This can be largely circumvented by using a hand-crafted xorg.conf (e.g. from Etienne Barsac's website) though maybe some of the more subtle aspects of graphics do not work properly. There is no fix yet for the iMac iSight G5.

(3) The fans run at full speed. This is common to all the G5s. This can be fixed for the other G5s by a new kernel. There is no fix yet for the iMac iSight G5.


Beware, because some of the words you will find on the web do make a sufficient distinction between the varieties of G5 (or between the subtleties of the specific faults).

(Of course, I would love to put bug references against each of these faults, but the bugs are also not sufficiently precise).

---

### Post by ssam on 2006-09-30
there is this bug [iMac G5 will freeze after booting up]("https://launchpad.net/bugs/23445"), which you might want to read.

---

### Post by wagerrard on 2006-09-30
Appreciate the replies. I've been scouring around looking for posts on this issue and agree that a lot of them don't distinguish between the various incarnations G5 machines Apple has released.

I'm not averse to doing a kernel compile, I've done it often enough on Intel machines.

---

