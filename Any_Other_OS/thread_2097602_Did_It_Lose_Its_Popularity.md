---
title: "Did It Lose Its Popularity?"
date: 2012-12-23
forum: Any Other OS
---

### Post by Majorix on 2012-12-23
There were days when literally everyone was going for an Arch Linux installation. However I see that people aren't that excited about it anymore. Do you agree?

PS: What other rolling-release can I use instead?

---

### Post by Petro Dawg on 2012-12-23
I'm assuming people can find an existing distro which now fits their needs quite well; be it Ubuntu, Fedora, or Mint (or one of the countless others out there) without having to build everything from scratch.   

Typically one of the existing distros can be modified sightly fit your needs nearly perfectly with very little time investment.  I suspect Arch only appeals to perfectionists with too much time on their hands.

---

### Post by Version Dependency on 2012-12-23
Arch is still quite popular for Linux enthusiasts...but probably not all that popular for the general Linux user who just wants something quick to install and without the hassles of installing drivers, codecs, etc.

>  PS: What other rolling-release can I use instead?

You could try Sabayon.  It's very nice...but I didn't care for how slow the package manager was.

---

### Post by haqking on 2012-12-23
> **Majorix said:**
> There were days when literally everyone was going for an Arch Linux installation. However I see that people aren't that excited about it anymore. Do you agree?

PS: What other rolling-release can I use instead?

[https://en.wikipedia.org/wiki/Rolling_release#Rolling_distributions:_further_details](https://en.wikipedia.org/wiki/Rolling_release#Rolling_distributions:_further_details)

Take your pick

---

### Post by claudecat on 2012-12-23
If anything Arch and its ever growing list of derivatives seem to be growing in popularity, if Distrowatch page hit rankings can be believed. Raw Arch is indeed a pain to install, but something like Manjaro or Bridge are relatively easy and give you a fully functional system right from the start. 

Personally I like the Arch way of doing things, especially the speed and elegance of pacman. It's not nearly as daunting as many people seem to think and results in a system that will always be up to date and will never need to be reinstalled.

---

### Post by offgridguy on 2012-12-23
> 
You could try Sabayon.  It's very nice...but I didn't care for how slow the package manager was.
Having used sabayon ,i would agree.

---

### Post by andrew.46 on 2012-12-23
> **Majorix said:**
> PS: What other rolling-release can I use instead?

The development version of Slackware, known as Slackware -current could be considered a rolling release and has the benefit of being pretty stable for the most part. Not recommended for production machines etc etc.

---

### Post by lykwydchykyn on 2012-12-24
I'm sure it's as popular as ever, just the folks who hyped it on these forums seem to have moved on to other things.

---

### Post by kiyop on 2012-12-24
> **Majorix said:**
> What other rolling-release can I use instead?
I do not know well the meaning of "rolling release", but if you want new packages...
Aptosid, Siduction.

My updated Sabayon has kernel-genkernel-x86-3.5.0-sabayon now.
My updated Aptosid has vmlinuz-3.7-1.slh.1-aptosid-686 now.
My updated Siduction has vmlinuz-3.7-1.towo-siduction-686 now.
My updated Arch has vmlinuz-26 (version 3.6.10-1-ARCH).

But maybe I do not know how to update the kernel on sabayon correctly. :oops:

You know, on Arch, 
```
pacman -Syu
```updates.

For Aptosid and Siduction, update is very easy.
```
apt-get update
apt-get dist-upgrade
apt-get autoremove
apt-get autoclean
```To find newer kernel:
```
apt-cache search linux-image
```To install newer kernel (such as 3.7-1.slh.1-aptosid-686):
```
apt-get install linux-image-3.7-1.slh.1-aptosid-686
```To remove old kernel:
```
apt-get purge linux-image-OLD_KERNEL_VERSION
```

---

### Post by benerivo on 2012-12-24
I think the Arch user base is still growing fast. It's hard to tell, but looking at the number of people logged on to the arch forums (currently 227 as i'm typing this) it is more than i remember it being when i first tried it a few years ago. Compare that to the LinuxMint forums, where there are currently 177 users online. I know that's very unscientific, but there's not much else to go by other than [google trends]("http://www.google.com/trends/explore#q=arch,%20ubuntu,%20fedora,%20debian") or the fact that whenever you use google to search for something linux related (eg. "linux partitioning"), the arch website always seems to be in the top five hits.

---

### Post by mips on 2012-12-24
> **Majorix said:**
> There were days when literally everyone was going for an Arch Linux installation. However I see that people aren't that excited about it anymore. Do you agree?


No. I think it's popularity is actually increasing. People just don't mention that they are using it here any more.

---

### Post by snowpine on 2012-12-24
Discussion here of non-Ubuntu distros is down significantly in the past few years, I don't think it's an Arch-specific thing at all. :)

---

