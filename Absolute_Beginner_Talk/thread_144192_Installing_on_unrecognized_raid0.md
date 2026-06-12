---
title: "Installing on unrecognized raid0"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by Sharphedin Olsen on 2006-03-13
Today I finally got ubuntu installed for the first time, but to do so I had to install it on a disk where I conincidentally had some free space, and not where I wanted. The result of not having both xp and ubuntu on the same phsyical drive is that I have to change what hd that is supposed to have boot priority every time. So, since grub & ubuntu  is not on the drive I have xp, I can`t boot xp through grub.

Why all this hassle?
Well, the installer dindn`t - as far as this newbie could see - recognize the two disks that I`ve set up as my system disk for XP (in raid0); they just came up as two seperate and identical drives.
I`d very much like to have ubuntu on that partition as I`ve left 10G unpartitioned just for ubuntu.

So, is there something to be done to have ubuntu recognize the radi0 of my drives?

---

### Post by Sharphedin Olsen on 2006-03-14
I figure I`m allowed to bump this once, having gotten java and the nvidia drivers installed on the same day as my first installation of ubuntu :)

Is there really nothing that can be done to make the ubuntu installer recognize the fact that I have two disks in Raid0, holding an ntfs-partition, but with 10G of free space?

And another question:
Is it possible to have grub select an os to boot that is on a different physical drive?

---

### Post by Sharphedin Olsen on 2006-03-14
Not alot of answers here on this topic :D

What I have found out this far is that this contains the solution: [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)
It`s a little bit over my head as I am completely new to this and feel a bit initmidated by the instructions...

On the other hand I have also learned that this is a non-issue with SUSE [http://www.linuxcompatible.org/installing_fedora_core_4_on_sada_raid0_t33701.html](http://www.linuxcompatible.org/installing_fedora_core_4_on_sada_raid0_t33701.html) 
So I am now considering a migration there.

Anyway, for anyone else researching this topic, now at least you have something to go with :neutral:

---

