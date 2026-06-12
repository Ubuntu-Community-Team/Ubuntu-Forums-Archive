---
title: "Early kernel panic"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by jabbiati on 2006-11-01
I am trying to install (completely replace/reformat) Ubuntu onto a machine that is currently running SUSE.  I have tried several install CDs (6.06.1, 6.10, and both versions of the "alternative install" CDs) and all result with an immediate kernel panic (black screen white letters before any splash screens) when the CD tries to boot.  This comes right after I select "Install in test mode" or "Install from OEM mode" from the very first menu.  The exact message that I get is:

<0>Kernel panic - not syncing: Attempted to kill init!

I have installed Ubuntu before on this machine, so I don't think that it is a hardware conflict.

Why would I not be able to boot to a CD?  I was of the impression that the current operating system has no impact whatsoever on things that happen so early in the boot cycle like choosing a boot device such as the CD ROM.  

Maybe a BIOS problem?  Where the kernel is associated with the operating system, if the BIOS were involved with the panic it would have to be because of conflicts with the settings, right?  If Ubuntu has been installed before, then installing SUSE, and then trying to go back to Ubuntu and having a conflict, it seems that SUSE altered the BIOS.  Can this happen?

Sorry about the rambling.  I'm probably way off track with the thought process.  Any of your thoughts would be great.

Thanks.

---

### Post by marianom on 2006-11-01
Hi there. Had the same problem once so here's a few questions to see if it's the same:
Suse works ok every time you start the machine? or sometimes you have to start several times until it works?
Did you try running the live cd for a few minutes?
If so, does it eventually freeze and you have to reset the machine?

---

### Post by jabbiati on 2006-11-01
Thanks for responding.

> **marianom said:**
> Hi there. Had the same problem once so here's a few questions to see if it's the same:
Suse works ok every time you start the machine? **Usually**

 or sometimes you have to start several times until it works? **Never more than twice, but that is more than it should be.**

Did you try running the live cd for a few minutes? **I can't get the Live Cd to boot either**
If so, does it eventually freeze and you have to reset the machine?

I am very interrested in knowing what you are thinking.

Thanks again.

---

### Post by marianom on 2006-11-02
What happened to me was a hardware maintenance problem: the machine overheated every time I used the cd drive. If I wanted the machine to work, I had to let it cool a few minutes and then I would try again. Booting from the cd: sometimes worked, sometimes not but eventually the machine would freeze and after extracting the cd I could fry an egg on it. 
Finally it died in the middle of an installation so I was left without os in the machine.
I took it to a local store and they cleaned it (fans, cooler, the cd drive, the works), can't tell you exactly what they did but after it, I could run the livecd and finally installed Dapper in it. 

The error I always got with the cd with this problem was the same as you. So it might be a coincidence but if you run out of options, consider it.

Hope it helps. Buena suerte.

---

### Post by jabbiati on 2006-11-02
Thank you for the information.  I don't think that I am dealing with a CD drive issue as the drive seems to work in other situations just fine.  I'll check it out when I get home just to be sure.

I will also try posting more information about the panic message.  It seems that that is what other people are needing to help with similar problems.

I appreciate your help.

Joe

---

### Post by floridauser007 on 2006-11-02
> **jabbiati said:**
> Thank you for the information.  I don't think that I am dealing with a CD drive issue as the drive seems to work in other situations just fine.  I'll check it out when I get home just to be sure.

I will also try posting more information about the panic message.  It seems that that is what other people are needing to help with similar problems.

I appreciate your help.

Joe

Actually I had a problem installing too from the CD a while back.  My CDrom worked well elsewhere but always had problems.  I ended up trying a few times and cleaning the CD a little and it worked.  Use the self test of both the CD and the memory test.  I don't think the installer was written to be very fault tolerant so beware of this.

---

