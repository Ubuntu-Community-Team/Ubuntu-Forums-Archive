---
title: "Gnash binaries for PPC/iBook on Ubuntu?"
date: 2007-02-21
forum: Apple PPC Users
---

### Post by ebeyer on 2007-02-21
I'm a casual linux user without much IT experience.  I have an iBook running Ubuntu 6.10 and I want to install Gnash.  I've downloaded the source code but have been unable to create a usable binary.  Has anyone here been able to compile Gnash?  I'd be especially interested in the browser plugin.

If somebody could link me to a usable binary I'd be grateful.

EB

---

### Post by maggot_brain on 2007-02-22
I'm pretty sure Gnash is already in backports so you don't have to compile it.  Also gnash only supports OpenGL at the minute so you'll have to have 3d acceleration working.

Ananda

---

### Post by ebeyer on 2007-02-22
Is that hard to do on the iBook?  I have an ATI radeon mobility on mine.  Do I need to go through the steps I went through on my PC to set up XGL or AIGLX?

EB

---

### Post by maggot_brain on 2007-02-22
I forgot you're the guy with the same laptop as me!  I've not even tried using 3d acceleration on this machine.  It's only got 16MB of video ram so it doesn't even seem worth it.  You'll have to ask around.  Sorry I can't be of more help.

Ananda

---

### Post by ebeyer on 2007-02-23
Do you need 3D acceleration for flash/gnash? Flash seemed to work on my non-accelerated Celeron-based ubuntu box.

Seems like PPC is big enough somebody would have compiled the binaries for it and made it more available, either on some unofficial repository or through something like EasyUbuntu, but no dice.

---

### Post by maggot_brain on 2007-02-23
There's no official flash player of plugin for Linux on the PPC platform.  Gnash is a GNU project to provide a free alternative.  Gnash is under development and needs OpenGL at the minute.

---

### Post by BryannMelvin on 2007-02-28
I recently compiled gnash for use on a g3 ibook,

I made a deb but notice that it puts the plugin in my home directory...so this wouldn;t work for another's computer... I would have to compile it as root. I might do this is there is demand for it in Dapper.

there is no need of 3d acceleration to use gnash.,...depending on how it was set up. I compiled my version against cairo.

FWIW the plugin only works in firefox...stalls in opera and konqueror.

---

### Post by ebeyer on 2007-02-28
So I stumbled across 'THE SOLUTION':

Use EasyUbuntu to add extra repositories (possibly not necessary).

In Synaptic, enable universe and multiverse repositories.

Search for "gnash" and install everything.  

Done.

---

### Post by spikee on 2007-03-01
so how well does gnash work in terms of flash on powerpc? It looks really promising although it hasn't been updated in a while.

---

### Post by ebeyer on 2007-03-01
Well, I at least don't get the annoying error that I don't have a flash plug-in.  However, many flash animations don't work the way the commercial product does.  Actually, most don't.  Homestarrunner.com is a total bust.  Apple's web site works hit and miss.  I haven't tried much else yet.

EB

---

### Post by spikee on 2007-03-01
alright thanks. it's better than nothing :confused:

---

### Post by dpny on 2007-03-01
> **ebeyer said:**
> So I stumbled across 'THE SOLUTION':

Use EasyUbuntu to add extra repositories (possibly not necessary).

In Synaptic, enable universe and multiverse repositories.

Search for "gnash" and install everything.  

Done.

Tried this, and nothing. In addition, EasyUbuntu modifies your sources.list file, including a lot of Breezy depositories, which would be a bad thing.

---

