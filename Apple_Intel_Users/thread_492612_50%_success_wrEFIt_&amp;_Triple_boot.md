---
title: "50% success w/rEFIt &amp; Triple boot"
date: 2007-07-04
forum: Apple Intel Users
---

### Post by sprucio on 2007-07-04
I currently have triple boot setup with my Macbook pro with rEFIt. The reason for this post is due to the fact that Linux sometimes loads fine and sometimes just gets stuck at the penguin logo after choosing the OS in the rEFIt menu.

First, I'd like to say that I used the following method from:
[http://ubuntuforums.org/showthread.php?t=198453](http://ubuntuforums.org/showthread.php?t=198453)

When I am at the rEFIt menu and select any OS other than Linux (OS X or Windows), it'll say something like "boot from n partition." When I choose Linux, it says just "boot from ." It is that is starting to make me think that I perhaps installed this wrong.

Can anyone who has a triple boot tell me what the text says when choosing Linux in the rEFIt menu at boot? Any suggestions on how to fix this would also be tremendously helpful.

---

### Post by cyberdork33 on 2007-07-04
can't offer much, but I do get the freezing when choosing to boot linux every once in awhile (although I only dual boot). I think it might be an issue with refit.

---

### Post by sprucio on 2007-07-04
Would you mind paying attention to the text message when selecting the Linux icon when in the rEFIt menu? Again, mine just says "boot from " without any partition number.

---

### Post by trouble1313 on 2007-07-05
Make sure you don't have more than a total of 4 partitions including that little EFI partition. Setting up a dedicated swap partition can push you over to 5. I think it's possible to actually have more but I could only get refit to boot from the first 4. 

-Trouble

---

### Post by cyberdork33 on 2007-07-05
you can only have 4 because legacy BIOS can only recognizes 4 primary partitions

BTW, I don't get any text, it sometimes freezes at the Tux logo as you stated in your first sentence.

---

### Post by Chrisj303 on 2007-07-05
Thats what my ubuntu partition says on the rEFIt screen (i Tripleboot)

"Boot Linux From"

It dosen't seem to make any difference at all. Until my recent windows re-install, my XP partition used to say the same - " Boot Windows from ", but it did no harm...

---

### Post by trouble1313 on 2007-07-05
Mine also does not define a partition at the boot menu for Linux. It does so for MacOS and for Vista but it just says 'boot linux from partition [blank]' where there's a number for the other two OS's.
-Trouble

---

### Post by sprucio on 2007-07-05
I guess this is a known problem?

---

