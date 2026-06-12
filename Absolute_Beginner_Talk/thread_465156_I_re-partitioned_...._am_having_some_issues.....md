---
title: "I re-partitioned .... am having some issues...."
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by ElEdwards on 2007-06-05
I have a 40-gig hard drive in my Presario 2170us, so originally I set up a dual boot with Ubuntu 7.04 and Windows XP Home, with each using 20 gigs.

I downloaded the QTparted iso and burned a cd, then booted to it and made some changes in my partitions:
(I'm not at my laptop right now, so these aren't labeled correctly and the sizes are approx.)....

**ORIGINAL**:
----- Windows XP - 20 gigs ----- | ----- Ubuntu - 19.5 gigs ----- | ----- Swap - .5 gig -----

**NEW**:
---- Windows XP - 14 gigs ---- | ---- FAT32 - 6 gigs ---- | ---- Ubuntu - 18 gigs ---- | ---- Swap - 2 gigs ----

After this, I rebooted to Windows and it, naturally, had to do an integrity check because of the resize, which in turn hosed GRUB, resulting in 'Error 17' upon a reboot.

I found some directions here (I love this forum) and was able to restore GRUB from my Ubuntu Live cd..... but now I get 'Error 15' when I try to select Ubuntu, which (if I understand things correctly) means that GRUB isn't set to the correct partition, right?

Again, if I understand correctly, in my **ORIGINAL** setup (see above), Windows was (hd0,0) and Ubuntu was (hd0,1)......
....but now in my **NEW** setup (above), Windows is still (hd0,0), the FAT32 is (hd0,1) and Ubuntu is now (hd0,2)

Two Questions:
Is restoration anything more that making sure that **/boot/grub/menu.lst** points to (hd0,2)??
Would the process be made easier with the Super Grub Disk?

Thanks! :)

.....and if I've really screwed things up, I can always start over, too.

---

### Post by jonward0690 on 2007-06-05
Error 15 means that grub is looking for a file and can't find it.
Since you don't even get the menu, its probably in the splashimage line in grub.conf   I know what this error is but I can't help you fix it though.

---

### Post by ElEdwards on 2007-06-05
Sorry.... but I DO get the menu.

When I said "**but now I get 'Error 15' when I try to select Ubuntu**", I was implying that I was selecting it from the menu.... sorry for not being more clear.

The menu does come up but from that menu, Windows is the only thing I can correctly select.... all other selections (all Ubuntu with two different kernal numbers) result in 'Error 15'.

:)

---

### Post by jonward0690 on 2007-06-05
Ok well I will google around and see if I can help you.

---

### Post by jonward0690 on 2007-06-05
Well I found two links that might help you out.  [http://www.statusq.org/archives/2007/01/07/1267/](http://www.statusq.org/archives/2007/01/07/1267/)                      [http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

---

### Post by dstew on 2007-06-05
You probably need to edit your /boot/grub/menu.lst file. The new partition may be messing up the original grub mapping. Can you boot your Ubuntu installation from the Live CD? If so, it will be fairly easy to edit. If not, we will need to mount the hard disk Ubuntu root file system onto the Live CD file system, and edit from there.

---

### Post by ElEdwards on 2007-06-05
Thanks for all this info.

dstew, your suggestion is what I've been thinking.... when I get home from work, that's what I'll try first and report back :)

Thanks!

---

### Post by vanadium on 2007-06-05
Just my 2 cents, but it may indeed be as simple as changing the references to the hd's like you suggested yourself in your first post. It is obvious that, if you add a partition, that the partition references must have changed. It is indeed the /boot/grub/menu.lst file that tells grub how to proceed.

---

### Post by confused57 on 2007-06-05
> **ElEdwards said:**
> Thanks for all this info.

dstew, your suggestion is what I've been thinking.... when I get home from work, that's what I'll try first and report back :)

Thanks!
Mounting your root partition from a live cd is an excellent way to edit your menu.lst.  You might want to try this:
highlight your Ubuntu entry in your grub boot menu, press "e" to edit, then change root to (hd0,2), then press "b" to boot...if you're able to boot into Ubuntu, you can edit your menu.lst to make the changes permanent.  Be sure to change your groot line, whichever method you use:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

---

### Post by ElEdwards on 2007-06-05
confused,
I did as you suggested at the main menu and Ubuntu booted perfectly..... so while I was there, I edited menu.lst, restarted and things are back to normal!!  Yay! :)

---

