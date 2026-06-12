---
title: "Install getting stuck"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by TBridges on 2007-06-11
Hello, as you can probably tell, I am new to this forum, I have been browsing for a few hours to a) try and fix my problem and b) get a feel for the ubuntu experience!

So I downloaded the Ubuntu 6.10 cd image and burned it. I then put the cd into the pc I wanted to install it on and booted, it takes me straight to the desktop and I click install. I then follow this guide: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
I went for the more advanced setup with partitioning the hdd. I setup one partition for the '/' drive at 10Gb, and there is a logical drive already labelled as linux-swap or something and then create the final partition for all the other files. Click forward and assign the swap mount to the partition that was labelled linux-swap, assign the '/' mount to the 10Gb partition and the /home mount to the other partition which from memory is ~145Gb. 
I click forward once more and it takes me to the confirmation window, which I must admit I havent checked through once, apart from the bit where it says GRUB will be installed to, then there is a button with (hd0) on it. I have checked what that means, but I'm still not 100% on it. Plus my hdd was referred to as 'sd' during partitioning, but I assumed that was because its a sata drive.
I click forward again and it begins to format/install etc, it gets through one partition, then goes onto the large partition, gets to 15% and sits there with all the fans roaring away, but its stays this way until eventually it sounds like the mobo starts beeping at me, but still sticks at 15%. 

As you can probably tell I'm totally stuck! And any help would be very greatly appreciated.

Many Thanks,
Tom

---

### Post by Seisen on 2007-06-11
You might want to try a text-based install and see if that works.

---

### Post by bobplano on 2007-06-11
did you check the cd for errors? to answer some of your questions/confusions, grub is a program that lets you choose which operating system to boot into. installing to hd0 just means thatthe computer boots to grub first, then you choose ubuntu or whatever and it boots to that. the sd in your partitions does mean that your using a sata hard drive. even though grub says hd0 and your hard drive is sata it should still work

---

### Post by _simon_ on 2007-06-11
Could be a bad burn or bad cd. I had the same problem when installing Ubuntu for someone else, turned out the CD was dodgy.

---

### Post by lazyart on 2007-06-11
How much memory in this machine?  >256 megs I hope....

---

### Post by TBridges on 2007-06-11
Yeah its got 512 at least.

---

