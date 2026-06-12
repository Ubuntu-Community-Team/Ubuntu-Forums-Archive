---
title: "Problem installing with manually edited partitions"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by coldstatue on 2006-12-16
Note - I have re-read the partitioning guides, and searched the forums. It sounds like I did everything right, so I really need some issue-specific assistance.

I am installing Ubuntu 6.10 - what I hope is my first Ubuntu install. (though not my fist attempt) I got a second hard drive, and edited the partitions just how I want them. I am using Boot Magic on another dirve, so there is no need to worry about GRUB. Please don't try to convert me, I've been down a very messy road with it. I'm using BM. Anyway, on my new, second hard drive, I have the following partitions.

2 GB for swap (linux swap file system), Logical
29 GB for Ubuntu (ext3 file system), Logical
29 GB for SUSE (ext3 file system), Logical
29 GB for Fedora (ext3 file system), Logical

46 GB for sharing with Windows (FAT32 file system), Logical.

So, this should be just fine for me to install a few distros, and get my feet wet.

However, when I go through the Ubuntu install, I run into problems when manually assigning what partitions will be mounted at what points.

I choose the 2GB swap for swap, and the 29 GB Ubuntu (ext3) partition for "/"

Whether or not I check the reformat boxes, I get the error, "No root file system."

What am I doing wrong? Please be as simple and specific as possible. I have a clear plan mapped out, and I devised it by talking to people in this forum, so I am really not looking for alternatives. I'd like to finish this as I have started it. If I have to create more partitions within my Ubuntu partition, no problem. But everyone said all I needed is a partition for swap and root... So what gives? What am I missing?

Thanks for any help. It's greatly appreciated... especially if translated into noob-speak.

---

### Post by speedman on 2006-12-16
Change the partition type to primary instead of logical.

SM

---

### Post by coldstatue on 2006-12-16
Will do... thanks. I'll let you know.

---

### Post by coldstatue on 2006-12-16
It didn't help... same problem. Fedora installed with no issues, so I'm not sure what's wrong here. I've attached a .gif of my partition table, since Partition Magic can give far more info than I can.

---

### Post by speedman on 2006-12-16
Partition Magic is brutal.  It has probably made a mess of your partitions.  I bet if you use a tool like cfdisk, or fdisk in Linux it will complain about partitions not ending on boundaries.  Other than starting over with a better partitioning tool I can't offer much help.

SM

---

### Post by coldstatue on 2006-12-16
If Ubuntu and Fedora recognize the partitions the same way, I guess I don't understand why I'm having all these problems. I cleared the partitions and started over... same problems. I went through a bout of installing Ubuntu on a dedicated hard drive, and letting it do it's own thing, and it couldn't manage a usable installation in that case either. Well, considering Fedora doesn't have a problem with it, I think I'll just use other distros for a while. I really wanted to try Ubuntu, because it's getting so much hype, but it's giving me far more problems than SUSE or Fedora, even just on live-spins. Fedora could use more space anyway.
Thanks for your help.

---

### Post by WaWeeT on 2006-12-17
I had the same problem...I just gone back to GParted and recreate a partition (delete partition and create partition raiserfs) and this fix my problem!
I hope that this will help you

---

### Post by coldstatue on 2006-12-18
Ok, thankyou. I'll look into it. I appreciate it.

---

### Post by WIVO_Riley on 2006-12-18
> **WaWeeT said:**
> I had the same problem...I just gone back to GParted and recreate a partition (delete partition and create partition raiserfs) and this fix my problem!
I hope that this will help you


ditto on this post.  I was having a BUNCH of trouble- I found somewhere that it may be necessary to delete the partition.  Changing from logical to primary may not do the trick.

Delete the partition, create the new partition as primary .....

I tried a ton of different things and none took until I did this. Then sucess.

Good luck

riley

---

### Post by coldstatue on 2006-12-18
Well, I used gparted, deleted the old partition and recreated. Success!. So now I know, I can use partition magic in windows for simple organizing, but just use gparted to recreate the partition during install. I was pretty weary of having GRUB in my MBR, but I got sick of spending so much time on it, so I installed it. I am now running Edgy Eft, and actually got my nvidia drivers to work at 1280x1024. Now for the wireless... ugh.. Still, it's looking good! thanks for the help!

---

