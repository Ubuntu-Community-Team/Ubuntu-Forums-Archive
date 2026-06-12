---
title: "&quot;GRUB GRUB GRUB...&quot; fills the screen when trying to boot Karmic"
date: 2009-11-14
forum: Apple Hardware Users
---

### Post by EchohcE on 2009-11-14
This has probably been answered already, and if this is the case, I apologize for the redundancy of the thread, but I can't find any threads that list this problem.

First, I am using a late 2008 Unibody 15" Macbook Pro (unsure whether it's 5,1 or 5,2) with Leopard and rEFIt.  When I had Jaunty, everything worked fine, got all the tweaks worked out with the touchpad and all that jazz(thank you MacTel), rEFIt worked perfectly, then I heard about the new Grub2 and how it was recommended to use a clean install of Karmic instead of upgrading via the Update Manager in Jaunty.

So I downloaded the 64-bit version of Karmic, burned it to a cd using the Disk Utility in Leopard, and used the LiveCD to go to the new partition thing(not gparted) to delete first the swap partition and then the entire Ubuntu install so that I was left with only Leopard, the 200mb rEFIt part, and free space.  I have a 320g hard drive, 300 of which is recognized due to the HDD manufacturers' weird way of measuring HDD size, so now I have the partitions as follows:

200mb EFI partition
100gb Leopard partition
200gb Free Space

I chose to install Karmic within the LiveCD(via the icon on the desktop), chose to use Largest Continuous Free Space.  I also chose the "use password to unlock home folder" option(not sure if it has anything to do with it, but listing everything I did).  I cannot remember whether I first chose in the Advanced to put the Boot loader on hd0 or sda3, but a fresh install with choosing sda3 leads to the GRUB filling the screen. 

I waited for it to install, after which I learned that rEFIt won't synch the partition tables, and that Karmic is recognized by rEFIt as a Legacy OS. I clicked on the Legacy OS, and GRUB filled the screen.  I tried to go back to Jaunty, but now Jaunty won't work either.  It does the exact same thing.  It should be noted that I used 32-bit Jaunty and 64-bit Karmic.

I have no clue what is making it do this.  Can anyone help me so I can get back to using my beloved Ubuntu?

---

### Post by tom4everitt on 2009-11-15
When you reach the rEFIt menu directly after booting, try to choose partitioning tool. This will hopefully ask you to let it sync partition tables. Let it.

After that everything should work.

Note that the issue has nothing to do with karmin or jaunty, but with that your partition tables got out of sync when you installed karmic the first time. Simply syncing partition tables generally solves this (sometimes you have to restore grub as well, but this shouldn't be necessary after a fresh install).

---

### Post by EchohcE on 2009-12-05
I think I found the problem.  Apparently I had loaded Grub2(which refit won't recognize anyway) to either the ext4 or the swap partition(both are 8gb on my setup).  I'm trying to delete the partitions now, but it's refusing to let me delete the swap.  I've gone in via both the osx and ubuntu install discs, but it simply will not delete.  Will I have to completely reinstall Leopard?

---

### Post by tom4everitt on 2009-12-05
First of all, rEFIt is able to boot grub 2. I actually have it doing that on my computer right now, and it works perfectly. So what I really think you should do first is syncing partion tables as I said above. This is a really common problem for mac users installing linux, since linux and mac are you using different partition tables, and these will always get out of sync when doing any kind of partitioning. As a result, almost no boot loader will work at all. 

And syncing them is as easy as pushing a button in refit, which you can boot from a cd...

I see no reason at all why removing grub/grub2 would help at all. That said, if you still want to remove your swap partition, try


sudo swapoff -a


in ubuntu before you try to delete it in gparted or fdisk.

---

