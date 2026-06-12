---
title: "Kernel panic on encrypted system!"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by blastus on 2008-02-29
I installed Ubuntu on an encrypted volume group containing root (/) and swap. I am trying to get the rt73 serialmonkey drivers setup but now my machine freezes and won't boot anymore. Attempting to recover reveals that the rt73 driver caused a kernel panic and doesn't boot.

I need to edit my /etc/network/interfaces file but I can't because the partition is encrypted! Is there a quick way to mount a dm-crypt partition that contains an LVM with the Live CD?

---

### Post by blastus on 2008-03-01
I found a way to do it...

sudo aptitude install cryptsetup lvm2
sudo modprobe dm-mod
sudo cryptsetup luksOpen /dev/sda3 crypto
sudo mkdir ~/mnt
sudo mount /dev/mapper/lvm1-root ~/mnt

It looks like opening the encrypted partition automatically created the device mapper files for all the logical volumes in it. I also came across this guide which was very helpful [HOWTO: Rescue an encrypted LUKS LVM volume](http://ubuntuforums.org/showthread.php?t=611165)

---

