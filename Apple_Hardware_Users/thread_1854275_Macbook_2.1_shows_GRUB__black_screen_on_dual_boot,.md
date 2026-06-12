---
title: "Macbook 2.1 shows GRUB_ black screen on dual boot, please?"
date: 2011-10-04
forum: Apple Hardware Users
---

### Post by liviococcia on 2011-10-04
Hello Members
I have Zorin Core 5 (Ubuntu) installed on an external 100gig Solidstate hardrive, and i use Plop bootloader to boot it up using my Macbook 2.1, it works really great so i thought i'd give it a go installing it to the Macbook as a duel boot system, below is what i did (following the Ubuntu instructions)...

1:I partitioned OSX 160gig HD into an 80gig for OSX, and 80gig for Zorin, i did this using 'Boot Camp' and only created the partition as if i was installing Windows.

2: While still in OSX i installed 'reFIT' dual loader for Mac's.

3: Then booted up the Macbook using the Zorin Ultimate DVD, and picked the 'installation' from the menu, when i got the point of choosing where to install i chose 'Custom' , then created an 75gig Ext4 (/ root )partition, picking 'Format' and 'Beginning of the drive', and a 'Swap' of 5gig.

4 I then chose for the 'boot-loader' (Grub) to install to the same Ext4 partition i had created, and everything installed great.

The problem is when i chose to boot from the 'Linux on HD' in 'reFIT' os picker, all that happens is that a black screen appears with the word GRUB_ (and a flashing cursor), i did try the 'resyncing' hard drive partitions facility in 'reFIT' but it didn't do anything, and even reported the partitions were correctly synced.

Has and member experience this GRUB problem, and knows what's wrong?

(just a note: it was easy enough to reverse everything i had done above, with no issues arising but it would be nice, to now have both Zorin and OS-X on the Macbook if it's possible)

kind regards
Livio

---

