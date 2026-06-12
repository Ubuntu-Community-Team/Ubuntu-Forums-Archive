---
title: "Installing Gentoo from a live DVD"
date: 2011-08-10
forum: Any Other OS
---

### Post by tech291083 on 2011-08-10
Hi,

I have just downloaded Gentoo 11.0 DVD and would love to install it on a single hard drive which already has Fedora 14 and Ubuntu 10.10, is it possible to have Gentoo here as the third OS?

If the above scenario is not possible then, I would be happy to install Gentoo on the entire hard drive. But it looks like that there are a very few sites talking or describing the Gentoo installation on a hard drive, so please guide me step by step if possible, here is what I have ben looking at lately. Thanks


[http://dev.gentoo.org/~neddyseagoon/HOWTO_DVD11.xml]("http://dev.gentoo.org/%7Eneddyseagoon/HOWTO_DVD11.xml")

---

### Post by KurtCho on 2011-08-10
yes, it is totally doable as long as you have enought free space on your disk. All that you need to do is use gparted to free some space and then you can install gentoo to that partition.
personally the way i have my disk set up is to have 4 partitions, gentoo system, ubuntu system, documents, and swap.
good luck!:D

---

### Post by tech291083 on 2011-08-10
> **KurtCho said:**
> yes, it is totally doable as long as you have enought free space on your disk. ....
personally i have my disk set up is to have 4 partitions, gentoo system, ubuntu system, documents, and swap.



Ok, this is good news to me. So my plan of 3 OS together on the same hard drive can be a reality. In your settings, you must have set up some links from Ubuntu to  Documents paritition and Gentoo to Documents paritions to access the files, am I right? Thanks a lot.

---

### Post by KurtCho on 2011-11-11
exactly
I just created a symbolic link eg. -s folder (where the link should be made) (what to link)
cheers:)

---

