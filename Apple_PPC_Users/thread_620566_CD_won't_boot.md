---
title: "CD won't boot"
date: 2007-11-22
forum: Apple PPC Users
---

### Post by rcarter0 on 2007-11-22
Hi everyone--

The problem, in brief: I hold down the C key when I restart, but the CD won't boot

Full exposition: I decided to use my holiday time off to finally install Ubuntu on my iBook dual USB G3,  it's been a frustrating day and I've made no progress. I downloaded the .iso file, I burned the CD, I inserted it into my laptop and restarted while holding down the C key and then... nothing. That is to say, OS X boots up fine, but it ignores me when I tell it to boot from the CD.

So far I've tried:
- Both the i386 and the PPC versions (I now know the latter is the one I want, I downloaded the first one by mistake)
- Two different versions of Ubuntu PPC (Feisty and Gutsy) and one version of Edubuntu
- Burning both the iso file to the disc, and opening the disk image and burning its contents to the disc
- Booting with a known working disc,  my OS 10.4 install DVD, to make sure that the C key thing works. It does, which suggests that there's something wrong with the discs I'm burning

I've looked at a dozen or so threads in which people have expounded on problems installing Ubuntu on  PPC ibooks, but I seem to be the only one who can't get so far as to boot from a CD... what is it that everyone else knows that I don't? Is there an option one needs to select when burning a disc that makes it boot-able? 

Thanks, happy T-day y'all

---

### Post by PaganHippie on 2007-11-22
> **rcarter0 said:**
> So far I've tried:
- Two different versions of Ubuntu PPC (Feisty and Gutsy) and one version of Edubuntu
- Burning both the iso file to the disc, and opening the disk image and burning its contents to the disc

Stick with Feisty for now; Gutsy currently has huge issues with PPC.

I think I see your problem.  Burning the .iso file to the CD, *as a file,* gives you only a backup copy of the .iso file itself.  It's the contents of the file you're interested in.

You had the right idea burning the .iso contents to a new CD, but (if I read your post corrently) the wrong technique.  Simply copying the file system (opening the .iso file and copying its contents) to a CD doesn't make it bootable, as you discovered.  To do it right, check your CD burning software.  There should be an option to "Burn CD Image" or "Burn ISO image" in there somewhere.  Try again using this option; an .iso file is literally an image, not unlike a photograph, of *everything* on the original CD, including boot information that is not in the file system *per se*.  Burn the complete image to the CD and it should boot.

Hope this helps.

---

### Post by rcarter0 on 2007-11-22
Thanks PH, that got me on the right track. -- R

---

