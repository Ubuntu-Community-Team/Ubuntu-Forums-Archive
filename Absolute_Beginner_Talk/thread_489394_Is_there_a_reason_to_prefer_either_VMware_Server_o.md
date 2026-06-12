---
title: "Is there a reason to prefer either VMware Server or Virtualbox?"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Eggnog on 2007-07-01
I'm not trying to get a flame war going here.  I've just reinstalled Ubuntu with a /home partition and now I am going to install Win XP on a virtual machine.  There are a few apps that are indispensable to me, Quicken being one of them, and Quicken doesn't seem to play well under Wine or Crossover.

Before I reinstalled I briefly installed Win XP on VB, and then later on VM, just to play around with each one.  Both were easy to set up and the OS installed without any problems.  I had Quicken up and running on each but I didn't really get a chance to test out many of the features of either VM or VB beyond that.  I did, however, manage to get the USB controller working in VMware but never even looked at that capability in VB because I hadn't thought about it when I had the OS in VB.

The questions I have are mostly basic.  Do people generally prefer one over the other, VB or VM Server, for running Win XP under Ubuntu?  Is one more stable than the other?  Does one handle various apps and devices better than the other?  Is one preferred for loading the odd game or two on?

Just looking for general impressions from people who have used both.  Thanks in advance.

---

### Post by Nekiruhs on 2007-07-01
I think  VMWare Server is a bit easier to configure and troubleshoot than Vbox, having used both. Also, VMWS seems a bit faster than Vbox, and you can emulate 64 Bit OSes in VMWS.

---

### Post by bodhi.zazen on 2007-07-01
vmware is a more "mature" product.

---

### Post by mig5 on 2007-07-01
I prefer VMware server because it is easy to configure and get the sound working.  However, one weird thing about it is that Clamav thinks my Windows 98 virtual machine is a Kill CMOS virus.  This isn't true, as I've done checks inside the virtual machine and they turned up nothing.  I also tried other antivirus programs in my host OS and they didn't say that the virtual machine was a virus either.  It's probably something to with the virtual BIOS that VMware has, seeing as Kill CMOS is a virus that messes with the BIOS.
Anyway, I've never tried Virtualbox.  In difference to VMware, it's open source, so that's a plus.

---

### Post by LGer on 2007-07-01
I have a Windows XP VM inside of VirtualBox that just does not stay running. It "aborts" at random. Seems that this is a somewhat common problem.  Have seen a lot of posts but no solutions. I also run VMWare server and it is as solid as a rock running the same programs. I would prefer to run VirtualBox - being open source - but it has a few bugs to work out before I would trust it for anything serious.

---

### Post by Eggnog on 2007-07-01
You say this Virtualbox problem is happening to others, too?  If so, it sounds wise to perhaps avoid VB for a while until the issue gets sorted out.  How about other features?  Is USB support easy to configure?  Sound?  Anything else of note?

---

### Post by AndyCooll on 2007-07-01
Can't say I've heard of others having "abort" problems with VirtualBox, indeed lots of people love it. And interestingly, in the threads I've read users state its faster than VMware. I personally haven't really been able to tell the difference.

VMware is more mature since it's been around longer, but is only "free" as in beer. VirtualBox is "free" as in freedom. So ...takes your pick really.

I personally prefer VirtualBox for the "freedom" reasons, however my XP image is a VMware one since that's what was around at the time. And I can only speak from personal experience and state that USB and sound work fine in both Virtualbox and VMware for me, and without any problems.

:cool:

---

### Post by LGer on 2007-07-01
> **Eggnog said:**
> You say this Virtualbox problem is happening to others, too?  If so, it sounds wise to perhaps avoid VB for a while until the issue gets sorted out.  How about other features?  Is USB support easy to configure?  Sound?  Anything else of note?

Everything configures perfectly for me. Actually both do - VMWare Server AND VirtualBox. I would prefer to go with VirtualBox only because it is open source. I like them both. Once I get this "abort" issue cleared up I will probably use VirtualBox exclusively. I have the problem posted on the VirtualBox forum and will wait to see where that leads me. I would guess that there are not many with this problem but I had no trouble finding them. My suggestion.... for what it's worth.... Give VirtualBox a try - VERY easy to install. Most everyone that uses it seems to love it.

---

### Post by dotancohen on 2008-03-15
I am now using virtualbox and I do not have any "abort" problem. In fact, it seems less resource intensive than the VMWare server it is replacing, and the desktop integration is amazing (variable guest resolution! brilliant!). It was easy to set up a shared folder between the host and guest. I have not yet tested USB or sound.

---

