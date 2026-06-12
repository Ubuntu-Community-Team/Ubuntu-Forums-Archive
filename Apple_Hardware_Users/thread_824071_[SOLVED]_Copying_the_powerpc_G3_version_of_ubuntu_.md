---
title: "[SOLVED] Copying the powerpc G3 version of ubuntu on the pc..?"
date: 2008-06-09
forum: Apple Hardware Users
---

### Post by spannernick on 2008-06-09
I this possible, I have a Power Mac B and W G3 400 mhz 512mb memory.

It works but it has no os on it so i just need to install ubuntu on it..?

Span..

---

### Post by stream303 on 2008-06-09
There are quite a few B&W owners here with good installs.

You have enough memory to run the live installer, but my personal preference is to use the non-live "alternate" images

Your machine *may* have the 128gb partitioning limitation (you have to keep root at a bit less, say 125gb and the rest can be custom-partitioned) if you have an upgraded hard drive, so keep that in mind, otherwise, with an oem drive, just let guided partitioning "use the whole disk".

---

### Post by spannernick on 2008-06-11
So what do it need to copy it on the pc so it boots on the mac,I have UltraISO..?

What "alternate" images should i use..?

My mac is the one with the scsi in it,if that helps..:)

---

### Post by stream303 on 2008-06-11
Well, pick your choice of the live-cd desktop (because you have a nice amount of ram), or if that gives you trouble, choose the non-live "alternate" which merely does an install right off the bat:

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

Keep these two good faqs handy:

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
and
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

It is also good to know your system specs, such as video card, and possibly if your hard drive has been upgraded:

[http://www.everymac.com/systems/apple/powermac_g3/index-powermac-g3.html](http://www.everymac.com/systems/apple/powermac_g3/index-powermac-g3.html)

For example, you *may* run into the issue of having to keep your install (or at least the root partition) under 128gb, (say 124gb to be safe)

Also do you want to dual-boot, or dedicated the whole drive to Ubuntu?

Look through the faqs, and see if you are comfortable with what might be an install that is going to require a bit of work.  It isn't too hard, but it may not be a "drop-in" installation. :)

---

### Post by cyberdork33 on 2008-06-11
> **spannernick said:**
> So what do it need to copy it on the pc so it boots on the mac,I have UltraISO..?
If you are asking how to use the iso file, you need to use a disc burning utility to burn it to disc. What OS are you trying to use to burn the ISO? Windows? OS X?

---

### Post by spannernick on 2008-06-11
> **cyberdork33 said:**
> If you are asking how to use the iso file, you need to use a disc burning utility to burn it to disc. What OS are you trying to use to burn the ISO? Windows? OS X?

I am using windows xp and i have UltraISO on it..?

---

### Post by cyberdork33 on 2008-06-11
> **spannernick said:**
> I am using windows xp and i have UltraISO on it..?
imgburn is a good app and is free:
imgburn.com

You can use it to burn the image to a CD-R. Burn Slowly!

---

### Post by spannernick on 2008-06-11
> **stream303 said:**
> 
It is also good to know your system specs, such as video card, and possibly if your hard drive has been upgraded:

[http://www.everymac.com/systems/apple/powermac_g3/index-powermac-g3.html](http://www.everymac.com/systems/apple/powermac_g3/index-powermac-g3.html)

For example, you *may* run into the issue of having to keep your install (or at least the root partition) under 128gb, (say 124gb to be safe)

Also do you want to dual-boot, or dedicated the whole drive to Ubuntu?



Ok thanks all..

This is my system..

The Apple Power Macintosh G3/400 (Blue & White), based on the Yosemite architecture, features a 400 MHz PowerPC 750 (G3) processor with 1 MB of backside cache, 512 MB of RAM, a 9 GB Ultra2 SCSI hard drive, a Sony CDRW Drive i put in myself, and an ATI Rage 128 GL graphics card with 16 MB of SDRAM.

---

### Post by spannernick on 2008-06-11
> **cyberdork33 said:**
> imgburn is a good app and is free:
imgburn.com

You can use it to burn the image to a CD-R. Burn Slowly!

So i have download imgburn and ubuntu-8.04-desktop-powerpc.iso and i am going to copy it at 1X.

Is that ok..?

---

### Post by cyberdork33 on 2008-06-11
> **spannernick said:**
> So i have download imgburn and ubuntu-8.04-desktop-powerpc.iso and i am going to copy it at 1X.

Is that ok..?If it will burn that slow... Most will only go down to 2x.

---

### Post by stream303 on 2008-06-12
Note that most have the best results with CD-R media and not CD-RW, although if that new Sony drive you installed is pretty recent, you might get away with it, and also be able to burn at higher speeds - as long as the mac itself doesn't seem to object to the new arrival. :)

Still, I like to burn install images at pretty low speeds anyway.

---

### Post by spannernick on 2008-06-12
I copied it at 2x with imgburn and it works..;)

Thanks so very much for all your help,this forum is great,my powerpc is working with the live CD,i am using firefox as i type..:)

Thanks All..

Span..

---

### Post by spannernick on 2008-06-12
Just installed to my hard drive and all system GO..;)

Thanks..

Span..

---

### Post by spannernick on 2008-06-12
All Done..

---

### Post by spannernick on 2008-06-12
All sorted now,Thanks for all your help..:)

---

### Post by cyberdork33 on 2008-06-12
You should mark this thread as solved (see thread tools menu), and ask new questions in a new thread.

Thanks.

---

