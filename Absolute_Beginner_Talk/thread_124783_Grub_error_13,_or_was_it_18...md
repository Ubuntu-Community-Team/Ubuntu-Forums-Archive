---
title: "Grub error 13, or was it 18.."
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by radoncdude on 2006-02-02
Hi,

I downloaded the .iso file and burned it,
booted up the ubuntu disk and proceeded with the installation..
it did everything required in the setup, except..

when I was supposed to boot up in Ubuntu,

it never got past the 2nd line in the command prompt

first it says:

wait for GRUB to load

then:

error 13

My computer specs are:

Amd Duron 750
512 Megs ram
160 GB hard drive (Maxtor)

I am thinking maybe its the hard drive's boot record that causes the conflict?

Thanks for the help

---

### Post by milstead on 2006-02-02
First off getting this wrong may make data on your hard disk unreadable so do this at your own risk.

You make no mention of sharing with Windows. If you are you should be extra careful.

I think this is one of two things.

1. Your partition table is corrupt and needs fixing. I had this once on a Fedora Core installation. I managed to fix it and get my windows partitions back. I can't remember exactly how it was done but it involved boot a linux rescue CD and using fdisk to work out what the correct partition table should be and then using it to write the correction back to the partition table. Simple(ish) but scary. You'll have to google for how to do it.

2. Grub did not install properly. I would go with this one.
a. Boot from a linux rescue CD.
b. Mount the hard disk's ubuntu root partition.
c. chroot to the mounted root directory.
c. run grub-install <device> e.g. grub-install /dev/hda

d. exit the chroot
e. unmount the mounted root directory.
f. Restart, eject rescue CD and hopefully ubuntu will load.

Tim.

---

### Post by Iowan on 2006-02-02
It won't help help solve the problem, but [HERE]("http://www.uruk.org/orig-grub/errors.html#stage2") is a list of what the error messages mean.

---

### Post by radoncdude on 2006-02-02
Can I just pop the installation CD back in, reformat the disk and try again?

Or will that give me the same error?

---

