---
title: "&quot;GRUB GRUB GRUB...&quot; fills the screen when trying to boot Karmic"
date: 2009-11-14
forum: Apple Hardware Users
---

### Post by EchohcE on 2009-11-14
This has probably been answered already, and if this is the case, I apologize for the redundancy of the thread, but I can't find any threads that list this problem.

First, I am using a late 2008 Unibody 15" Macbook Pro (unsure whether it's 5,1 or 5,2) with Leopard and rEFIt.  When I had Jaunty, everything worked fine, got all the tweaks worked out with the touchpad and all that jazz(thank you MacTel), rEFIt worked perfectly, then I heard about the new Grub2 and how it was recommended to use a clean install of Karmic instead of upgrading via the Update Manager in Jaunty.

So I downloaded the 64-bit version of Karmic, burned it to a cd using the Disk Utility in Leopard, and used the LiveCD to go to the new partition thing(not gparted) to delete first the swap partition and then the entire Ubuntu install so that I was left with only Leopard, the 200mb rEFIt part, and free space.  I have a 320g hdd, 300 of which is recognized due to the hdd manufacturers' weird way of measuring hdd size, so now I have the partitions as follows:

200mb EFI partition
100gb Leopard partition
200gb Free Space

I chose to install Karmic within the LiveCD(via the icon on the desktop), chose to use Largest Continuous Free Space.  I also chose the "use password to unlock home folder" option(not sure if it has anything to do with it, but listing everything I did).  I cannot remember whether I first chose in the Advanced to put the Boot loader on hd0 or sda3, but a fresh install with choosing sda3 leads to the GRUB filling the screen. 

I waited for it to install, after which I learned that rEFIt won't synch the partition tables, and that Karmic is recognized by rEFIt as a Legacy OS. I clicked on the Legacy OS, and GRUB filled the screen.  I tried to go back to Jaunty, but now Jaunty won't work either.  It does the exact same thing.  It should be noted that I used 32-bit Jaunty and 64-bit Karmic.

I have no clue what is making it do this.  Can anyone help me so I can get back to using my beloved Ubuntu?

---

### Post by jamesey on 2009-12-11
I get that too. There is something obvious that all the expert users do that the novices users don't see during the install process.

---

### Post by linuxopjemac on 2009-12-12
I made a page of stuff what people came up with with this kind of boot problems. Read it and try it out. If you have anything to add, feel free to contact me or post your comments.

[http://mac.linux.be/content/gptsync-gpt-partition-type-unknown-found-will-not-touch-disk](http://mac.linux.be/content/gptsync-gpt-partition-type-unknown-found-will-not-touch-disk)

---

