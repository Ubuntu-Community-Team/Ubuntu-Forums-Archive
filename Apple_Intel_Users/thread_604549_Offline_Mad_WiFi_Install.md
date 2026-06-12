---
title: "Offline Mad WiFi Install"
date: 2007-11-06
forum: Apple Intel Users
---

### Post by Chrisj303 on 2007-11-06
Hi!

For several irritating reasons, I am now unable to use my computer with a wired connection at all:(
I am contemplating installing Gutsy on my MBP, but I need wireless.

Could someone in the know point me towards the files I need to download, aside from the Madwifi package,  through OSX - so i can transfer them to Ubuntu and install wireless wile offline?

Any help would be much apreciated!:)


thanks
chrisj303

---

### Post by mert on 2007-11-11
I haven't tried it myself but I think you'll only need the madwifi package.  when you install gutsy without a network connection, the installer will disable the network software sources.  when you install the build-essential packages you will be asked to insert the CD rom.  I think it will install the files you need from the CD.

So, leeching wifi off of the neighbors, eh?  :)

---

### Post by ronocdh on 2007-11-11
> **mert said:**
> I haven't tried it myself but I think you'll only need the madwifi package.  when you install gutsy without a network connection, the installer will disable the network software sources.  when you install the build-essential packages you will be asked to insert the CD rom.  I think it will install the files you need from the CD.

So, leeching wifi off of the neighbors, eh?  :)
I believe that you can at any time go into Software Sources and uncheck the CD-ROM option.

You'll need the madwifi packages as well as build-essential. Install build-essential first, so you'll be able to compile the madwifi packs, then follow whatever instructions you have. If you come across any dependencies you can't satisfy, add them to your list, then grab then in OS X and try again.

Good luck, and let us know how it goes!

---

### Post by Chrisj303 on 2007-11-11
Thanks for the replys!

I will be giving this a go tomorrow morning.

And NO, I'm not ripping next doors broadband!! - I'm sharing a router between 5 of us (all Uni students) I also haven't got an ethernet cable - and even if I did my housemates would freak out if I hogged it for the afternoon.

So let me get his straight - I can install build-essentials from the CD ROM? - if so,  thats no problem.

I will post back either way - as this could be helpful to someone else. I really wish that a self-contained .deb file for MadwiFi existed....

---

### Post by XeutonMojukai on 2007-11-14
ChrisJ, please do, as I am in the *exact* same situation, and would like to know how you do (and let others know how my results compare).

~ XM

---

### Post by Chrisj303 on 2007-11-14
I went to do it today, but I'm having a hard time even partitioning my drive! Need to verify/repair my disk, but I have lent my leopard DVD to my brother (lives 300miles away), Doh! 

I've just aquired a Tiger install DVD, so hopefully I will be able to sort it out with this....

I **will** report back **as soon** as I have tried to install Madwifi offline. I promise.

---

### Post by cyberdork33 on 2007-11-14
> **Chrisj303 said:**
> I went to do it today, but I'm having a hard time even partitioning my drive! Need to verify/repair my disk, but I have lent my leopard DVD to my brother (lives 300miles away), Doh! 

I've just aquired a Tiger install DVD, so hopefully I will be able to sort it out with this....

I **will** report back **as soon** as I have tried to install Madwifi offline. I promise.

Can you not boot into single-user mode (CMD-S) and repair from there?

---

### Post by Chrisj303 on 2007-11-14
> **cyberdork33 said:**
> Can you not boot into single-user mode (CMD-S) and repair from there?


Hey, thanks *a lot* for that mate! - I had no idea you could repair a disk/volume like that.
From the single user command line just did : /sbin/fsck -f

Disk utility is now allowing me to partition. Thanks.


I will post back in the next couple days regarding the offline wireless install..

---

