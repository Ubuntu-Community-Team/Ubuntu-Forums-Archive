---
title: "vmware"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by billgoldberg on 2008-01-06
I want to install vmware through add/remove, I get an error saying "VMware Player cannot be installed on your computer type (i386)".

That can't be right, can it?

Anyhow, is there any other software like this I can install?

---

### Post by zasf on 2008-01-06
> **billgoldberg said:**
> Anyhow, is there any other software like this I can install?

virtual box, see [www.virtualbox.org](www.virtualbox.org). Add their repositories to your sources.list and install virtualbox package.

---

### Post by forestpixie on 2008-01-06
whjat do you get from synaptic?

Some people have had a can't install on you computer type with sources.list problems, check that you don't have everything commented out

---

### Post by melopsittacus on 2008-01-10
Hi! I am having the same problem as billgoldberg. I looked at my sources.list and a lot of repositories are commented out. Which one do I have to enable in order to get vmware? (By the way: how is that possible that a repository is disabled, but I can still see its contents but cannot install them?)

---

### Post by forestpixie on 2008-01-10
open software sources in system > admin

tick the main, universe, restricted and multiverse repos and reload

once it's finished try again

---

### Post by Seti on 2008-01-10
> **forestpixie said:**
> open software sources in system > admin

tick the main, universe, restricted and multiverse repos and reload

once it's finished try again

Sorry, but that doesn't work.
You actually have to go into Synaptic, not Add/Remove, and install VMware server for it to work.

---

### Post by billgoldberg on 2008-01-10
I downloaded it from vmware's website and it seems to work.

It was quite a hassle to get an .iso going in vmware player.

this included download an .vmx (i think) file and editing it with gedit.

Virtualbox didnt work for me, all I got were errors when I wanted to open an .iso

Anyways, I think I'll pass on the wole virtualisation "hype". I don't see any point in using it unless to try out a distro (once every 6 months or so). But i'm 100% windows free and apple (itunes) free so I don't need any of those programs.

---

