---
title: "Unetbootin will not appear in Grub"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by sans on 2008-03-30
Hello all

I installed Linux for the very first time using Unetbootin for Windows. Having read up a little more about partitions and the like I'd like to reinstall Ubuntu. 
Given the previous success I'd figured I'd use Unetbootin again,

To move on; when I specify my distro and am prompted for "Reboot", nothing happens. When rebootin manually the Unetbootin option does not show up in grub.

I'm kinda at my end here. I tried installing from USB but I can't load up bios, and trying Lilo I can't seem to install that as it keeps complaining about my disk setup?

I really just want to repartition my drives and have ubuntu present so I can carry on with work -- windows free :)

Thanks for any (noob-friendly) pointers!

---

### Post by Daveth on 2008-03-30
never used it but this might help if you have not seen it

[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by sans on 2008-03-30
Thanks Daveth. I used it as a reference the first time. Unfortunately it doesn't mention anything about my specific problem.

---

### Post by Daveth on 2008-03-30
damn! So you are keeping your windows OS then? Is this XP or vista? What happened to the first ubuntu install? Did you wipe it, or is it still there? It sounds as if the hard drive is becoming a bit of a dog's dinner, and is as confused as I am!

---

### Post by sans on 2008-03-30
Sorry Daveth - rereading that first post, I realize I didn't make myself perfectly clear. Let me outline what I did so far;

The setup is an ASUS T2 with two physical drives.

1. The machine had Windows XP present. I downloaded, installed and ran unetbootin (for windows.)
2. During the unetbootin install there was a little unclarity about partitions. I ended up going with the 'guided partitioning' option (basically letting unetbootin do its own thing.)
3. Unetbootin succesfully installs ubuntu 7.10. There is NO (dos/ntfs) windows partition left.

I start reading up and come to realize the partitions it (or I, depending which way you look at it) aren't that great and decide I want to reinstall.

Which leads me to what I've tried out already:

- I burned two cd's (one using macbookpro and one using the ubuntu box and checking the CD's returns errors so they're of no use either.)

- I then opted for Unetbootin again, which I get running and which sets itself up for reinstall upon reboot. Hitting the final OK prompts a reboot, which does nothing. Manually rebooting shows no Unetbootin option in grub. I guess it doesn't work.

- I'm now trying to install Ubuntu from USB (I did manage to edit BIOS-Boot so it'll find my USB drive) - unfortunately, I can't get my USB stick to work along. I understand I can use lilo for this purpose but I can't make it past the install screen (it keeps complaining about odd filesystems)

So yeah basically one problem: I want to repartition and reinstall Ubuntu and absolutely no means of getting it done :)

---

### Post by Daveth on 2008-04-02
so I was right, a bit of a dog's dinner then. I think I would try a new ubuntu live cd burn, give up on unetbootin, and use gparted to start your partitions from scratch. Remember you cannot partition a mounted partition, so you go from the live cd. Lots of help available here, just ask:)

---

### Post by sans on 2008-04-04
Thanks Daveth, as it happens my LiveCD arrived in the mail today so I hope I'll get it done!

---

