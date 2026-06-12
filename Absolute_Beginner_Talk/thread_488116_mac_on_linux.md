---
title: "mac on linux?"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by pinkdog on 2007-06-29
okay, maybe i'm a complete and total noob when it comes to linux, but is there a way to put ubuntu on a mac without Parallels or the ubuntu live cd?

i just want to install ubuntu like a dual-boot OS but can you do that with a mac?

---

### Post by tregetour on 2007-06-29
I've never done it before myself but I understand that it is very possible. The one thing you'll need to know is whether your mac has the newer intel chip or the older powerpc chip. Depending on the answer just get the appropriate cd. Boot into the live cd and you'll see an option on the desktop to install. As far as I know it should automagically detect the mac os and allow you to set up a dual boot [I've only done it on windows so you may want to double check -- elsewise I am sure there still a way to do it just not as simply]. Hope that answers the question.

---

### Post by starcraft.man on 2007-06-29
> **pinkdog said:**
> okay, maybe i'm a complete and total noob when it comes to linux, but is there a way to put ubuntu on a mac without Parallels or the ubuntu live cd?

i just want to install ubuntu like a dual-boot OS but can you do that with a mac?

Install an OS without putting it in a VM or install it from a CD.... hoping it magically appears on your drive???

Easiest way IMO is Parallels if you have that and are comfortable with VMs. A VM like that of course has its limitations. If you meant something like the WUBI installer on Windows, I don't think theres a Mac version. If you just didn't want the live environment look at the alternate CD for the text installer.

Any way you do it though you need a CD or at least the ISO for mounting to parallels (parallels and all other VMs will mount ISOs to the emulated cd drive).

[Link to media]("http://releases.ubuntu.com/7.04/")

Desktop is the Live CD, Alternate is the text based installer. AMD64 is the 64 bit version and x86 the 32 bit, pick your flavor. When in doubt, 32 bit Live usually works in most things, alternate works on all the rest.

---

