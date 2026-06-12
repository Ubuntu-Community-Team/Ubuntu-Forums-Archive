---
title: "Using a Linux Disk Utility on an Intel Apple System"
date: 2008-10-27
forum: Apple Hardware Users
---

### Post by Misterbadexample on 2008-10-27
I'm getting Kernel Panics on my Os X 10.5 system. I need to run an error check and repair on the hard disk to see if that solves the problem.

But! I have misplaced my Install/Bootable Disk Utility Disc from apple.

Can I safely use a linux/OSS bootable disk utility and not harm my operating system?

By the way of that, what are some good ISOs I can download for this purpose?

I posted this on MacForums also, but this is quickly becoming my go-to place to help solve all my computing woes.

---

### Post by volanin on 2008-10-27
You could try the following steps:

1. Download the Hardy Desktop LiveCD:
**[http://releases.ubuntu.com/hardy](http://releases.ubuntu.com/hardy)**

2. Boot the LiveCD, connect to the internet and open a terminal.

3. Type to download and install the HFS+ filesystem utilities:
**sudo aptitude install hfsprogs**

4. Check the filesystem securely with:
**sudo fsck.hfsplus -f -l /dev/sdaX** *(put your Mac partition number here)*

5. See if it detects any errors.

You might also try to fix the errors, by removing the -l option.
But I suggest that you read the manpage before.
:)

---

### Post by cyberdork33 on 2008-10-27
There is a link to information on this in the FAQ.

---

### Post by Misterbadexample on 2008-10-27
@cyberdork33: Well, fair enough. But my question wasn't necessarily how to do it, but if it was safe. I'm guessing since you responded to the OP in the FAQ that you have done this and nothing ill came of it.

But what OSX operating system were you using? The apple support forums guys said over and over that using a non-proprietary error repair could potentially damage a Leopard installation, which is apparently very picky about the system it is installed into.

I got nearly twenty replies in a couple of hours, and nearly all were very much against doing this on Leopard.

It wouldn't matter to me if this was my personal Mac. It would be easy enough to back stuff up and see if I fsck things up. I could always format and reinstall.

But as a work Mac, I can't risk exacerbating the problem.

Thank you for pointing out the tutorial, and thank you, also volanin for yours as well. But I'm still doubting the safety of doing this on a Leopard HFS filesystem.

---

### Post by cyberdork33 on 2008-10-27
> **Misterbadexample said:**
> @cyberdork33: Well, fair enough. But my question wasn't necessarily how to do it, but if it was safe. I'm guessing since you responded to the OP in the FAQ that you have done this and nothing ill came of it.Yes, Sorry. Well, I personally would not use it on a system that I want to make sure to preserve (just in case). It does and has worked for people though if it is the only route you have.

> **Misterbadexample said:**
> The apple support forums guys said over and over that using a non-proprietary error repair could potentially damage a Leopard installation, which is apparently very picky about the system it is installed into.Well, the "apple guys" tend to take things to the extreme, but do have a point. Apple is really the only one that fully understands their proprietary filesystem. On the other hand, they have also told several people that installing rEFIt will break the Firmware on their Mac... which is absolutely ridiculous if you understand what rEFIt is.

> **Misterbadexample said:**
> I got nearly twenty replies in a couple of hours, and nearly all were very much against doing this on Leopard.

It wouldn't matter to me if this was my personal Mac. It would be easy enough to back stuff up and see if I fsck things up. I could always format and reinstall.

But as a work Mac, I can't risk exacerbating the problem.

Thank you for pointing out the tutorial, and thank you, also volanin for yours as well. But I'm still doubting the safety of doing this on a Leopard HFS filesystem.
If you have the option to use a Install DVD, that is what I would do. Have you tried booting in single-user mode?

---

### Post by Misterbadexample on 2008-10-27
> Well, the "apple guys" tend to take things to the extreme, but do have a point. Apple is really the only one that fully understands their proprietary filesystem.

They are a weird breed, the "apple guys". They all seem to be all about paying for stuff and scared of messing up a system here and there. I don't get it. The OSS culture makes so much more sense to me. On the other hand, the guys I talked to did seem very knowledgable, very intelligent, if not paranoid.

> On the other hand, they have also told several people that installing rEFIt will break the Firmware on their Mac... which is absolutely ridiculous if you understand what rEFIt is.

What does a boot loader have to do with firmware? It's like GRUB or Yaboot, right? Is the official Intel Mac bootloader part of the firmware?

> If you have the option to use a Install DVD, that is what I would do. Have you tried booting in single-user mode? 

That's what it comes down to, recovering that Install DVD. I'm going to have to bite the bullet and get one.

Is single user mode like root or super user? I haven't tried that yet, I don't really know what I would be doing in that mode. Didn't even really know what it meant until I just now googled it. What would you recommend trying?

---

### Post by cyberdork33 on 2008-10-27
> **Misterbadexample said:**
> What does a boot loader have to do with firmware? It's like GRUB or Yaboot, right? Is the official Intel Mac bootloader part of the firmware? rEFIt is just an executable (ran directly in EFI) that presents a GUI for the existing Mac Bootloader (and some other nifty tools).

> **Misterbadexample said:**
> Is single user mode like root or super user? I haven't tried that yet, I don't really know what I would be doing in that mode. Didn't even really know what it meant until I just now googled it. What would you recommend trying?
Single-User mode is like a recovery mode. Try booting with CMD+S first to see if it will work. From there you can run fsck from the root console.

---

### Post by Lars Noodén on 2008-10-28
> **volanin said:**
> You could try the following steps:
...

2. Boot the LiveCD, connect to the internet and open a terminal.

3. Type to download and install the HFS+ filesystem utilities:
**sudo aptitude install hfsprogs**

4. Check the filesystem securely with:
**sudo fsck.hfsplus -f -l /dev/sdaX** *(put your Mac partition number here)*
...


Hey, thanks.  That's cool to know a live cd can do that.

---

