---
title: "Repair Restore Grub... yes! it works"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by angler on 2006-11-03
I was finally able to repair my MBR and get grub going after searching and searching and loading up the live-cd twelve dozen times. I'm really glad too, cause I just started to get everything how I like it. Special thanks go to Arsgeek for this one!!!!

Arsgeek didn't mention doing this, but to get this to work I first mounted my first few partitions into /mnt like this. You'll notice I use a small boot partition btw.
...........................
sudo su- 

mkdir /mnt/boot
mkdir /mnt/ubuntu
mkdir /mnt/store

mount /dev/sda1 /mnt/boot
mount /dev/sda2 /mnt/ubuntu
mount /dev/sda6 /mnt/store
............................
Of course that may be different for you, but this wouldn't work for me without having those mounted.

Now for the Arsgeek commands - found at [http://www.arsgeek.com/?p=655](http://www.arsgeek.com/?p=655) - Thanks !!
............................
sudo su-

grub

find /boot/grub/stage1
............................
You're output should look something like this.. (hd0,1)
Using that output =>
............................
root (hd0,1)
setup hd0
............................
Output should say you were succesful!!
You can quit grub and reboot.
............................
quit
shutdown -h now
............................

I hope this can help somebody as much as it did me. All the other "how to" posts were getting me nowhere. Thanks again arsgeek!

---

### Post by %hMa@?b&lt;C on 2006-11-03
just fyi, the mepis live cd has an auto GRUB repair tool. for future circumstances, I suggest using that.

---

### Post by angler on 2006-11-03
> **jeffc313 said:**
> just fyi, the mepis live cd has an auto GRUB repair tool. for future circumstances, I suggest using that.

That's good to hear. I think that should be included, among other things, on all the new live-cd's.

---

