---
title: "Back Track 5"
date: 2011-12-02
forum: Any Other OS
---

### Post by sam-c on 2011-12-02
Please Discuss Black Track 5 based on Ubuntu 10.04 LTS.
I got it on a rather thin DVD Nov 2011 issue of LINUX Magazine.
Back Track 5 R1.
a)Is it safe?
Please Answer FAQ's?
Thanks
Sam
17th Feb 2012:
PS a- I copied DVD to fresh DVD.
b- I have added software like Opera , Chrome games etc... as 10.04 LTS and is like a Normal Ubuntu with BT Extensions.:popcorn:

---

### Post by haqking on 2011-12-02
> **sam-c said:**
> Please Discuss Black Track 5 based on Ubuntu 10.04 LTS.
I got it on a rather thin DVD Nov 2011 issue of LINUX Magazine.
Back Track 5 R1.
a)Is it safe?
Please Answer FAQ's?
Thanks
Sam

An Excerpt from my own blog (See signature)

> 
I briefly mentioned Backtrack earlier, I will actually be using this quite a lot for the demonstrations. People often assume or use the term Backtrack to refer to a hacking/cracking tool itself and it is not. You cannot type backtrack into a command line and hey presto you hack into some system.

There are certainly more versions of it in global possession than there are people who can actually use it at least to its full potential.

Backtrack itself is a toolbox, and within the toolbox lie a wide selection of tools available to help achieve allsorts of goals, but as I said before, owning a chisel wont make you a carpenter or having a toolbox full of tools does not mean you can even bang a nail in straight, I am certainly no backtrack guru and I could not say that I am familiar with every tool in its armoury either, accepting this fact I think makes me a better a security professional IMHO.

Backtrack is a Linux distro (based currently on Ubuntu 10.04) which is built around a specialist kernel that has many particular drivers for devices such as wireless built in so that many devices will work out of the box with specific tools.

You can run it from a Live CD or USB, install to a USB or Virtual Machine or install to local hard drive as dual boot with your current OS, it is not designed to be a OS for everyday use though no reason why you couldnt, but the kernel is specifically geared towards the tools built into it and updates are specific to its approach and not about everyday use or latest applications and drivers. I personally have it on CD, I have BT4 on a USB with persistence which I keep on a keyring and a dedicated dual-boot BT4/BT5 laptop, I also run it from a VM in my main host OS on my main machine.

Owning a copy of Backtrack does not make you a hacker, being able to run some of the tools available on Backtrack does not either, learning what the tools can do for you and how they work and the underlying infrastructures and protocols involved makes you a hacker.

So feel free to go ahead and get yourself a shiny new toolbox and as we move on we will take a look at getting those DIY skills upto scratch.

You wont be able to put a shelf up at the end of it but it will be a lot more fun.

You can get it from [http://www.backtrack-linux.org/downloads/](http://www.backtrack-linux.org/downloads/)

Also there is no requirement to use Backtrack or download it, no pen-test/ethical hack requires it or needs it. All the security auditing tools available out there can be installed and used in other Linux distros if you so desire and some are meant for Windows environments also so take your pick at how you do things.

---

### Post by kio_http on 2011-12-02
It is safe but very stupid.

It is common to see backtrack users in IRC complaining in Kubuntu channels about why things don't work. The problem here is that they cannot keep up with updates, they come with an old version of KDE and other components, which has none of the performance fixes in Kubuntu.

You can install Kubuntu and install all the applications that come with backtrack easily while enjoying a faster and up to date system.

---

### Post by haqking on 2011-12-02
> **kio_http said:**
> It is safe but very stupid.

It is common to see backtrack users in IRC complaining in Kubuntu channels about why things don't work. The problem here is that they cannot keep up with updates, they come with an old version of KDE and other components, which has none of the performance fixes in Kubuntu.

You can install Kubuntu and install all the applications that come with backtrack easily while enjoying a faster and up to date system.

What are you talking about ?

Backtrack can be downloaded with KDE or Gnome version, the default is Gnome version actually.

You can also add any DE you choose.

Updates are not meant to be the latest, as it pertains to the applications and kernel modules built into it, it is not a Distro for everyday use or end user it is a specific Security Auditing distro built around specific tools.

---

### Post by kio_http on 2011-12-02
> **haqking said:**
> What are you talking about ?

Backtrack can be downloaded with KDE or Gnome version, the default is Gnome version actually.

You can also add any DE you choose.

Updates are not meant to be the latest, as it pertains to the applications and kernel modules built into it, it is not a Distro for everyday use or end user it is a specific Security Auditing distro built around specific tools.

I know but the fact being that you can setup Ubuntu in a similar way. And the fact that they ship KDE in an unstable form is not really excusable.

---

### Post by haqking on 2011-12-02
> **kio_http said:**
> I know but the fact being that you can setup Ubuntu in a similar way. And the fact that they ship KDE in an unstable form is not really excusable.

Excusable ?

KDE is not unstable in Backtrack, and it is not marketed or intended to be a desktop OS for any old user.

It is a security auditing distro and intended for that audience.

---

### Post by collisionystm on 2011-12-02
> **haqking said:**
> Excusable ?

KDE is not unstable in Backtrack, and it is not marketed or intended to be a desktop OS for any old user.

It is a security auditing distro and intended for that audience.


Exactly. Back track is specifically for security. Who really cares about the GUI interface when you will always be in the terminal

---

### Post by haqking on 2011-12-02
> **collisionystm said:**
> Exactly. Back track is specifically for security. Who really cares about the GUI interface when you will always be in the terminal

Exactly

most of the time i dont even startx anyways.

everything is in the /pentest dir.

Geez get a grip people, dont download tools you have no clue about

See attachment, that is Backtrack, not a sign of KDE, Gnome or anything else in sight and doesnt need to be

---

### Post by Dangertux on 2011-12-02
Back Track is fine for what it needs to do, IMHO the DE is stable -- I don't have any issues with it, either as an installed OS, VM or USB boot. I use it frequently for both my job and for amusement.

If you are having trouble addressing simple issues with stability (which likely are due to bad configuration on your part) it's probably not the OS you should be using. Just my thoughts.

Hope this helps.

---

### Post by MG&amp;TL on 2011-12-02
The DE IMHO is not stable.

The terminal's fine, but everyone seems to get a kernel panic when they start the X server.

---

### Post by haqking on 2011-12-02
> **MG&TL said:**
> The DE IMHO is not stable.

The terminal's fine, but everyone seems to get a kernel panic when they start the X server.

Who is everyone ?

The thousands of Sec auditors who use it everyday ? NO...which by the way is its intended audience IMO

I have used it in various version with varying DE and no issues.

Besides as already stated it is not about the X anyways, and if you cant get X to work it is likely not the distro of choice for your security auditing

---

### Post by MG&amp;TL on 2011-12-02
> **haqking said:**
> Who is everyone ?

The thousands of Sec auditors who use it everyday ? NO...which by the way is its intended audience IMO

I have used it in various version with varying DE and no issues.

Besides as already stated it is not about the X anyways, and if you cant get X to work it is likely not the distro of choice for your security auditing

Oops. I didn't mean everyone. :( Sorry.

*Quite a few people are experiencing kernel panics when they startx, it's a bug apparently.

I never said it was, I fixed it, but I was more curious than using it to hack or audit stuff. :)

Peace.

---

### Post by haqking on 2011-12-02
> **MG&TL said:**
> Oops. I didn't mean everyone. :( Sorry.

*Quite a few people are experiencing kernel panics when they startx, it's a bug apparently.

I never said it was, I fixed it, but I was more curious than using it to hack or audit stuff. :)

Peace.

no worries.

it is in my opinion a very fine distro, however it is a specialist distro with an intended audience and focused market.

For that audience it works extremely well as intended.

If you are not a sec auditor then it is not worth looking at really, if it is the tools you are interested in they can all be run from any other Linux distro.

Peace

---

### Post by jimrew111 on 2011-12-02
its a good system. fast and all that.
mostly cuz it has g2 lol.

---

### Post by sam-c on 2011-12-04
Thanks Guys,
For your responses.
I am going to have a lot of fun Back Tracking!
Uncle Sam:D

---

