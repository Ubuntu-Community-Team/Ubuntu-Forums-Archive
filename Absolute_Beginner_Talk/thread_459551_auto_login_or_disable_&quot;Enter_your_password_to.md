---
title: "auto login or disable &quot;Enter your password to perform administrative tasks&quot;?"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by brandonjp on 2007-05-30
I'm not actually a complete linux newbie - but I'm constantly adding and removing users and packages to test some stuff in Ubuntu and I'm a little unclear....

is there a way to be automatically logged in so I don't constantly have to enter my password?
or
is there a way to disable the "Enter your password to perform administrative tasks" dialog box?

thanks
--bp

---

### Post by starcraft.man on 2007-05-30
> **brandonjp said:**
> I'm not actually a complete linux newbie - but I'm constantly adding and removing users and packages to test some stuff in Ubuntu and I'm a little unclear....

is there a way to be automatically logged in so I don't constantly have to enter my password?
or
is there a way to disable the "Enter your password to perform administrative tasks" dialog box?

thanks
--bp

Ubuntu is based on the [Sudo system]("https://help.ubuntu.com/community/RootSudo"). The reason its used is listed on the page and explained in detail. The bottom line is it is for security. Just like UAC (Vista's poor imitation), you could bypass it by logging in as root constantly, but then you give all programs and everything you run administrative access to everything on your computer. IMO thats not a good idea (especially if an exploit or other attack happens, its possible. Linux ain't bulletproof, no software is.). I'd stick it out and enter your password, it costs you 2-3 seconds a shot? Its not much for peace of mind I think. After a while, you don't even notice, its second nature. Oh and I install and remove apps alot, I input sudo probably close to 50+ times a day on heavy usage, maybe more.

---

