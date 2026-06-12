---
title: "Installing Make without access to the 'net"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by cornellfinch on 2006-04-25
Good afternoon!

I know this sounds like a strange question (as in why would I want to), but is there a way to install "make" without having access to the 'net on the ubuntu machine?

I am trying to get my Belkin wireless card working with ndiswrapper and I need to "make" it first.  I don't have any connection to my router through a wired cable (it would need to be 30m+) but I can get hold of one as a last resort.

Make is no problem in Breezy (as it's included for install using sudo apt-get), but I cuurently have Dapper Beta installed and it doesn't appear to have it.

Yep, I can switch to Breezy if required but would prefer to stay with Dapper as it's the latest version (albeit beta!).

If have net access through my XP machine.

I know this sounds like I know what I'm talking about, but I really am an absolute newbie at this!

Thanks in advance for any help.

Collin

---

### Post by macdo on 2006-04-25
On your Xp machine, go to [http://archive.ubuntu.com/ubuntu/pool/main/m/make](http://archive.ubuntu.com/ubuntu/pool/main/m/make)

Download and copy (to CD, floppy, USB drive, whatever) the relevant make .deb 
Never underestimate the bandwith of a stationwagon roaring down the highway: walk your copy over to the ubuntu machine.
Install it (on Dapper, you just need to double click - easy!)
Sorted!

---

### Post by Pjukern on 2006-04-25
Hi.

I ran the following command to install the build essentials package wich contain the "make" package. I didnt have net access at the time I did this.

```

sudo apt-get install build-essentials

```

---

### Post by cornellfinch on 2006-04-25
Fantastic! Thanks macdo - I'll try that when I get two minutes :)

Pjukern - thanks for the info!  I tried (and it worked) that with Breezy, but no joy with Dapper unfortunately :(

---

### Post by cornellfinch on 2006-04-25
Madco - worked a treat, thanks.

Faor information, I found build-essentials in the "pool" (see madco's link) and downloaded that but got an error message when I double clicked to install it:

```
Error: Dependency is not satisfiable: libc6-dev|libc-dev
```

I suspect I downloaded the wrong package but it's not *too* important now.

Next question (sorry!):

In [this thread](http://ubuntuforums.org/showthread.php?t=165689) it mentions installing headers with:

linux-headers-2.6.12-9-386
and 
linux-headers-2.6.12-9

using Synaptic. This is still for installing the ndiswrapper.  I've had a look through the pool but can't see them, is there a .deb package for these files?

Cheers again!

---

### Post by macdo on 2006-04-25
You don't need the headers to install ndiswrapper from the .deb.

If you need the package, I've put it on my website [here]("http://macdo10.free.fr/deb/")

---

### Post by cornellfinch on 2006-04-25
You are a star!  Thankyou so much :)

---

### Post by macdo on 2006-04-25
I can't code, but at least I can help other strugglers :-) 
My pleasure!

---

### Post by Rower on 2006-07-17
Oh man.. thanx :D i also needed this
You really are helpfull, keep that up =)

---

### Post by az on 2006-07-17
You *DON'T* need to recompile ndiswrapper.

Ndiswrapper-utils is on the cd.  SO is build-essential.

The Desktop cd has a repo on it apart from the live cd session.  Boot into your installed ubuntu system and put the cd back into the drive.  You will be brought to the package manager and you will be able to install build-essential or ndiswrapper-utils.

The ndiswrapper modules are already part of your kernel.

If you installed using the alternate cd, that stuff is already part of your package list.

---

