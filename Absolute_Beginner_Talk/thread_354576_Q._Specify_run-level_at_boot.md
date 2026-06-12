---
title: "Q. Specify run-level at boot?"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Babybel on 2007-02-06
Hi,

First of all let me say I'm new here (and new to forums in general), so please forgive me if I post in the wrong place. I'm not a guru, just one of those slow human types with two legs.

Not sure if this is the right place, but as I'm new I thought it best to say hello here. Hello!

Tried a search but couldn't find anything.

I'm using run levels on a legacy laptop to aid performance. They go something like this:

2. Lean
3. With printing
4. Local webserver

I'd like to choose the run level at boot time rather than login and do the telinit thing.
Question: Can run level be specified as a boot time parameter (overriding the default in inittab)?

I've tried for example:

  kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=some-id ro quiet splash 4

but it always boots to run level 2. (who -r indicates run-level 2 and the webserver stuff isn't running). I can get to run level 4 using telinit without a problem, just not via grub.

Using Ubuntu Edgy 6.10 on a Toshiba laptop
(I would have stayed with Dapper, but Dapper couldn't reboot the Tosh which was a tad annoying)

Any ideas?

---

