---
title: "Kernel config not what I expected --not sure how to approach some things"
date: 2011-10-25
forum: Any Other OS
---

### Post by ClientAlive on 2011-10-25
Ok, so I started talking about building my own system from the ground up quite some time ago. I made several posts here at Ubuntu forums about things like kernel configuration and compiling, and other things. I piddled around for months, reading various things about it and generally just taking my time getting to it. I ultimately decided on Gentoo.

So now, here I am with a second machine built and ready for the system; and I started that Gentoo build almost two weeks ago now. I got past raid and lvm and installing my stage 3 and emerge and dug into configuring my kernel. It wasn't until after several unsuccessful attempts that it occured to me that something was off in the config file to begin with.

I began to suspect that there are a whole slew of thing pre-selected right out of the box that have to do with all kinds of different machines (possibly even conflicting selections). So I ran a

```

make mrproper

```

and a

```

emerge --unmerge hardened-sources

```

which removes the kernel source (the source that I chose anyhow).

And I basically got back to the point where the system was before I downloaded the kernel source. I wanted to take the opportunity to examine this config file, fresh, out of the box, before I even touch anything.

So, after acquiring the kernel source again, what I saw was that, yes, indeed there is stuff pre-enabled that has to do with all kinds of various machines (not mine).

So I'm sitting there, staring at the screen, at this menuconfig screen open in front of me. And I'm trying to make sense of the kind of logic that would have to be applied to deal with a mess like that.

I think the logic would go something like this:

If, the config file were relatively empty to begin with and what you needed to do to configure your kernel was just 'add' what you need that's specific to your machine --then you could do that easily enough. In a case like that, all you would have to do is identify what is needed for your machine and enable it. Easy peasy, all done.

If, the config file is filled with a a bunch of selections that have to do with all kinds of other, varying, machines to begin with, then you need to know --not just about your own machine, but about every other machine as well. Then you need to not only enable the things specific to your machine (if they aren't already), but you also need to clean up that mess that was left for you when you first opened the file.

With the first scenario, pretty much anyone could do it with limited or no experience. With the latter scenario, it become much much more of a challenge.

I don't know what I expect to come of my having written this post. I do know that it isn't just a complaint (although it has that element as well). I suppose I thought I would just put down some of my observations and see what kind of response I would get. I know that I still want to do this and that I'm willing to deal with the mess if that's what has to happen. What I don't know is what I'm really looking at when I look at all that junk in the config file and what the best strategy is to take.

Thanks for taking the time to read this. If you have any feedback that you feel would be helpful I would sure appreciate hearing it.

Thank you
Jake

---

### Post by kk0sse54 on 2011-10-25
Easiest way to configure a clean kernel: grab one of pappy's [_kernel seeds_]("www.kernel-seeds.org") and just enable your approriate device drivers and any other specific misc options needed.

Otherwise I'm not really sure what kind of "cruft" you're talking about since running 'make mrproper' deletes any .config in your kernel sources and you'll essentially be left with a default configuration file for your architecture which will include support for several basic options that you can simply unselect if need be.

---

### Post by ClientAlive on 2011-10-26
Well, aparently when you open the config file it has a lot of things enabled right out of the box (I mean like half the stuff, before you even touch it). I don't recognize about 80% of what's already enabled but I do recognize a few things and see that they are the same feature but for different cpu. or are things that have nothing to do w/ a desktop system for instance. Things like stuff for pcmcia cards being enabled already, and wireless and power management options that only apply to laptops (like "battery"), etc, etc, etc . . .  And the list goes on. I don't quite get why anyone would hand you something like that but it is sourced from the same distro I'm trying to build - so I'm sure anything different would even work.

---

### Post by kk0sse54 on 2011-10-27
> **ClientAlive said:**
> Well, aparently when you open the config file it has a lot of things enabled right out of the box (I mean like half the stuff, before you even touch it). I don't recognize about 80% of what's already enabled but I do recognize a few things and see that they are the same feature but for different cpu. or are things that have nothing to do w/ a desktop system for instance. Things like stuff for pcmcia cards being enabled already, and wireless and power management options that only apply to laptops (like "battery"), etc, etc, etc . . .  And the list goes on. I don't quite get why anyone would hand you something like that but it is sourced from the same distro I'm trying to build - so I'm sure anything different would even work.

Like I said it's part of the default configuration file that's found for every architecture in the kernel. Either you manually unselect the things you don't need (i.e. Wireless) or start with a minimal kernel seed from the site I linked earlier.

---

### Post by ClientAlive on 2011-10-29
Sorry I went mia for a while there. I think I got it. It boots but still have to fig out what I had set the login info to before I can log in and see what's up.

I just remember thinking that doing things that way made it unnecessarily difficult, especially for the less experienced. Nothing I can do about it though unless I went in and edited the default make file I guess. Make my own default version. Idk.

Thx tho.

---

