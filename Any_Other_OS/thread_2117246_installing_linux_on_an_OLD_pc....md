---
title: "installing linux on an OLD pc..."
date: 2013-02-17
forum: Any Other OS
---

### Post by aderwent on 2013-02-17
ok, so i have a dell inspiron 4300 that is more than a decade old. it has windows xp sp3 on it. i downloaded a recent version of macpup because it's light-duty. even after updating my bios to the most recent version (2003 lol) it couldn't boot from usb, and i don't have a cd burner. so i found a floppy disk from the doldrums and after disk checking it 3-5 times, i was able to successfully install plop boot on it which allowed me to boot from the usb drive.

so here i am, with macpup running. i want to completely uninstall windows, and have just macpup on my hard drive. i'm sitting here in gparted with two partitions - /dev/sda2 18.64 GiB, 11.24 used. and an unallocated partition at 1.94 MiB. 

so what do i do from here? if i format /dev/sda2 to ext4, will my computer be able to boot? remember, i don't care about windows or any of its files. i want a fresh install of macpup and macpup only. if that format does get rid of my bootability i'm screwed right? and to prevent that, how do i partition for just the bios boot? or am i an idiot and it boots from ram or a "hidden" partition some place?

thanks for any help. i have experience with ubuntu but i'm installing macpup for the first time on this dinosaur.

---

### Post by Bucky Ball on 2013-02-18
Welcome to the forums.

I'd reinstall Macpup, when you get to the partitioning section of the install do it manually (in Ubuntu you choose 'Something Else'), kill the Win partition, or all partitions, and create what you need and away you go.

I have never heard of nor have any experience of Macpup so not sure what it's capable of, but manual partition should be a given. 

Your other option is, if it runs from a LiveUSB boot (gets you to a desktop) then you could boot Gparted, unmount the Win partitions if they aren't already, kill them, expand the Macpup partition and reinstall grub. This can also be done using a *buntu LiveUSB.

Out of curiousity, how much RAM do you have?

---

### Post by aderwent on 2013-02-18
i'm stupid. macpup has its own "universal installer". all i have to do is choose that sda2 partition to install on. i hope anyway :p. i have no idea how much ram i have. its maximum is 512mb :o.

---

### Post by aderwent on 2013-02-18
also, initially macpup copied itself to the ram to boot. is that a temporary thing, especially if i install it to the hard drive?

---

### Post by Bucky Ball on 2013-02-18
*Thread moved to **Other OS/Distro Talk**.*

Read here. It tells all:

[http://macpup.org/](http://macpup.org/)

As I suspected it is a derivative of Puppy Linux and as such runs from RAM. Doesn't install to the hard drive. Don't know if you can do that. You'll need to research it, learn a bit more about what you're dealing with and get familiar.

---

### Post by mips on 2013-02-18
> **Bucky Ball said:**
> Doesn't install to the hard drive. Don't know if you can do that. You'll need to research it, learn a bit more about what you're dealing with and get familiar.

[http://macpup.org/forums/index.php/topic,7.msg13.html#msg13](http://macpup.org/forums/index.php/topic,7.msg13.html#msg13)

Tried it before and it was a convoluted process :D

---

