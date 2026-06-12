---
title: "I want to test drive Ubuntu before I kill Fedora"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by GregAllen on 2006-11-07
I would like to just try out Ubuntu before I decide to deep-six Fedora. 

Actually, I'd kind of like to try out openSUSE, too. 

Can I set up a multiple boot?  

I have no idea even where to begin. 

Thanks!

PS: I'm a newbie to Linux (but not computers) and all the program names still sound like gibberish to me!  (like "themes in Gnome in the Hoary") So any dummies style help is highly appreciated.

---

### Post by boban on 2006-11-07
You can test ubuntu from livecd... 

If you want to install it, you'll have to create partition for Ubuntu, then install it - installer SHOULD configure dual/multi boot automatically for you... (I didn't try it for other linux, but it worked for win)

---

### Post by taurus on 2006-11-07
I have both Gentoo and Ubuntu running on a same machine and GRUB (bootloader) can handle both just fine.  My friend even has three different Linux distros on his machine and he can boot all three so dualbooting ot multi-booting is not a problem at all.

---

### Post by boban on 2006-11-07
> **taurus said:**
> I have both Gentoo and Ubuntu running on a same machine and GRUB (bootloader) can handle both just fine.  My friend even has three different Linux distros on his machine and he can boot all three so dualbooting ot multi-booting is not a problem at all.

Grub can handle this for sure... I have both Gentoo and Ubuntu installed too. But I installed Gentoo from Ubuntu, and manually updated Grub configuration... 

But I don't know what will happen if Ubuntu installer find another distro on hard drive... Will it install Grub on it's own partition or will it modify existing Grub configuration? If first - he is likely to have some trouble if he deletes Ubuntu partition... If the latter - he will have some trouble if he removes fedora...

---

### Post by taurus on 2006-11-07
You can have Ubuntu install it own GRUB on MBR, not install GRUB at all, or install it on the first section of whatever partition Ubuntu is it.  So, if you don't want to overwrite FC's GRUB, then don't install GRUB and just modify GRUB in FC to include an entry for Ubuntu!

---

### Post by boban on 2006-11-07
> **taurus said:**
> You can have Ubuntu install it own GRUB on MBR, not install GRUB at all, or install it on the first section of whatever partition Ubuntu is it.  So, if you don't want to overwrite FC's GRUB, then don't install GRUB and just modify GRUB in FC to include an entry for Ubuntu!

Good to know...

But GregAllen said:
>  
PS: I'm a newbie to Linux (but not computers) and all the program names still sound like gibberish to me! (like "themes in Gnome in the Hoary") So any dummies style help is highly appreciated.


I don't know if what we are writing here make any sense to him :)

---

### Post by GregAllen on 2006-11-08
So, thanks guys for the helpful posts.

I gather from your replies that to get started, I need to learn GRUB. BTW, I found wat seems to be a good article bout it on [http://en.wikipedia.org/wiki/GRUB]("http://en.wikipedia.org/wiki/GRUB")

I gather that creating a partition is a totally separate process than GRUB. But which program does that?  

Is the term "partition" the same in Lunux as it is in DOS/Windows? (i.e. a separate logical disk?)

(BTW, if I can do a multiple boot, I'll probably not delete Fedora if it's no conflict being there. . This is my wife's computer and she never fills up her hard disks. )

---

### Post by bodhi.zazen on 2006-11-08
> **GregAllen said:**
> So, thanks guys for the helpful posts.

I gather from your replies that to get started, I need to learn GRUB. BTW, I found wat seems to be a good article bout it on [http://en.wikipedia.org/wiki/GRUB]("http://en.wikipedia.org/wiki/GRUB")

I gather that creating a partition is a totally separate process than GRUB. But which program does that?  

Is the term "partition" the same in Lunux as it is in DOS/Windows? (i.e. a separate logical disk?)

(BTW, if I can do a multiple boot, I'll probably not delete Fedora if it's no conflict being there. . This is my wife's computer and she never fills up her hard disks. )

You may partition with fdisk or gparted, both on the Ubuntu Live CD.

You may find this helpful as an introduction to Linux partition terminology:

[Basic partitioning](http://ubuntuforums.org/showthread.php?t=282018)

_Note_: Fedora uses a LVM partitioning scheme which is different.

---

### Post by funrider on 2006-11-08
you can download vmserver and build your own ubuntu vm system before you kill the current OS. you have nothing to lose other than time.

---

### Post by GregAllen on 2006-11-21
Thanks for the advice, everybody. 

I'll be honest... I whimped-out and just did a clean install of Ubuntu. 

The more I thought about it the less I felt a need to keep my copy of Fedora on there.   I'm just not that happy with it. 

But I still would like to do a dual-installation of openSUSE, so not all your advice was wasted!

Thanks again.

---

