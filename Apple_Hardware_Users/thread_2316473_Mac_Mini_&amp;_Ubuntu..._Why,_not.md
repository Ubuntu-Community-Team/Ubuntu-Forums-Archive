---
title: "Mac Mini &amp; Ubuntu...? Why, not?"
date: 2016-03-08
forum: Apple Hardware Users
---

### Post by yogich246 on 2016-03-08
Posting this, in hopes that someone might be, helped.

I got a i5 Intel Mac Mini, about 3 years, ago, and it ended up with Yosemite, on it, which didn't work as well as what came, on it. Consequently, I determined that I was going to install Ubuntu, on it, come hell or high water. As an aside: I have been using Linux, off & on --in particular, Ubuntu, of late-- for a very long, time. However, it was always on Windows-based PC. I usually blew Windows away, before doing, so, but, still...never played with a Mac, before.

I read multiple threads, on this topic, and googled it, frantically, and I finally got Ubuntu installed along side, Yosemite, to determine that it worked, according to expectations. It, did! Fact is, it exceeded any of my expectations. I then attempted to use a bigger hammer to get Ubuntu on the whole, drive. Google pointed me to 'refind,' which promised to deal with my UEFI issues, so I installed it within the Windows --> Linux partition (windows was deleted, during installation). Sadly, I kept getting an error, on configuration, that DPKG was in use. Nothing I did changed, that, & I did not want to horse around trying to get an answer to a question. So, I got an even bigger hammer and commenced to do it, 'My Way'! :-\"

I booted the Ubuntu Live DVD, and when it came to partitioning, I chose the option which wipes everything --which, in turn, took me to another screen where I could fine tune, so I did. I also chose /dev/sda for bootloader, and upon completion of the installation, held my breath, a bit, as I rebooted. The result was, awesome.

If Mac doesn't detect any OS, on the main partition, it searches for anything at all, which is bootable. Usually, that amounts to the Recovery partition (been there, a couple times), but in this case, it was Ubuntu! The search took, maybe, four or five seconds, but Ubuntu was, indeed, found. No, 'blessing' the boot partition, no hoops, nothing. Just wipe the drive, install, enjoy. 

Now...I'm not saying that everyone will find it this simple, but I can assure you that this document is being written on my Mac Mini, within FIrefox, on Ubuntu with the XFCE Desktop.

 Any observations are welcome. I would be most interested in others', experiences.

---

### Post by howefield on 2016-03-08
Thread moved to the "*Apple Hardware Users*" forum.

---

