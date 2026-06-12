---
title: "Trying to install Darwin in VB..."
date: 2010-01-23
forum: Apple Hardware Users
---

### Post by JiuJitsu500 on 2010-01-23
Hey all! I don't know where else to post this, but I'm also not sure where else anoyone would know about Darwin. I love Mac, but don't love how difficult it is to virtualize (not to mention the legal issues for the time being)... And want to try Darwin (I can compile the Tiger UI later and work to an OSX 10.6 (and Darwin 9+) feel later as well)....

BUT, I'm running into every wall concievable. I have the Darwin 8.0.1 ISO downloaded directly from apple's open source pages... and am trying to virtualize it in VB (egads!) Now, I'm running into the same error over and over... a dreaded "Still waiting for root device" while installing.

I've switched Primary and secondary masters/slaves, deleted the machine and re-created (including the virtual drive, and mounting/unmounting the ISO)... but to no avail, it either locks at the debug screen or tries to install then fails with this error after about 4 seconds....

But, maybe there is the issue since I'm running a 64-bit laptop (Karmic), and a 32-bit VirtualBox (with windows XP Vienna already on one VM as 32bit)....

I type "-s platform=x86pc" when the Darwin Bootloader shows up and after hitting a key to set boot parameters, then the terrible message... So long story short, anyone have any tips for this on this Darwin thing? Thanks in advance too!

---

### Post by JiuJitsu500 on 2010-01-23
Oh, I should add that I did everything on [this]("http://www.facepunch.com/showthread.php?t=726350") guide save the ACPI option (as I have virtualbox 3.1.2 and it is not there...).... but there is an option for IO AIPC or something like this... and still the same result with this enabled/disabled (but this shouldn't affect the install)...

The Windows XP works great without any issues except slow boot occasionally (go figure)... but I just cannot get this Darwin thing figured out....

---

### Post by Mike_IronFist on 2010-01-23
> **JiuJitsu500 said:**
> Hey all! I don't know where else to post this, but I'm also not sure where else anoyone would know about Darwin. I love Mac, but don't love how difficult it is to virtualize (not to mention the legal issues for the time being)... And want to try Darwin (I can compile the Tiger UI later and work to an OSX 10.6 (and Darwin 9+) feel later as well)....

BUT, I'm running into every wall concievable. I have the Darwin 8.0.1 ISO downloaded directly from apple's open source pages... and am trying to virtualize it in VB (egads!) Now, I'm running into the same error over and over... a dreaded "Still waiting for root device" while installing.

I've switched Primary and secondary masters/slaves, deleted the machine and re-created (including the virtual drive, and mounting/unmounting the ISO)... but to no avail, it either locks at the debug screen or tries to install then fails with this error after about 4 seconds....

But, maybe there is the issue since I'm running a 64-bit laptop (Karmic), and a 32-bit VirtualBox (with windows XP Vienna already on one VM as 32bit)....

I type "-s platform=x86pc" when the Darwin Bootloader shows up and after hitting a key to set boot parameters, then the terrible message... So long story short, anyone have any tips for this on this Darwin thing? Thanks in advance too!

Did you make sure that the OS type for your Darwin VM is set to Free BSD? Darwin is basically BSD with some Apple-specific changes, so that might help. From what I heard, Virtualbox does a little bit to help compatibility depending on what kind of OS you tell it you're installing.

Might I also add, Darwin was made to run very specifically on Mac hardware, which almost ALL Intel stuff with support for an NVIDIA and ATI graphics card or two, and very specific stuff at that, so running it in a VM can't be, as you might expect, particularly easy.

---

### Post by JiuJitsu500 on 2010-01-23
Yes, I tried it not knowing I had it on OpenBSD for a while, and when I found out about that I tried it 12 or 398 more times on FreeBSD, changing everything I could except the BSD options (it might be the only thing I have right so far... seeing how it's based off the FreeBSD kernel).... this is extreme for sure, and definately as you said, not easy at all.

I thought the point of an open source program was to be easy in getting the basics, no?

I'm still struggling with this. That damn line I'll bet will haunt my dreams until I can figure out the right combo to get it on an x86 platform (even though my laptop is x64, the virtual machine shouldn't know the difference...)....

Still waiting for root source... :)

---

### Post by k64 on 2010-01-23
Actually, Darwin is a hybrid kernel based on the Mach microkernel. This is an entirely different kernel type from traditional FreeBSD, which is monolithic.

Mach is a pretty old microkernel, then again, it was never originally in UNIX. That kernel was its own monolithic kernel.

In fact, Darwin is closer to Minix than to traditional BSD.

Not to mention, Darwin uses its own file system compared to BSD (HFS+).

If I were you, put it under "Other/Unknown" just to be on the safe side.

Oh, and while you're at it, install GNOME and [Mac4Lin]('http://mac4lin.sourceforge.net/') to create a near perfect replica of Mac OS X - all with open source software.

---

### Post by JiuJitsu500 on 2010-01-24
Wow, thanks for the info! I'm trying it again right now, with all unknown things.... didn't really know it was based off Mach, that's interesting (and makes more sense I think).

I'll use those links too, thanks again!

---

### Post by JiuJitsu500 on 2010-01-24
Okay, Darwin successfully installed.... the only thing left to do now is compile the GUI...

Google, here I come!

EDIT* Google is failing me.... I do not know any commands over here, but have got my Darwin logged in as root.... anyone have any tips on getting GNOME installed??? Or whatever comes first here.... I'm totally lost in Darwin :)

---

