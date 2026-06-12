---
title: "Restore &quot;with grub&quot;"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-06-02
I do not know what I want to do has a name.

What I would like to do is add a entry in grub "Restore System". That when it is selected will restore a partition.

In others words, I want to setup a machine, then make a image of the partition, then make that image copy back over when "Restore System" is selected from grub.

Anyone know on how I might achieve this?

Thanks

---

### Post by jakev383 on 2007-06-02
Probably one of the first things you're going to want to look at is the System Rescue CD. It allows easy imaging of partitions. Then you have something to start with. After that, it depends on how you want to restore it.
First thing that pops in my head is an EXTREMELY small distro (Puppy, or DSL, or even something else like the FloppyFirewall with the needed utilities added) to use as a base when booting to the restore partition. Then just script it to restore whatever image is there to your main partition.
Sounds easy enough.... But we all know those are famous last words.

---

### Post by guysmiley25 on 2007-06-02
Yes I was thinking along those lines as well.

I was hoping that maybe someone has done it and could share with me what they did.

Or that someone out there has come up with a really nice way to do it.

Thanks

---

### Post by confused57 on 2007-06-02
I don't have any experience with what you're wanting to do, but maybe this will help:
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)

---

