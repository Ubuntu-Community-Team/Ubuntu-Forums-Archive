---
title: "MacBook single boot 30s delay: I think I got it."
date: 2008-11-16
forum: Apple Hardware Users
---

### Post by regebro on 2008-11-16
I had a problem with MacBooks just hanging around and doing nothing for 20-30 seconds while booting, if you had made a single boot with Ubuntu. This issue seems to be only with Core2Duo MacBooks.

After much testing and reinstalling and fiddling, I found a solution: It seems that MacBooks (3,1 and later) prefer to boot from HFS+ partitions, and will hang around for 30 seconds hoping for you to insert one, if there isn't one. And only after that wait, will it boot from the volume that is marked as bootable. :mad:

Solution: A small HFS+ partition (20MB is probably enough, I made mine 50MB, but only 14 is used) where rEFIt, and only refit is installed, according to the instructions on how to install it on external partitions (must be done from OS X).

You get a silly 2-step boot process with first rEFIt and then Grub, but the machine boots 15 seconds faster (if you set the timeouts low).

---

### Post by volanin on 2008-11-16
I confirm this.
And although you need refit, you don't have to see it's face if you're
installing a single-boot ubuntu. Just set the timeout to zero. Your
macbook will boot to a nice penguin logo, and grub a little after.
:)

---

### Post by hyperboloid on 2008-11-17
Doesn't "blessing" the thing solve this?  See the following post

[http://ubuntuforums.org/showpost.php?p=5166788&postcount=21]("http://ubuntuforums.org/showpost.php?p=5166788&postcount=21")

from the FAQ list for details.

---

### Post by cyberdork33 on 2008-11-17
I don't think this is restricted to any certain type of Mac either.

---

### Post by regebro on 2008-11-18
> **hyperboloid said:**
> Doesn't "blessing" the thing solve this?  See the following post

[http://ubuntuforums.org/showpost.php?p=5166788&postcount=21]("http://ubuntuforums.org/showpost.php?p=5166788&postcount=21")

from the FAQ list for details.
I can't remember exactly what variations of bless I tried, although I tried all I could find. It is possible that this is one variation I did not try, I didn't write them up, sorry.

However, many of the variations I tried was reported (like this one) to work on 2,1 but was reported not to work with 3,1 and 4,1, and of course didn't work with mine. I know for sure I tried to bless the EFI partition after installing rEFIt to that one, and that did not work.

---

### Post by cyberdork33 on 2008-11-18
> **regebro said:**
> I know for sure I tried to bless the EFI partition after installing rEFIt to that one, and that did not work.
For rEFIt, you should be blessing the actual executable, not the partition... You can check the enable-always.sh script to see how the blessing is done.

---

### Post by regebro on 2008-11-18
> **cyberdork33 said:**
> For rEFIt, you should be blessing the actual executable, not the partition... You can check the enable-always.sh script to see how the blessing is done.

Yes, I'm pretty sure I did that correctly. It didn't work. It seemed to be because it was on a FAT32 partition and not an HFS+ partition. Installing it on an HFS+ partition solved it.

---

### Post by cyberdork33 on 2008-11-18
> **regebro said:**
> Yes, I'm pretty sure I did that correctly. It didn't work. It seemed to be because it was on a FAT32 partition and not an HFS+ partition. Installing it on an HFS+ partition solved it.

Hmm... Odd. You used to be able to install rEFIt to the EFI partition (which is essentially just a FAT32 partition, plus the EFI spec says it should look in FAT32 volumes for executables as well. Either way, glad you figured out a way. 

It would be helpful to mark this thread as solved from the thread tools menu at the top of the page.

---

### Post by ninjaaron on 2008-12-20
> **regebro said:**
> Solution: A small HFS+ partition (20MB is probably enough, I made mine 50MB, but only 14 is used) where rEFIt, and only refit is installed, according to the instructions on how to install it on external partitions (must be done from OS X).

So, can this be done on a single boot machine?

---

### Post by regebro on 2008-12-20
> **ninjaaron said:**
> So, can this be done on a single boot machine?

Uhm. Yes? In a way, since you boot via rEFIt, it's in some sense multiboot, but you don't have to have OS X installed anymore. I have it on an external HD for testing webapps on OS X; should I need to. But my internal HD is now all Ubuntu (except for the small rEFIT partition, and the 200MB EFI partition. (I'm not sure if that one is strictly needed, though).

As mentioned above, some people mention that it should work to dop the correct blessing of the Linux stuff and skip rEFIt, but I haven't succeeded, and I have no more time for testing now. I need this machine for work now. ;)

---

### Post by hyperboloid on 2008-12-20
> **ninjaaron said:**
> So, can this be done on a single boot machine?

Yes, I'm running a single boot without rEFIt and after following the instructions for blessing my bootup takes place with little or no delay. This is what I did:

[http://ubuntuforums.org/showpost.php?p=5166788&postcount=21]("http://ubuntuforums.org/showpost.php?p=5166788&postcount=21")

---

### Post by regebro on 2008-12-21
> **hyperboloid said:**
> Yes, I'm running a single boot without rEFIt and after following the instructions for blessing my bootup takes place with little or no delay. This is what I did:

[http://ubuntuforums.org/showpost.php...8&postcount=21]("http://ubuntuforums.org/showpost.php...8&postcount=21")

That link doesn't work.

---

### Post by hyperboloid on 2008-12-21
> **regebro said:**
> That link doesn't work.

Sorry - try it now. It's a link to a post in the FAQ found at the top of this forum. You can also find the link by reading the second post there. I think I just did steps 5 and 6 there, since I already had a running system once I found the post, but I may have done step 4 earlier.

---

### Post by cyberdork33 on 2008-12-22
> **ninjaaron said:**
> So, can this be done on a single boot machine?

You need OSX to bless.

---

