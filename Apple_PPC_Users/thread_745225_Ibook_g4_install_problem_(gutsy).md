---
title: "Ibook g4 install problem (gutsy)"
date: 2008-04-04
forum: Apple PPC Users
---

### Post by Mingusings on 2008-04-04
Hey all. I am new to linux, and eager to jummp in and get started, so I am trying to install Ubuntu 7.1 on my ibook g4 right now. I downloaded the install disc for ppc computers, and am trying to boot from the cd, but every time I do I don't get the GUI screen shown in the guides, but a dos type screen that tells me to hit enter. I do so and it says it loads the kernel, but then goes to a white screen, and then a black screen which says "Cannot allocate resources region 0 of device" and then some long number. Any advice please?

---

### Post by stream303 on 2008-04-04
> **Mingusings said:**
> Hey all. I am new to linux, and eager to jummp in and get started, so I am trying to install Ubuntu 7.1 on my ibook g4 right now.

Welcome aboard!  For future reference, are you using the live-cd desktop, or the "alternate" ppc non-live installer?  Most recommend using the "alternate" non-live installer, but with more recent machines this may not be an issue.

To make things easier, you may want to make sure of your G4 iBook specs:
[http://www.everymac.com/systems/apple/ibook/index-ibook.html](http://www.everymac.com/systems/apple/ibook/index-ibook.html)

> I do so and it says it loads the kernel, but then goes to a white screen, and then a black screen which says "Cannot allocate resources region 0 of device" and then some long number.

Dont' worry about it not being able to allocate resources.  This time when you boot and after you have pressed "L" for linux, at the next prompt hit -tab- to stop the boot countdown and it will show you some booting options.  At that prompt, do you get further along if you enter

```
Linux video=ofonly nosplash
```

You may want to keep these two excellent faqs handy:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)
and
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

On my G4 iBook, after install the system was sluggish due to Network Manager tying up all the resources as shown by using the TOP command in a terminal.  If that is the case, we can disable it, but for now, let's see how it goes....

---

