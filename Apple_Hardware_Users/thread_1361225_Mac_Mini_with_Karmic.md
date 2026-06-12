---
title: "Mac Mini with Karmic?"
date: 2009-12-21
forum: Apple Hardware Users
---

### Post by Ted3929 on 2009-12-21
I have a 2 GHz Intel based Mac Mini currently running OS X and I'm less than enthused with that OS.

Since it's Intel based is there any reason I can't just pop in a Ubuntu disk and blow off OS X?

I checked the forums and couldn't find anything specific.

Thanks

---

### Post by thatguruguy on 2009-12-21
Run the LiveCD.  If it runs, try to install it.  Intel-based Macs are pretty well supported by Ubuntu.

---

### Post by tom4everitt on 2009-12-22
The only thing that's different with macs from (most) pc's nowadays is that macs are not booted by a BIOS, but by EFI. 

Therefore you usually install an efi bootloader such as refit, to make sure your mac boots linux properly. The linux bootloaders are beginning to support EFI-boots with grub2, but its highly experimental still. 

Also, macs use gpt partition table, whereas linux use mbr. They can exist simultaneously, but if they get out of sync (which they basically do as soon as you do any changes to your partitions in linux) you might experience booting problems. rEFIt contains an excellent partition syncer, which is another reason to install rEFIt. 

Heres refit (should normally be installed from within os x)
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

and here's a guide on how to install ubuntu on a macbook (should be fairly similar)
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)


I hope I didn't scare you, usually its not harder to use ubuntu on a mac than on a pc. It's just that a lot of people here get suprised by one of these reason after using ubuntu for a while, and something stops working.

Good luck!

---

