---
title: "Help with installing from hard drive"
date: 2008-11-04
forum: Apple Hardware Users
---

### Post by bazookaaa on 2008-11-04
Hello,

On my iBook G4, I'm trying to install Ubuntu 8.10 from my hard drive (following [this guide]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/boot-drive-files.html#files-newworld")) but I'm stuck. After (successfully) booting into the installer, it says it can't mount the CD-ROM drive, which is fine because it is broken, but how can I use the actual partition it's currently on instead of the CD-ROM? The partition has all the files that is found on the installation ISO, plus those four files I copied to root. I tried typing in "/dev/hda5" (5 is the partition number) but that didn't work.

Thanks for the help.

---

### Post by bazookaaa on 2008-11-06
I don't like bumping. :(

---

### Post by pxwpxw on 2008-11-06
Have you used the hd-media images?

[http://ports.ubuntu.com/dists/intrepid/main/installer-powerpc/current/images/powerpc/hd-media/](http://ports.ubuntu.com/dists/intrepid/main/installer-powerpc/current/images/powerpc/hd-media/)

---

### Post by bazookaaa on 2008-11-06
> **pxwpxw said:**
> Have you used the hd-media images?

[http://ports.ubuntu.com/dists/intrepid/main/installer-powerpc/current/images/powerpc/hd-media/](http://ports.ubuntu.com/dists/intrepid/main/installer-powerpc/current/images/powerpc/hd-media/)

Thank you so much, that does the trick! New problem though, when I reach the partitioner, I only get presented with three options ("Help with partitioning", "Undo changes", "Finish partitioning and install" [text not exact]). When I select "Undo", nothing happens and it just becomes a blue screen, and when I select "Finish", it says I didn't choose a mount point ("/"). There's no way to specify a partition.

Thanks for the help.

---

### Post by pxwpxw on 2008-11-06
I know what you mean. 

I had that problem with the partitioner (missing choices, nowhere to go) with the server install from an iso using hd-media, but on a mactel macbook i386. I could not make it work with the hd-media install, and had to burn the same server iso to a cd, which was ok (but not much help to you). However, on another pc (i386) i got the same bug, but by backing off right out of the partitioner and re-entering, several times, eventually got the usual guided, manual etc and got thru.

Now I have not used the hd-media/iso server install on a g4 or g5 yet, so dont know if its the same issue.

But I have done a network install on the g5, using the mini-iso cd from the netboot images, which had no problem with the partitioner. I was about to try an alternate cd install, but the downloads are too slow just now to get it.

So maybe there is some bug with the hd-media  installer for g4, and there certainly is for mactel, but that is i386. It is hard for me to see any connection between powerpc and i386 installers.

So for now, I can only suggest have a few more goes at the hd-media install with backing out of the partitioner and re starting that step of the installer, or try the network install images, which were ok for me.

I really dont know whats going wrong there until I try it again on my ibookg4.

Just checked now,
The netboot images partitioner checked out good on my ibookg4, just a bit slow,
depending on time of day.

[http://ports.ubuntu.com/dists/intrepid/main/installer-powerpc/current/images/powerpc/netboot/](http://ports.ubuntu.com/dists/intrepid/main/installer-powerpc/current/images/powerpc/netboot/)

edit:
forgot to mention I use the cli-expert option from the yaboot menu (for a server install) to get more control.

---

### Post by bazookaaa on 2008-11-07
Thanks for the info about the netboot installer. That didn't work since I don't have access to an ethernet cable (can just use AirPort). And on the hd-media installer, I kept backing out of the partitioner and going back in for a really long time! That didn't help though. Oh well, I'm just going to give up. Thanks again for the help.

---

### Post by pxwpxw on 2008-11-07
The hardy 804 images were ok for me, I think the partitioner problem is just with the intrepid version.

---

### Post by stream303 on 2008-11-09
I noticed the new partitioner kink in Intrepid when I was first installing over some old partitions - my old "go back" technique is now gone, since the partitioner won't let you delete existing ones without defining a root partition before leaving the setup.

I think perhaps Intrepid is being too smart putting an end to some of our tricks. :)

In the end I cheated by using OSX disk-utility to wipe out the old partitions to just leave some free space for this dual-boot scenario.  Guess I could have used a live-cd and gparted too...

---

### Post by pxwpxw on 2008-11-09
Well the problem here with the hd-media/iso install, was that the partitoner menu did not have any choices at all, and would not go forward either, the only way out was to go back.

---

