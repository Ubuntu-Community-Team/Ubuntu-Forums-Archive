---
title: "Is there much point in using the 64-bit version, for a realative newbie?"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by Subterranean on 2007-02-01
I have an Intel C2D E6600 which supports 64-bit processing through the EM64T instruction set. Would I benefit from installing the 64 bit version of Ubuntu rather than the 32-bit version? I'm guessing there would be more difficulties, driver problems etc since 64-bit software is relatively under-developed currently, but if I could get this sorted, would I see any sort of performance increase or other advantages over the 32-bit version? 

If not, what is the major reason for having a 64-bit version? I guess for future proofing; by developing it early on, by the time 64-bit processing becomes mainstream, Linux will be right up there fully developed for it.

Thanks for any advice.

---

### Post by pizzutz on 2007-02-01
Pretty much right on.  I have an AMD64 and I use the 32 bit version.  After a bit of research, I decided that the 64 bit version would be more trouble than it was worth for now.

If my programming skills wern't so outdated, I would probably run it just to help out with the development of the drivers and software, but alas it is beyond my current capibilities.

---

### Post by teaker1s on 2007-02-01
apart from flash, which plays up 64bit been okay for me

---

### Post by NESFreak on 2007-02-01
> **Subterranean said:**
> I have an Intel C2D E6600 which supports 64-bit processing through the EM64T instruction set. Would I benefit from installing the 64 bit version of Ubuntu rather than the 32-bit version? I'm guessing there would be more difficulties, driver problems etc since 64-bit software is relatively under-developed currently, but if I could get this sorted, would I see any sort of performance increase or other advantages over the 32-bit version? 

If not, what is the major reason for having a 64-bit version? I guess for future proofing; by developing it early on, by the time 64-bit processing becomes mainstream, Linux will be right up there fully developed for it.

Thanks for any advice.

i don't really know the pros, but the one big con is that you can't really run 32bit applications. These 32bit only applications include WINE, WMV support, adobe FLASH, and several games like unreal tournament, neverwinter nights and doom3. Though there are attempts to create a compatibility mode for 32bit under 64bit, i don't know how good they work.

NESFreak.

---

### Post by deadgobby on 2007-02-01
The Linux 64bit kernal can be stable. Just not a whole lot of apps to support it. Like Suse has  good support for 64bit. I say that the Linux commune needs to get cracking on 64 and programs. Cause the up and coming CPU demands are going to go away from 32bit. Soon you can only use 64. 
Gobby

---

### Post by PgR on 2007-02-01
So are we saying it's possible to run the 32-bit version of edgy on a 64-bit processor? If so will it run all the usual 32-bit software?

If so, that's a marvelous solution - so many apps don't run (properly) on amd64 that I'm beginning to regret ever buying the thing.

---

### Post by Spr0k3t on 2007-02-01
I use the 64bit Edgy and 32bit Edgy on a different drive.  Since AMD64 processors can run 32bit just fine, there's no downfall in the change.  You get a few more supported applications and plugins.  However, with 64bit taking over mainstream systems it will not be long before 32bit is on the other side of the fence.

---

### Post by Brunellus on 2007-02-01
The single biggest benefit of moving to a 64 bit kernel is the fact that your memory address space becomes HUGE.  If your workstation has more than 4 GB of RAM, then a 64 bit kernel starts to make sense.  But if you have 4GB or less, there's not much point.

---

### Post by ucsdrake on 2007-02-01
so even though i have a AMD turion 64 the fact that i only have 512mb of RAM means i could go with a 32bit and not feel the difference? but run more applications such as WINE?

---

### Post by Brunellus on 2007-02-01
> **ucsdrake said:**
> so even though i have a AMD turion 64 the fact that i only have 512mb of RAM means i could go with a 32bit and not feel the difference? but run more applications such as WINE?
pretty much, yeah.  

Remember that we were running 16-bit OSes for a good long while after 32-bit processors came out. . .

---

### Post by pseudonym on 2007-02-01
> **NESFreak said:**
> i don't really know the pros, but the one big con is that you can't really run 32bit applications. These 32bit only applications include WINE, WMV support, adobe FLASH, and several games like unreal tournament, neverwinter nights and doom3. Though there are attempts to create a compatibility mode for 32bit under 64bit, i don't know how good they work.

Not true. 64-bit is backwards compatible with 32-bit - it's part of the spec. The issue mainly revolves around ensuring 32-bit programs have access to the 32-bit libraries. Ubuntu64 comes with many of these by default, and you can add others later which improve compatibility for things like graphics and sound.

It's possible to run all those applications you mentioned, though most of them require a little tweaking. And when they're running they're doing so just as well as if they were running on a 32-bit system. :) Many tips on setting things up are available in the [Ubuntu 64-bit forum]("http://www.ubuntuforums.org/forumdisplay.php?f=134").

I do notice a significant performance increase in processor-intensive 64-bit apps like re/encoding video. This is probably the main advantage for desktop use. The extra memory capability is only useful at this point for things like large database servers.

But 64-bit is the way of the future and I figure it's good to get used to it now since 64-bit desktop distros have developed well enough IMHO for general use. But, as with everything, YMMV.

One thing that scares me a little is that MS Vista still seems to be pushing 32-bit. Just look at all the ads for upgrades and new systems - they all seem to be for 32-bit Vista! Not surprising really, considering the installed base for Windows is almost totally 32-bit, and it's impossible to upgrade from that to the 64-bit version without doing a clean install with a full-version 64-bit copy.

But we've always been able to count on MS to hold back computer development, haven't we? ;)

---

### Post by nitebum on 2007-02-02
I'm new to Ubuntu (been using for about a week). I have tried the 64 bit versions of Ubuntu and Kubuntu so far, and I can't see any real advantage to 64 right now. 

I'm currently burning the 32bit b/c I want Flash and Wine. And I don't feel like fighting my computer to make them work in 64. Once Wine and FLash work in 64, I'll probably swiitch back.

---

### Post by ShadowRage on 2007-02-03
I use 64 bit and couldnt be happier.

wine works with some tweaking (I'm going to look into compiling it to run natively on 64 bit whilst maintaining a 32 bit environment within wine) and flash works with nspluginwrapper.
I might as well start using 64 bit and ride out the storm. there is a difference when it comes to compression.

---

