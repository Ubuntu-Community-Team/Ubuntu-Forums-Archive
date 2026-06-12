---
title: "Linux for older PPC macs????"
date: 2008-04-27
forum: Apple Hardware Users
---

### Post by shgadwa on 2008-04-27
I have a lot of older imacs as well as G3s and 6500s....the specs are nto that great, usually around 300Mhz and the memory is not too good either. I want to isntall linux and sell them. I already did it to one that had 96MB ram. I installed xubuntu 6.06 and solt it for $30.00. It was a 333mhz imac. That was a little low on memory though.

I wanted to install xubutnu 8.04 on these so that it will be current, as well as having bug fixes and a recent version of firefox. However, that does not work as I get this blank screen that most have and I seem to not be able to get around it.

So, my question is, would Gentoo work good for these computers? WWhat other opperating system is good for slower macs??? Secondly, how does it compare to kubuntu which I really like? Third, I tried to isntall it but the whole thing is manual install and seems very complicated. No idea AT ALL as to how to isntal it. They do have handbooks but they are long, and they expect you to print the whole thing out and to know what they do not tell you.

Also, keep in mind that one or two of these computers, I will use, the others I want it to be one that people will buy for a good price.

Thanks,

Shawn

---

### Post by stream303 on 2008-04-28
With low-spec Macs you can still do a lot, but you may have to change your expectations / usage patterns a bit, unless you want to pop for more ram etc.

For those really small-memory machines, you might want to do just a server-install, and then add just a touch of xorg, xdm, a window manager, and a few lighter-weight apps along the lines that Xubuntu does.

A nice example of how to build it yourself can be found here, even though the intros talk about Intels - the info applies to ppc's as well for the most part:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

I think you are looking for an easier-to-install system, but this would be good for a great starter project at some point.

---

### Post by Jammin80503 on 2008-04-28
I would suggest you take a look at fluxbuntu. Its a tiny little OS, only 300 meg, and its actually pretty easy to use, once you get used to it. I put it on a  friend's really old laptop, and the thing runs like a dream. (but looks like a brick :P)
take a look, see what you think.
[http://fluxbuntu.org/js.html](http://fluxbuntu.org/js.html)

---

### Post by oswaldkelso on 2008-04-28
PPC builds are "pending" for fluxbuntu. You could use the ubuntu server edition and build a system. A standard Hardy install would bring in to much baggage on those old systems. 

I run a net install on an an imac333 256mb runs great. The machine I'm on now. 
debian-lenny
[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)

I've not installed it as yet but would be very suitable 
arch-ppc 2007.08.2 (Don't Panic) - NewWorld Boot ISO
[http://www.archlinuxppc.org/download/](http://www.archlinuxppc.org/download/)

The best supported ppc linux distro. once you get it installed and configured :)
gentoo ppc
[http://www.gentoo.org/main/en/where.xml](http://www.gentoo.org/main/en/where.xml)

I have installed an earlier version ran great on my imac333 ok for a techy person or some one that has everything they want already installed. A bit unfair to tell an inexperienced user to build from source 
slackintosh 12
[http://workaround.ch/download.html](http://workaround.ch/download.html)

---

### Post by shgadwa on 2008-04-28
I might use Gentoo for myself then...is it better than KDE?? How do I install it?

Also, for these computers, I want something that does not take much time for me to install so that I can sell it.

---

### Post by shgadwa on 2008-04-28
I really need tog et these computers working...as for xubuntu 8.04, if its the graphics card, It seems as if I cannot edit the xerver0xorg file or whatever..an errot pops up sayins some warning that its dangerous and you need to backup......

As for the older imacs, I need something that does not take much time to install, and is decently fast and will allow me to sell the computer for a good price to someone who would be happy and use it. That is what I need.

---

### Post by stream303 on 2008-04-28
> **shgadwa said:**
> I might use Gentoo for myself then...is it better than KDE?? How do I install it?

Well, Gentoo is an entire distribution that relies on compiling to get the most out of it, and KDE is a desktop environment.  You may want to look at the Gentoo PPC faq:

[http://www.gentoo.org/doc/en/handbook/handbook-ppc.xml](http://www.gentoo.org/doc/en/handbook/handbook-ppc.xml)

As for turning around older iMacs quickly, you may want to stick to an older more stable version.  Xubuntu Dapper or Debian Etch come to mind.

You may also want to look into Fluxbuntu, which appears to have a ppc port coming out.

Thing is, are you going to support your users when things go wrong?  If so, you may want to get a bit more experience on your own box first.  You are kind of experiencing what your buyers might face right now, since ppc distros aren't always 100% right out of the box....

---

### Post by shgadwa on 2008-04-28
hmmm......I think I like kde better than the xubuntu one and gentoo is very hard to install it seems. I might jsut isntall drapper on all these then...thats easy to do but the only problem with that is that if you try to upgrade, i found it often does something wrong and xserver-xorg is messed up. That was why I was thinking it shoud be current.

I might jsut get these computers running and use them for a little while first.

---

### Post by stream303 on 2008-04-28
> **shgadwa said:**
> I might jsut get these computers running and use them for a little while first.

I think that would be your best option, rather than focusing on a quick turnaround.

With all the machines at your disposal, you can do the ppc community a great service by finding and verifying bugs and solutions with us.  Along the way, your Linux skills in general will grow, and may turn out to be far more important than the machines in the first place. :)

---

### Post by dcb146 on 2008-05-13
I have Debian etch 4r3 installed on an Imac G3 450mhz with 512 ram   and I have the same on an Ibook  366mhz clamshell with 320 ram. I have used Ubuntu 7.04 on both machines as well but I have had no installation issues with Debian.

---

### Post by stream303 on 2008-05-13
Debian Etch is a fine distro.  In fact, I used it to upgrade to lenny-testing.  About the only thing I needed to do was to clean up the fonts a bit by running

```
dpkg-reconfigure fontconfig-config
```

and specifying in the last prompt NOT to use bitmapped fonts.  Ah, much better!

If you envision upgrading to testing or eventually stable when it comes out later this year, you may want to back up or write down your existing /etc/X11/xorg.conf file, as the transition from xorg 7.2 to xorg 7.3 is a biggie.  As Hardy users can attest now that we are running xorg 7.3, is that for some you might need to use info obtained from your existing xorg.conf to work properly.

With xorg 7.3, the old dpkg-reconfigure xserver-xorg no longer prompts you about your video card.

While I like Debian very much, this could also be used as a diagnostic tool for those who want to run other distros, but for some reason can't get them to work.  Try Debian Etch, and make note of the xorg.conf and possibly yaboot.conf file, and use that info on your new distro's installation.

Or just keep Debian - that's cool too.  I run both Ubuntu and Debian so it's a win-win at my place. :)

---

### Post by sudo55 on 2008-05-14
What is driving me batty is the lack of live cd's for any of the linux ppc distros...

The only ones I have found is system rescue 0.2.0, finnix (no gui), knoppix 3.2 (does not boot), linux from scratch 6.1 (no gui), and gentoo live cd 2006.1.

These live cd's are very limited and outdated.

In terms of ppc distros for older macs...

I have used (with my iBook G4 1.42 ghz) openSUSE 10.3, Fedora 7, Ubuntu 7.04, and Yellowdog 5.0.2...

They all work well except wifi is a real pain in the *** to get working if you can at all...

Well peace,

:)

---

