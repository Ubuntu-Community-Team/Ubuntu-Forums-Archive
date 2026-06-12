---
title: "Trouble booting: &quot;IO-APIC not connected&quot;"
date: 2008-05-19
forum: Apple Hardware Users
---

### Post by Aurora on 2008-05-19
[Edit] I found the bug report for this one; there doesn't appear to be a solution. It's bug #54621: "Hardy final 8.04 generic works fine. -rt version panics." was the last relevant comment.  The realtime kernel is essential for the work I want to do, so I guess I have to wait until it's fixed and reinstall.  My original post follows.

Greetings,

I installed Ubuntu Studio in a CD MacBook.  The install seemed to go well, but booting is hit or miss.  Sometimes I can boot in recovery mode; sometimes not.  A couple times I got a normal boot.  Sometimes  in recovery mode it just goes to a blank screen; other times I get a message like this:

"MP BIOS bug: 8254 timer not connected to IO-APIC.

Trying to set up timer (IRQ0)through the 8295A(something)...failed.

Trying to set up timer as Virtual Wire IRQ...failed.

Trying to set up timer as Ext-INT IRQ...failed.

Kernel panic - not syncing - IO-APIC doesn't work! Boot with APIC=debug and send a report. Then try booting with 'noapic' option."

Sometimes with a regular boot, I will see something about IO-APIC flash briefly on the screen, then it will either boot to the desktop, or I will see colored patterns as the screen flashes on and off before finally going blank.

I can't figure out how to access boot options like noapic.  I can't even find a reference to "IO-APIC" on the forums.  Does anybody know what this means, or what to do about it?

--Paul

---

### Post by louisiana84 on 2008-05-19
I've got a pretty similar thing happening on my Toshiba A215-S5829. It takes a minute to boot but operates fine afterwards. The "Ubuntu" with the orange bar going back and forth does not appear but the log-in screen eventually does. Any help would be appreciated.

---

### Post by cyberdork33 on 2008-05-19
> **louisiana84 said:**
> I've got a pretty similar thing happening on my Toshiba A215-S5829. It takes a minute to boot but operates fine afterwards. The "Ubuntu" with the orange bar going back and forth does not appear but the log-in screen eventually does. Any help would be appreciated.
This is the Apple Users Forum and the rt kernel just doesn't work on Mac hardware... At least it hasn't ever worked before. There is a problem in the kernel itself that has not been fixed. I don't know if this is the same issue you have.

---

### Post by Aurora on 2008-05-20
> **cyberdork33 said:**
> This is the Apple Users Forum and the rt kernel just doesn't work on Mac hardware...


Wish I'd known that.

I have generic Ubuntu installed now; seems to work. I still have to do the sound tweaks and all that.  Maybe I'll try installing JACK and some audio apps and see what happens.  Without the realtime kernel, though, I don't expect good results.

Looks like I may have to break down and replace my hardware if I want to do serious audio work with Linux.

---

### Post by cyberdork33 on 2008-05-20
> **Aurora said:**
> Looks like I may have to break down and replace my hardware if I want to do serious audio work with Linux.
I don't have a clue why it doesn't work, nor do I know if there is even a bug filed about it (which means it won't get fixed). There are actually not many people using the -rt kernel so this issue doesn't come up often.

This looks like it might be the report...
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/54621](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/54621)

It seems the -rt kernel is unsupported by ubuntu.

---

### Post by Aurora on 2008-05-22
> **cyberdork33 said:**
> I don't have a clue why it doesn't work, nor do I know if there is even a bug filed about it (which means it won't get fixed). There are actually not many people using the -rt kernel so this issue doesn't come up often...It seems the -rt kernel is unsupported by ubuntu.

The Ubuntu Studio project uses the -rt kernel as standard. See [http://ubuntustudio.org/](http://ubuntustudio.org/)

I do believe the -rt kernel is supported:

 > Brian Murray  wrote on 2007-12-14:

I am assigning this bug to the 'ubuntu-kernel-team' per their bug policy.

>  Saïvann Carignan  wrote on 2008-01-20:

Marked Bug #91279 as a duplicate, set Importance to High and Status to Triaged since we have a lot of relevant informations and debug files from this bug and bug #91279

This from the URL you quoted.  I don't see any new action on it, though.

--Paul

---

### Post by cyberdork33 on 2008-05-22
> **Aurora said:**
> I do believe the -rt kernel is supported
I will explain... What I mean is that the rt kernel is developed by the UbuntuStudio people and is in the universe repo (not the 'main' software channel), so any bugs filed against it just end up in the real developers' hands anyway. 

The bug above is filed against the main ubuntu kernel not the rt kernel, but the ubuntu kernel is the basis for the -rt variant

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/54621/comments/37](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/54621/comments/37)

> -rt kernels are unsupported. Please contact the developer: Alessio Igor Bogani. That said, if Ryan sends a fixed patch that is applied to Gutsy, then -rt will get it automatically.

Apparently, this is the main dev for the -rt kernel:
[https://edge.launchpad.net/~abogani](https://edge.launchpad.net/~abogani)

---

### Post by Aurora on 2008-06-05
> **cyberdork33 said:**
> 

Apparently, this is the main dev for the -rt kernel:
[https://edge.launchpad.net/~abogani](https://edge.launchpad.net/~abogani)

So, would you recommend I contact him myself, or leave it to the Kernel People?

Meanwhile, I installed generic Hardy, then installed Ubuntu Studio packages into that.  It works, sort of, lots of xruns. But I can use hardware I never got working on my desktop, which I built specifically to do Linux audio work.  The Hardy kernel includes a fix for the specific device I use, so I'll be getting that on my desktop soon.

Thanks, CyberDork, you are a fountain of knowledge.

--PD

---

