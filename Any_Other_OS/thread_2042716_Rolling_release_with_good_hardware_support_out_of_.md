---
title: "Rolling release with good hardware support out of the box"
date: 2012-08-15
forum: Any Other OS
---

### Post by Random_Dude on 2012-08-15
Hi everyone,

I was thinking of changing to a rolling release Linux distro. I'm getting a bit tired of having to do a fresh install every year or so.

I've tried LMDE, but unfortunately the hardware does not work out of the box and I don't know how to install drivers.
Is there any rolling release distro (64-bit) that has an hardware support as good as Ubuntu?

I googled around and I found some people suggesting Sabayon, PCLinuxOS (I don't know if there is a 64-bit version yet) or Chakra. Has anyone tried these?

Cheers

---

### Post by Plumtreed on 2012-08-15
You could do an upgrade you don't have to reinstall......but you might want to have a look at Fuduntu which calls itself a rolling release!

---

### Post by ratcheer on 2012-08-15
I am using Sabayon 9 and I really like it. It is a very solid distro. I am wondering whether I prefer it to Arch Linux.

Tim

---

### Post by Random_Dude on 2012-08-15
> **Plumtreed said:**
> You could do an upgrade you don't have to reinstall......but you might want to have a look at Fuduntu which calls itself a rolling release!

I've heard a lot of horror stories with upgrades. I also tried it once and it didn't go so well. That's why I always do a fresh install.
Fuduntu sounds interesting... Do you know how it behaves with hardware?

> **ratcheer said:**
> I am using Sabayon 9 and I really like it. It is a very solid distro. I am wondering whether I prefer it to Arch Linux.

Tim

Does Sabayon support hardware and peripherals out of the box? Or is it closer to the Arch philosophy?

---

### Post by ratcheer on 2012-08-15
> **Random_Dude said:**
> 
Does Sabayon support hardware and peripherals out of the box? Or is it closer to the Arch philosophy?

It is well set up out of the box.

Tim

---

### Post by SpaceAviator on 2012-08-15
It's not rolling release but may I suggest SolusOS. My gaming rig is very new, about a month old and SolusOS was among the very few distributions that work very well out of the box.

---

### Post by Random_Dude on 2012-08-16
> **ratcheer said:**
> It is well set up out of the box.

Tim

Thanks. :)
I think I'll have a look. Since it's based on Gentoo, I was a little afraid that I was going to have to compile everything.

> **SpaceAviator said:**
> It's not rolling release but may I suggest SolusOS. My gaming rig is very new, about a month old and SolusOS was among the very few distributions that work very well out of the box.

My objective now was to have a rolling release distro. I don't have as much time and patience to reinstall Ubuntu every year.
Ubuntu supports all my hardware (except one little problem that forces me to recompile the kernel everytime it updates). But so far I haven't been so lucky with other distros.

Cheers

---

### Post by black veils on 2012-08-16
remember Ubuntu 12.04, and some other systems based on that version, have 5 years support.

---

### Post by Random_Dude on 2012-08-16
> **black veils said:**
> remember Ubuntu 12.04, and some other systems based on that version, have 5 years support.

True.
However, aren't those always lacking on more recent packages?
I had the idea that you have the support, but the more recent versions (12.10, 13.04, etc) would be more updated.

Cheers

---

### Post by black veils on 2012-08-16
i believe that is correct

---

### Post by SpaceAviator on 2012-08-16
You won't have to reintall solusos for the new version. Version 2 will be out pretty soon and the dev is going to release a small iso to update your current installation then there wont be a release for a pretty long time.

If you want rolling, I would suggest Arch. If you dont want to installing it from scratch, Bridge linux is your best friend. It is an arch linux install done for you. Have a look [http://millertechnologies.net](http://millertechnologies.net) 

Also Sabayon is mostly binary these days - they have a pretty good package management system too. You wont have to compile anything unless you want to.

---

### Post by Random_Dude on 2012-08-16
> **SpaceAviator said:**
> 
If you want rolling, I would suggest Arch. If you dont want to installing it from scratch, Bridge linux is your best friend. It is an arch linux install done for you. Have a look [http://millertechnologies.net](http://millertechnologies.net) 

I always wanted to try arch, but I'm not that tech savy compared with most Linux users. Maybe this is a good starting point.

Thanks :)

---

### Post by ratcheer on 2012-08-16
> **Random_Dude said:**
> I always wanted to try arch, but I'm not that tech savy compared with most Linux users. Maybe this is a good starting point.

Thanks :)

Sabayon and Arch happen to be my two favorite distros. Sabayon can give you a very Ubuntu-like experience if you choose the Gnome or KDE "spins", or it can give you a fairly Arch-like experience if you choose the LXDE spin or the minimal CoreCDX spin with Fluxbox desktop. Several other spins are also available, such as E17.

Sabayon has binary packages that are updated on a weekly basis. My installation is now running Linux 3.5, showing just how up-to-date it can be.

On the other hand, Arch is not really as difficult as some people make it out to be. I have used Arch for about ten months and, for the most part, it is solid and easy to maintain. I am much more intimidated by Gentoo and Slackware, both of which I would like to try sometime in the future. Slackware was actually the first distro I ever tried, but that was a long time ago (mid-90's). I worked on it as long as I could, but finally gave up in failure after about a month.

Good luck with whatever you choose.

Tim

---

### Post by kurt18947 on 2012-08-16
PCLinuxOS is pretty similar to Ubuntu in terms of usability.  It uses .rpm packages instead of .deb but includes synaptic by default.  In terms of system requirements it seems pretty similar to Lubuntu though I installed the LXDE version.  The 'standard' out-of-the-box WiFi adapters work with PCLinuxOS.  The only thing I had to research was setting up printers.  They seem to require a package called 'tasks-printing' or similar.  It's available via synaptic but no installed by default.  I believe it's only available in 32 bit but I have it installed on a PIII w/ 512 RAM and it performs pretty well except for flash (of course!).

I tried Sabayon and it looks very good as well.  I couldn't get its installer to cooperate with my 3rd party boot manager.  Sabayon performed quite well on the PIII machine as well, using around 150 mb. RAM  I'd probably have stayed with it if I could have resolved the boot issues.  It might be a good candidate for a USB install.

---

### Post by Majorix on 2012-08-17
Debian Unstable (Sid) is the Linux distro I am running. It is not "unstable" at all as the name suggests.

---

### Post by Random_Dude on 2012-08-19
> **Majorix said:**
> Debian Unstable (Sid) is the Linux distro I am running. It is not "unstable" at all as the name suggests.

I would love to get Debian on my laptop. That's why I tried LMDE (which supposedly uses the same repositories was Debian testing).
Unfortunately, the hardware does not work and I don't know how to install the drivers.

That's why I'm trying to find a rolling release distro that has as good hardware support out of the box as Ubuntu.

Cheers

---

### Post by Majorix on 2012-08-19
Well, it worked on my netbook and my notebook so I didn't experience any hardware problems. It is odd that you did.

---

### Post by Random_Dude on 2012-08-19
> **Majorix said:**
> Well, it worked on my netbook and my notebook so I didn't experience any hardware problems. It is odd that you did.

It was more an issue with the camera and the microphone of my laptop. I need them for skype.
Probably some other stuff too, but these I remember because I spent some time trying to get them to work.

---

