---
title: "Second hard drive install"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by ozarkman on 2007-07-27
Sorry if this has been asked before but I have searched and found nothing. I want to install Ubuntu on a second computer that has two hard drives in it and can only install on one of them. It was suggested to me by a friend to try fedora core 6 and it installed using both drives automatically. But I really don't care much for fedora and want to put Ubuntu back on the box.

---

### Post by Jeek Elemental on 2007-07-27
Shouldnt be a problem? ubuntu lets you choose which drive to install on and whether to wipe it or just elbow in.
Drives other than the one you install on will not be touched, as far as I know.

note that if you have changed boot order in bios, the default grub root entry may be wrong, it is easily fixed by using grubs edit tho.

---

### Post by pistcivet on 2007-07-28
By install on both drives do you mean mount one as / and the other as /home ? (for example)
If thats what you want then I don't think the live cd will do it.
But I believe that the alternate install cd allows it.

I've done this before, but haven't tried it yet with Ubuntu.

Or maybe you're thinking of LVM.
In which case, yes Ubuntu can do that.

---

### Post by ozarkman on 2007-07-28
What I would really like to do is use both drives. when I install from the livecd it shows both in the partition options but I can only choose one of the two 40 gig drives with the fedora install I get 80 gigs of hard drive and with ubuntu I cant seen to get more than 40 gig.

the second drive is visible after install also and can be seen using gparted. I just cant figure how to mount it I guess is the problem. sorry I know just enough to get myself in trouble LOL

---

### Post by ozarkman on 2007-07-28
From what I can tell this is a mounting problem. Am I on the right track?

---

### Post by Jeek Elemental on 2007-07-28
sorry I seem to have misunderstood :-\"

if you open places/computer on the menu bar, does the other drive show there? you should be able to mount it if so by double clicking it (if it has a recognized file system).

one of the install options lets you split off /home from root but Im not sure if it only works for separate partitions on the same drive.

---

### Post by ozarkman on 2007-07-28
I didn't have permission to use it. I used info found on this page to fix it
[http://ubuntuforums.org/showthread.php?t=463428&highlight=access+second+harddrive](http://ubuntuforums.org/showthread.php?t=463428&highlight=access+second+harddrive)
don't know how I missed this on my first search of the ubuntu forums. thanks for trying to help Jeek and pistcivet.

---

