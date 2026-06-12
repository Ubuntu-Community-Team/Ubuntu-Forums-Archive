---
title: "hibernate breaks swap"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by in_flu_ence on 2007-04-03
Hi,

     Whenever I use hibernate, it caused the swap drive (e.g /dev/hda2) to be unformatted or unrecognised. I can reformat the partition using gparted but it doesn't resolve the issue at hibernate.

I have read the other post about using swapon and etc. Those are useful to fix things but I think that there might be a bug somewhere in hibernate that doesn't really recognise or address the swap properly.

     Does anyone having similar problem?

BTW, I am using ubuntu edgy on my laptop.

Thanks alot

---

### Post by johnny4north on 2007-04-03
what make and model of laptop?

---

### Post by anaconda on 2007-04-03
I dont know, but I have heard that you need your swap to be (atleast)  2x the size of your RAM to get hibernate to work.

---

### Post by eljalill on 2007-04-03
Hibernate breaks my swap too... even when it was twice my RAM (swap was 1GB and RAM 512 MB). But then maybe it has to be more than 2xRAM?
Also running edgy on laptop (Fujitsu Siemens Lifebook S7010).
I usually just don't hibernate any more ... :) . But if there is a fix I'd be interested to know, too.

---

### Post by in_flu_ence on 2007-04-03
I have a compaq v2000 series. I have 3.0gb for my swap with about 1.5gb of RAM. again 2x

It used to be working until lately. I didn't realise it 'cause i only use hibernate once in a while.

But I need the hibernate function especially when i move from conference room to conference room. It saves me time from loading things up again.

Any help?

---

### Post by BUGabundo on 2007-04-04
> **in_flu_ence said:**
> I have a compaq v2000 series. I have 3.0gb for my swap with about 1.5gb of RAM. again 2x

It used to be working until lately. I didn't realise it 'cause i only use hibernate once in a while.

But I need the hibernate function especially when i move from conference room to conference room. It saves me time from loading things up again.

Any help?

actually hibernate takes longer then normal boot, specially with all that RAM.
You must be referring to suspend-to-ram, right?

---

### Post by in_flu_ence on 2007-04-04
The RAM bit was to respond to the post from anaconda.

I actually have a faster hibernate than complete restart somehow (including reloading the programme that I was using).

Nope. I don't mean suspend 'cause by moving from one place to another, i do mean some distance rather than really one room to another. Suspend works for me within my office area.

:) Hopefully we will find something out. since i think there are quite a number of post about hibernate but nothing that works at least for me yet:)

Thanks for all.

---

### Post by jakev383 on 2007-04-04
> **in_flu_ence said:**
> Hi,

     Whenever I use hibernate, it caused the swap drive (e.g /dev/hda2) to be unformatted or unrecognised. I can reformat the partition using gparted but it doesn't resolve the issue at hibernate.

I have read the other post about using swapon and etc. Those are useful to fix things but I think that there might be a bug somewhere in hibernate that doesn't really recognise or address the swap properly.

     Does anyone having similar problem?

BTW, I am using ubuntu edgy on my laptop.

Thanks alot

Same here. Mine WAS working until I shrunk my ext3 partition to grow my swap (I added more RAM, so needed more swap anyway). Hasn't worked since. I have a thread going on this:
[http://ubuntuforums.org/showthread.php?t=400673](http://ubuntuforums.org/showthread.php?t=400673)
I'm running Edgy on a Dell E1505 laptop. Hibernate used to work. I've got 2G of RAM and 1G of swap - my hibernate used to work when I had 1G of RAM and 468M of swap (that was before Beryl also....:) )

---

