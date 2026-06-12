---
title: "Ubuntu Installed, But Won't Launch"
date: 2011-05-20
forum: Apple Hardware Users
---

### Post by DoocesWild on 2011-05-20
I'm having some issues that I need help with.  I am trying to triple boot my macbook pro.  These are the steps I have taken: 1) ran the boot camp wizard on my existing install of osx Snow Leopard. Partitioned 125GB off for Windows.  Installed a brand new copy of Windows 7 Home Premium. Loaded up the Snow Leopard CD and got all of the drivers working, runs smoothly.  Back in OSX, installed REFit.  Dual boot works smoothly.  Inserted LiveCD (11.04 64 bit) of Ubuntu (Burned from OSX) and restarted.  Got a blinking curser that hung forever.  Restarted again, and ticked the option for "nomodeset" and got through the launch of LiveCD fine.  Opened up the install wizard, partitioned off 25 of my 125 in the "Bootcamp" partition, and it installed fine.  Restarted, went to the REFit partitioning tool, the tables are synchronized, no need to rebuild. Try to launch "Linux from HD" and it turns off my computer.  Also, REFit is very slow to launch.

I need suggestions for 1) fixing it or 2) removing Ubuntu partitions completely and returning to dual boot.  Also, I don't know if this is normal, but now when I choose to launch Windows under REFit, GNU GRUB launches, and I have to choose it again.

---

### Post by jamesjenner on 2011-05-20
G'day Mate,

I went through this process just this week gone and while I didn't install Windows, I did have the same problem that your experiencing with installing Ubuntu. The only other difference i can see is the version I installed (I installed 11.04 64-bit). Of course the model is different, I have a MacBook 5,1.

The problem I had manifested itself by giving two options only via REFit, one for Apple (with a pretty logo) and one for Legacy Operating System (the logo was a black and white stylised psudeo windows logo background, ie a window turned on it's side). If I selected the Legacy Operating System I got a single text line that said operating system not found (I may have the exact phrasing incorrect, I'm going on memory). 

The problem was caused because I didn't use GParted from the Live CD to setup the partitions for linux, I used the partition tool in the install process. I redid it following the sticky guide exactly as stated and everything then worked okay. 

I'm not sure if you did or didn't use gParted, but I suspect that may be the cause of your problem.

Cheers,

James.

---

### Post by DoocesWild on 2011-05-20
I didn't follow any guides.  I just figured it would be self explanatory.  I'll look for the sticky guide and follow said steps.  Thanks for the quick reply James

---

### Post by jamesjenner on 2011-05-20
> **DoocesWild said:**
> I didn't follow any guides.  I just figured it would be self explanatory.  I'll look for the sticky guide and follow said steps.  Thanks for the quick reply James

No worries mate.  :)

Since you didn't follow the guide I can guarantee then it will be because of the gParted issue. To be honest it was the only tricky bit in the whole thing, oh and installing grub onto the partition that Linux is going on as well. But other than that it's fairly obvious. 

Good luck!

---

