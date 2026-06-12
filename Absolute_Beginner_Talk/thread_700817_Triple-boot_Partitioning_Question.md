---
title: "Triple-boot Partitioning Question"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by drworm01 on 2008-02-18
I'm about to get a new computer and I want to have three versions of Linux on it: k/ubuntu, Ubuntu Studio and SlackWare. I say "k/" because I'm going to try Kubuntu and if it's not to my taste, replace it with Ubuntu.

The K/Ubuntu will be my primary OS, Studio will be for indulging occasional media muckery and the Slack to learn Slack. My question is can I get away with just 5 partitions: 1 for each OS (3 total), 1 swap and 1 where all my files and work will be? How large should I make each OS partition (1 GB for swap, remainder for rest) and will this set-up work without any extra jiggery-pokery? In other words, will each OS recognize and use the same swap and free space or do I have to configure each with "this is your swap," "this is your free space"?

I've been using Ubuntu for a while. My question is about how to make it work this way.

Thanks for your time,
D-

---

### Post by randy78 on 2008-02-18
> **drworm01 said:**
> I'm about to get a new computer and I want to have three versions of Linux on it: k/ubuntu, Ubuntu Studio and SlackWare. I say "k/" because I'm going to try Kubuntu and if it's not to my taste, replace it with Ubuntu.

The K/Ubuntu will be my primary OS, Studio will be for indulging occasional media muckery and the Slack to learn Slack. My question is can I get away with just 5 partitions: 1 for each OS (3 total), 1 swap and 1 where all my files and work will be? How large should I make each OS partition (1 GB for swap, remainder for rest) and will this set-up work without any extra jiggery-pokery? In other words, will each OS recognize and use the same swap and free space or do I have to configure each with "this is your swap," "this is your free space"?

I've been using Ubuntu for a while. My question is about how to make it work this way.

Thanks for your time,
D-

Well, just download and burn a copy of Gparted and do it!

I would personally set up the OS partitions to at least 10gb each...
Depending on how much memory you'll have, you might not even need a Swap file, but just in case, 2gb is a good size.

Just make sure to set the partition where the GRUB will be located to Boot.

Basically, make all the OS partitions and the shared partition EXT3, then format Swap as Linux-Swap...

Hope that answers your question ;)

EDIT:
If you're just fooling around with different Operating Systems, you can also just install one OS and then install VirtualBox up to run some virtual machines.

---

### Post by geo909 on 2008-02-18
I think that since every distro installs GRUB, the other distros already installed will be added to it automatically. No messing around with grub installations etc..

But I haven't seen it in practice so I can't say for sure

---

### Post by e_james on 2008-02-18
Based partly on my own experience and partly on other forum threads, I believe that some distros do not install grub automatically for multiboot. Ubuntu (presumably Kubuntu) does, but it can get confused about its own settings. You may need several attempts to get it right. I believe it is not necessary to completely reinstall a distro in order to fix grub. It is probably a good idea to have a Super Grub CD handy.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by randy78 on 2008-02-18
> **e_james said:**
> Based partly on my own experience and partly on other forum threads, I believe that some distros do not install grub automatically for multiboot. Ubuntu (presumably Kubuntu) does, but it can get confused about its own settings. You may need several attempts to get it right. I believe it is not necessary to completely reinstall a distro in order to fix grub. It is probably a good idea to have a Super Grub CD handy.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

SuperGrub +1!

---

### Post by Moop on 2008-02-18
One swap partition will work for all the os's.

 I don't think you should have any problem with grub if you install K/Ubuntu last. The OS you install last will normally control grub. :popcorn:

---

### Post by e_james on 2008-02-18
randy78

Sorry. I don't understand your comment.

---

### Post by Forrest Gumpp on 2008-02-18
randy's comment is forum shorthand for "I second that" in reference to whatever post he indicated.

---

### Post by e_james on 2008-02-18
Forrest Gumpp

Thanks for the explanation. I considered that possibility but I wasn't sure.

---

### Post by randy78 on 2008-02-18
Yeah, I noticed myself that it kinda looks like I was referring to some type of different version!

No worries... +1 = :guitar:

---

### Post by drworm01 on 2008-02-19
Thank you everyone. It's good to know. I'll get my GPartEd LiveCD ready, have SuperGRUB ready, split the drive into 10/10/10/2/218, install primary OS last and then it'll be monkey chow and margaritas all day long.

Thanks again.

D-

---

