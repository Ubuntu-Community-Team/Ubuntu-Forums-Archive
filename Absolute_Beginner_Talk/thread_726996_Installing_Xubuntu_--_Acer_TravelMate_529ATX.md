---
title: "Installing Xubuntu -- Acer TravelMate 529ATX"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by Brendan Hart on 2008-03-17
Im trying to install Xubuntu but It gets to splash page with loading bar then it goes to BusyBox Initramfs.
How do I get it to work?

---

### Post by gorgon on 2008-03-17
hi.

Where exactly are you in the process of installation? Have you installed xubuntu and are now booting?

Do you know how to edit grub? You would like some more info on why it goes into initramfs, and you'll get that by removing 'quiet' or 'splash', or writing 'nosplash' in the boot options in grub. You do this in the menu where you choose what OS to boot into (if you have more than one) or (i believe..) by pushing esc on startup. When in that menu, press e and then add the above. Then post what you see in the end here in this thread.

---

### Post by cmbcne on 2008-03-17
It sounds just like the problem I had.  Do a search for all posts by "cmbcne" (I've only made one post other than this one).

If the boot process gets part way through and then hangs at the Busybox/initramfs prompt, it could be one of a number of causes from research I've done (usually a hardware detections or video resolution issue).  

In my case, however, the fix was simple.  I had used a torrent file to get an ISO of Xubuntu 7.10, then burned it at 24x speed.  When I booted from the CD I got the busybox/initramfs problem.  I then downloaded the ISO again using HTTP from the Xubuntu web site and burned it at 8x speed -- it worked flawlessly.  

Either the fast burn corrupted the CD or the Torrent version was corrupted when I got it.  Sometimes the "fix" is so stupidly simple we ignore it.  Try it; what have you got to lose?

Hope that helps.

---

### Post by Brendan Hart on 2008-03-18
> **gorgon said:**
> hi.

Where exactly are you in the process of installation? Have you installed xubuntu and are now booting?

Do you know how to edit grub? You would like some more info on why it goes into initramfs, and you'll get that by removing 'quiet' or 'splash', or writing 'nosplash' in the boot options in grub. You do this in the menu where you choose what OS to boot into (if you have more than one) or (i believe..) by pushing esc on startup. When in that menu, press e and then add the above. Then post what you see in the end here in this thread.

it doesnt install, it comes up with the options start or install xubuntu then it goes to busybox initramfs,

also to the cmbcne, I burnt it at 4x

---

### Post by gorgon on 2008-03-18
Hm. ok, I'm no expert on this issue, but my first advice would be to download and burn another copy, or/and try the disk you got on an other machine to possibly rule out that it has something to do with that.

The only time I've gone into busybox is when I had the wrong pointers to my root file system in grub, i.e. the hd(0,1) part in the boot command. But that shouldn't have anything to do with installing.

---

### Post by fparri on 2008-04-30
I could install Xubuntu Hardy 8.04 perfectly on the same laptop :)

---

