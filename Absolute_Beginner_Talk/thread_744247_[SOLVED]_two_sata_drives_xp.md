---
title: "[SOLVED] two sata drives xp"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by matrixunloaded on 2008-04-03
While I am fairly experienced with Windows (shudder), I am a newbie at Linux.

I have two SATA drives. 
SATA 1 has Gutsy 7.10. 
SATA2 has Win XP that was independently created (i.e., MBR and NTLDR still in tact). 

From a search, I have edited I have edited menu.lst of GRUB on SATA1 to provide as follows:

title           Microsoft Windows XP Professional
root          (hd1,0)
savedefault
makeactive
chainloader +1

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3b91d2b5-26e6-4186-b3cd-66bd3df4cd10 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3b91d2b5-26e6-4186-b3cd-66bd3df4cd10 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet


MS XP shows up 1st on GRUB, but hangs with "Starting up ..."
Gutsy starts up fine
Win XP starts up fine when Sata1 with Gutsy is unplugged.

I suspect I am missing something in the Win XP portion of menu.lst

Any help appreciated!

---

### Post by bumanie on 2008-04-03
The preferred installation then method, at least as far as windows is concerned, is for it to be installed first on the first hard drive. That way, during the install of grub, grub recognises windows and gives the choice to boot ubuntu or windows. The work around for the way you have st up your computer is to add map commands to /boot/grub/menu.lst
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
[COLOR="Red"]map        (hd0) (hd1)
map        (hd1) (hd0)[/COLOR]
chainloader +1
I assume you have the windows directions under a heading such as this
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
if not this will also cause problems.
For more information read this [http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk)

---

### Post by matrixunloaded on 2008-04-03
Thanks for the fast reply.

At first, it did not work until I figured out that "chainloader +1 must be on a new line, not following "hd(0)"

After that correction, Win XP boots up fine.

BTW, the reason for having Ubuntu as sata1 is that I want to get rid of Win XP ASAP!

Many thanks!

Matrixunloaded:)

---

### Post by bumanie on 2008-04-03
Glad it is fixed. You can mark the post as 'solved' by clicking thread tools and marking solved. I did have chainloaer on a separate line until I inserted the color tags - they mucked it up. I changed it as soon as I saw how the text appeared on the post.

---

### Post by matrixunloaded on 2008-04-03
I am not sure how the cups and beans icons work, but I did want to make sure you got credit for a "thank you" from me.  Let me know if it is automatic or something I need to do.  Thanks again!

---

