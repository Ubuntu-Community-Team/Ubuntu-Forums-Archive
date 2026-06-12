---
title: "Resizing Partition using Live CD?"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by jankind on 2007-06-04
Hi all!
Well, here is my second question so far. Everything is going really well as I am a complete newbie and am feeling pretty fortunate with my new adventure here. I am, however, having a bit of trouble resizing the partitions using GParted. I read several other threads regarding this, one in particular stating that the poster run the Live CD so that the ntfs one could be unmounted and THEN resized...

This is what I am doing and I keep getting an error saying that it can't be resized because it's mounted. SO then I unmount and it does for a minute or so then says:

umount: /media/disk-1: device is busy
umount: /media/disk-1: device is busy
So I can't keep it unmounted and it won't allow me to resize...

Any advice??
Thanks in advance!

---

### Post by starcraft.man on 2007-06-04
Hold on, got me a bit confused in that (admittedly I am tired its kinda late)... Firstly, you are actually booting up into the live CD right (not just gparted in Ubuntu)? If thats the case, I'm kinda at a loss... the whole point of the live CD is that all drives remain unmounted unless ya tell em otherwise... Has this happened more than once i.e. have you rebooted multiple times into the CD and gotten this result? If thats the case, all I can think of is its some sort of glitch resulting from bad burn/image.

I'd redownload the image, then burn at low speed (4X) and try again... unless someone's seen this error, seems weird.

---

### Post by jankind on 2007-06-04
Hmm, well yeah, I'm booting with the Live CD, which I did burn at a pretty slow speed, I think it was 8X... (My install went without a hitch and all is running fine) but NO to the other question . I did NOT reboot to the CD several times. Just this once and tried the described exercise in GParted about a half dozen times. I think I'll at least try a reboot again like you suggest.
I do apologize for any cryptic or confusing wording as I admittedly am a complete newbie.
Thanks for your reply.

---

### Post by starcraft.man on 2007-06-04
> **jankind said:**
> Hmm, well yeah, I'm booting with the Live CD, which I did burn at a pretty slow speed, I think it was 8X... (My install went without a hitch and all is running fine) but NO to the other question . I did NOT reboot to the CD several times. Just this once and tried the described exercise in GParted about a half dozen times. I think I'll at least try a reboot again like you suggest.
I do apologize for any cryptic or confusing wording as I admittedly am a complete newbie.
Thanks for your reply.

Hmmm, maybe a one time glitch then... can't say I've ever had any trouble like this with GParted. And no, your probably not being cryptic... I'm just tired, been busy day. I was setting up a lot of VMs on my home PC for testing. Fedora and openSUSE really really take a long time to install. >.>

---

### Post by jankind on 2007-06-04
Gotcha, thanks alot.
Well I rebooted with the Live CD again and it's strange. Both the ntfs and ext3 ones were unmounted when I started GParted. Then when I go to resize it gives me the error saying that it's mounted and then I see the locked icon beside them, which are NOT there when I start it up. Is there a possibility that I am doing something really stupid here (sure I opened myself up for a wisecrack there ;) ) LOL but seriously...maybe I'm missing something.
Thanks again!

---

### Post by jerrylamos on 2007-06-04
Not sure, sounds like Ubuntu Feisty 7.04 which does have a nasty habit of mounting things in the middle of a format and other such gifts.  Reading between the lines, they tried to speed up Feisty by doing a lot of things in parallel which is NOT what you want when partitioning and formatting.

I'd suggest the standalone Gparted from

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

which has been pretty reliable for me.

Cheers, Jerry

---

