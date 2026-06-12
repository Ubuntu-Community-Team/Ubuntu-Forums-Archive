---
title: "Why are people developing the Hurd?"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by keymoo on 2007-08-18
Hi,

I'm new to linux and I'm curious as to why the Hurd project still continues when we have an excellent, stable Linux kernel and an alternative to Linux, BSD. Why does the community need another Unix kernel?

Any URLs that explain this would be gratefully accepted.

Thanks,
keymoo

---

### Post by kellemes on 2007-08-18
[http://www.gnu.org/software/hurd/hurd.html]("http://www.gnu.org/software/hurd/hurd.html")
[http://en.wikipedia.org/wiki/GNU_Hurd]("http://en.wikipedia.org/wiki/GNU_Hurd")

---

### Post by Bachstelze on 2007-08-18
> **keymoo said:**
> we have an excellent, stable Linux kernel

This is not everyone's opinion...

---

### Post by keymoo on 2007-08-18
Thanks I've already seen those links but there's no real convincing explanation on those sites as to why Hurd is better than or offers advantages over Linux or BSD.

What I'm really looking for is a comparison between the two, or even better, what is motivating the developers to write the Hurd when their efforts could (perhaps) be more usefully employed hacking the Linux kernel (or BSD).

The principle of not reinventing the wheel does not seem to apply with Hurd and Linux - but obviously I'm missing something, and I'd like to know what that something is.

---

### Post by p_quarles on 2007-08-18
> **keymoo said:**
> Thanks I've already seen those links but there's no real convincing explanation on those sites as to why Hurd is better than or offers advantages over Linux or BSD.

What I'm really looking for is a comparison between the two, or even better, what is motivating the developers to write the Hurd when their efforts could (perhaps) be more usefully employed hacking the Linux kernel (or BSD).

The principle of not reinventing the wheel does not seem to apply with Hurd and Linux - but obviously I'm missing something, and I'd like to know what that something is.
There are a number of issues that Linus Torvalds and Richard Stallman do not see eye-to-eye on. The Free Software Foundation and the GNU project have their own ideas about the best way to license free software (see GPL v.3), and the only way they can do what they wish is to write their own code from scratch. Hence, the Hurd.

That's my understanding, at least, but I can't pretend to speak for others. You might ask the developers, since they would have a better idea of their motives than anyone here.

EDIT: On the technical side, I should add: Hurd is a microkernel, and Linux is more-or-less monolithic. There are some hypothetical advantages to microkernels that have run into huge problems in actual implementations. That is why, at least, the Hurd has taken so long to get barely-past-nowhere.

---

### Post by irish_flu on 2007-08-18
There's also value to be learned from writing an OS kernel, value that could perhaps be applied to Linux and BSD.  Nothing exists in a a vacuum, and innovation can sometimes lead to improvements outside of the project you're working on.

Also, as the poster above me notes there are different ways to implement a kernel.  Although I wouldn't call OSX or BSD a "microkernel", they are both descended form the Mach Microkernel; even though it's not used anymore (as far as I know, again I could be wrong) some innovations and novel ideas used in it have spread to other kernels.

---

