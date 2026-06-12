---
title: "ASYNOTE A8550 - No Sound"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by pompeyjohn on 2006-10-07
Right, this is tough for me to write.

It looks like I am going to have sadly say goodbye to the world of Linux. At least for now. I have done absolutely everything I can think of to get sound working on my piece of crap Packard Bell laptop. But all to no avail.

I have tried every distro I can get my hands on, and still nothing comes through the speakers.

I work in a software house and I am constantly banging on about GNU Linux to the microsoft centric people I work. I am passionate about free software.

I guess unless someone can give me some good news about a distro that works or a proven hack, then I'll have to cheer on from the side lines for the the forseeable future.

I'll miss you Linux and I'll be gritting my teeth whilst in M$ world...

---

### Post by xpod on 2006-10-07
I suppose you`ve checked in the "multimedia system selector" to try the different options in there and do the sound test thing.

This aint a laptop but like many i had sound issues and it was just a case of playing about with it all...
I think i even had to try the "oss" type from synaptic on one of these machines once just to get it working.

The sound seems to get mixed up a lot when different apps are using it and some even change settings in my experience..
I still have to go change settings every now and again.

If you aint got that MSS thing in your preferences tab you can enable it in the alcarte menu editor...it`s my first stop if sound goes now.

Good luck regardless

EDIT and you`ll have checked that "alsamixer" thing too i suppose??;)

---

### Post by pompeyjohn on 2006-10-07
Thanks for response.

I feel like I have tried all the hacks suggested on these forums and elsewhere.

It baffles me because some people report that they work and others get nothing. How can that be? My guess it is not working anywhere.

It looks like I am bang out of luck with a dodgy proprietary sound chip.

Anyone wanna buy a Packard Bell laptop? It is in fairly condition.... with only slight damage due to tears falling on the keyboard.

---

### Post by xpod on 2006-10-07
Naa...I got 2 packard bell desktops and their enough trouble thank you very much.
Mind you,it`s usually just ME who is the real source of trouble when something goes wrong with any of ours.
I spent my 4 months on windows having a strange sound issue that i could never quite suss out.And that was with the correct drivers and right settings so i know how you feel.

I would`nt give up so easily though...you can surely still keep ubunto for learning on and hopefully your sound issue will be resolved somewhere down the line...????

---

### Post by pompeyjohn on 2006-10-07
yeah I think that is what I'll do... hopefully one day I'll be able to show of Ubuntu instead of just talking about it.

---

### Post by pompeyjohn on 2006-10-07
whoa there! hang on, Have just found t[his page]("http://forums.debian.net/viewtopic.php?t=7964&sid=8a74e375719d83c2c42609fb7fe55b66")

which suggests yet another fix.... do I dare give it another go and set myself up for potential heartache?! hell yeah!

I just tried Mandriva on the laptop and still nothing so I'll whack the edgy beta over the top of that then give this a go.

Can anyone suggest how I "Pass irqpoll=noacpi to the kernel" 

where do I type this?

kernel          /vmlinuz-2.6.15-26-386 root=/dev/sda6 ro vga=791 irqpoll=noacpi noapic nolapic single 

ACPI is the integrated features on the mobo right? so no acpi, no hibernation etc is that right? I can live without them if I can have sound!!

someone please advise.... cheers :)

---

