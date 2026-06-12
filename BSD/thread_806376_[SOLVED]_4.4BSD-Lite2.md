---
title: "[SOLVED] 4.4BSD-Lite2"
date: 2008-05-24
forum: BSD
---

### Post by J05HYYY on 2008-05-24
Hello all, I've just downloaded what I think is the source code for 4.4BSD-Lite2. Does anyone know how I'd go about compiling it as a bootable image?

Josh

---

### Post by J05HYYY on 2008-06-19
Okay, I've read further into this and realized it was a silly question. Please correct me if I'm wrong:

Some of the code in 4.4BSD-Encumbered (proprietary) is missing from 4.4BSD-Lite (free). So the free bits from 4.4BSD Lite have been used in freeBSD, netBSD, dragonflyBSD and openBSD (using the BSD license). These operating systems are directly or indirectly based on the object in question - 4.4BSD Lite.

Because 4.4BSD-Lite/Lite2 is incomplete, it takes whole teams of people to compile the source. Different approaches were taken and different bits had to be added.

Personally, to me, NetBSD looks good because of it's high portability. The version 2.0 has support for the amd64 architecture. It uses the alchemist shell which is a remake of the bourne shell, it's "fast, small and POSIX compatible".

I might try reading some guides about making a live cd but yeah, ubuntu still rocks. :guitar:

---

### Post by stream303 on 2008-06-19
You may want to jump directly to more recent versions of either FreeBSD, NetBSD, or OpenBsd.  Ver 2.0 of NetBSD is rather old, with v 5.0 coming out. :)  Go directly to the *BSD.org urls.

You may also be interested in FreeBSD-based desktop-focus derivatives such as PC-BSD, or Desktop-Bsd.

---

### Post by cardinals_fan on 2008-06-19
NetBSD is AWESOME!  Grab a 4.0 iso and have fun.

---

### Post by J05HYYY on 2008-06-19
I want the simplest form of UNIX, so I can write elegant, portable bourne shell script.
NetBSD's was the branch of BSD which focused on "clean" ports.
Version 2.0 was the first version of BSD to run on a 64 bit architecture.

I'd prefer not to download a later version, because I only want to use it as a base for development.


To see if my computer could theoretically still run NetBSD 2.0, I opened virtualbox and made a new virtual machine for the i386 iso.
I selected a language and went to the utility menu, it had an option called "a: Run /bin/sh" which tested successfully.
After this success, I was quite impressed, so tried to install it.
Unfortunately I got an error:
```
I can not find any hard disk for use by NetBSD
```
I don't think the kernel understands my hard drive but I'm not too sure.

---

### Post by J05HYYY on 2008-06-19
> **cardinals_fan said:**
> NetBSD is AWESOME!  Grab a 4.0 iso and have fun.

Actually, I think I will.

---

### Post by J05HYYY on 2008-06-19
> **J05HYYY said:**
> Actually, I think I will.

EDIT:
Nope ... it didn't work, same error as above. Now I am confused. Whoever came up with the catchphrase "Of course it runs NetBSD" should get a slap. My computer clearly doesn't, and it's only a year new. I can't believe I can't install this OS due to some little flaw like [this]("http://www.netbsd.org/ports/macppc/oldfaq.html#old-nodisk").
As far as I can see, there is [no solution to my problems]("http://www.linuxquestions.org/questions/bsd-17/i-can-not-find-any-hard-disk-for-use-by-netbsd-538893/"). :(

I might take this to the NetBSD forums, as it would be more appropriate. Not sure if the ubuntu forums is the best place to be asking about NetBSD.

---

### Post by J05HYYY on 2008-07-12
okay ... thought i would tie up this thread for the time being.

The problems I developed arose because I was trying to run NetBSD in VirtualBox. After resetting the console several times and rebooting the NetBSD iso; I managed to get to the NetBSD installer. Unfortunately, during the installation I hit a brick wall. With the [bad address]("http://forums.virtualbox.org/viewtopic.php?t=4548&sid=8344e667d6fef04eca44cccc4fd60c39") problem.

After searching for solutions (and testing them all out), I was no further in the installation of NetBSD in virtualbox.

I'm not sure about trying to use other visualization software. VirtualBox is the most popular and realistically looks the best at the moment anyway.

So on reflection, I might just install it on a new partition instead.

Sorry for constant posting on this thread. Thank you to everyone who replied. I would mark this as solved but I don't know how.

---

### Post by K.Mandla on 2008-07-14
Moved to BSD Discussions and marked as solved. :)

---

### Post by cardinals_fan on 2008-07-14
> **J05HYYY said:**
> okay ... thought i would tie up this thread for the time being.

The problems I developed arose because I was trying to run NetBSD in VirtualBox. After resetting the console several times and rebooting the NetBSD iso; I managed to get to the NetBSD installer. Unfortunately, during the installation I hit a brick wall. With the [bad address]("http://forums.virtualbox.org/viewtopic.php?t=4548&sid=8344e667d6fef04eca44cccc4fd60c39") problem.

After searching for solutions (and testing them all out), I was no further in the installation of NetBSD in virtualbox.

I'm not sure about trying to use other visualization software. VirtualBox is the most popular and realistically looks the best at the moment anyway.

So on reflection, I might just install it on a new partition instead.

Sorry for constant posting on this thread. Thank you to everyone who replied. I would mark this as solved but I don't know how.
VirtualBox tends to have problems with *BSDs.  VMware is usually better.

There are VMware virtual appliances premade for [NetBSD]("http://www.vmware.com/appliances/directory/1074"), [OpenBSD]("http://www.vmware.com/appliances/directory/1283"), [FreeBSD]("http://www.vmware.com/appliances/directory/1182"), and [PC-BSD]("http://www.vmware.com/appliances/directory/1051").

---

### Post by J05HYYY on 2008-10-26
just a quick follow up ... i managed to get NetBSD working slow(ish) in ubuntu using QtEmu (from Applications>Add/Remove).
Thought it would make a good alternative to vmware for now.

---

### Post by kk0sse54 on 2008-10-28
Best way to test NetBSD 
1) Install it on a free primary partition of course :)
2) More realistically try Vmware server 2 which I used to try out NetBSD with fantastic results

---

