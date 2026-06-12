---
title: "Dual-boot on two ppc HD's (Ubuntu/Ubuntu)"
date: 2012-01-15
forum: Apple Hardware Users
---

### Post by canhoto on 2012-01-15
Hi.

I'm thinking about deleting Mac OS from my G4 for good and installing Ubuntu on the hard drive where Mac OS is now (I explained in another thread).

So, I would like to ask:

- Will there be a booting problem if I have no Mac OS installed?
- Will yaboot be installed?
- How can I choose between the two hd's with Ubuntu on both? Can I just press the alt key like I do now? I should be able to setup a default startup drive afterwords, I think.

Thanks

---

### Post by pauljwells on 2012-01-17
I can't say for sure, but what I think will happen is that whatever you install last will become the default and the installation on the other HD will get renamed in yaboot as Ubuntu-Linux. At the 'boot' prompt press tab to see which kernels yaboot found. I have multiple Linuxes on my G5 but I always kept OSX, because I could and I like iTunes...
The accepted wisdom is that you should keep an Apple OS on a mac in case of firmware updates, but seeing how Apple don't support anything older than a couple of years there's not much danger of new firmware on any PPC iron.
As ever, make a backup, YMMV etc etc. Post back with results.

---

### Post by canhoto on 2012-01-18
> **pauljwells said:**
> 
As ever, make a backup, YMMV etc etc. Post back with results.

I already made a bakup of my Mac's home folder. But I have some more questions:

1. What's the best way of doing a backup of my current Ubuntu in case I have to recover it? Will DéjàDup make the job? That's in case anything goes wrong and I loose it (it would be bad, although my main documents are always synchronized with my Macbook).
- I would keep:[INDENT]- Some 50 GB of Mac OS in the "big" drive.
- Some 320 GB of Ubuntu on the rest of it.
- My current Ubuntu where it is now (my second 160 GB HD), which would become gradually my secondary installation (and which I could use for testing other releases or distro's, for instance.
[/INDENT]- So, my second question is: [INDENT]-What´s the best way of doing it? Should I try to install Ubuntu on the big HD along with Mac OS right now? Will it do it peacefully? Or should I delete Mac OS, install Ubnu and then Mac OS?
[/INDENT]Thanks

---

