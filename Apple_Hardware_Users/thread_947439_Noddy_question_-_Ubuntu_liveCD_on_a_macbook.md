---
title: "Noddy question - Ubuntu liveCD on a macbook"
date: 2008-10-14
forum: Apple Hardware Users
---

### Post by zzztownsend on 2008-10-14
Hi folks

Apologies for the simpleton question, but can I boot a macbook on a ubuntu 8.04.1 liveCD? 

I'm reasonably handy with ubuntu on a PC, but I have a colleague who has broken his mac and it won't boot. He has a external hard-drive and I just want to copy the personal contents off and then re-install an OS

Alternatively are there any other distros that may be better with macbook?

Cheers

Matt

---

### Post by cyberdork33 on 2008-10-14
> **zzztownsend said:**
> Hi folks

Apologies for the simpleton question, but can I boot a macbook on a ubuntu 8.04.1 liveCD? 

I'm reasonably handy with ubuntu on a PC, but I have a colleague who has broken his mac and it won't boot. He has a external hard-drive and I just want to copy the personal contents off and then re-install an OS

Alternatively are there any other distros that may be better with macbook?

Cheers

Matt
yes it will work. Note that you will probably only be able to get read access to the HFS+ filesystem used by OSX (but that should be all you need). Also, be aware of file permissions. The files on the OSX partition will not be 'owned' by your Ubuntu user, so you will need to become root or open a root browser in order to copy them anywhere.

---

### Post by zzztownsend on 2008-10-15
Great, I'll give it a go. Thanks for the tip on file system.

Maybe i'll get another convert!

Cheers

Matt

---

