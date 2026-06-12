---
title: "[SOLVED] Grub, Error 18, and Hope"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by onthefence on 2008-03-28
So, I have really been lucky to have no real problems with installing Ubuntu as a newbie. And I really attribute it to luck because if I did run into problems I know that I would be crying and frustrated over it.

Anyway, I just installed Ubuntu 64-bit the other day and got the dreaded "GRUB ERROR 18"!!! Well, it was very disconcerting because I had just setup two other partitions with 32-bit and 64-bit Windows and had spent some time configuring them. So I tried not to panic and searched the wonderful Ubuntu forums for an answer and some hope. Well, I did find a post on Error 18 which explains what it means and it had something to do with the grub information possibly existing beyond some data boundary setting in the BIOS. Well, whatever, I just rebooted and it went away. Like I said,I guess I'm just really lucky. 

However, I have had the desire to understand how GRUB works a little more. I have tried reading articles and manuals on GRUB, but I have not run across anything which is able to simplify the concepts into basic information that anyone could utilize to modify an existing grub file.

I know this isn't rocket science, which is why this post is in the beginner's section, but it seems to be a very difficult subject to explain in laymen terms. (Or maybe I'm just really thick-headed.) In any case, could anyone point me to some "good" resources for learning how to modify GRUB and/or how to make sure it's in the MBR and not in the root folder of the installation. Also any resources on explaining how the Windows Boot Manager and GRUB coexist on the MBR. Or if anyone feels like having a dialogue here, that would be very welcomed too.

Is it just me or does anyone else feel like at this point in time, something like installing an operating systems shouldn't be such a chore or hurdle to jump?

---

### Post by Duck2006 on 2008-03-28
These may help.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

[http://odzangba.wordpress.com/2007/03/10/how-to-restore-grub-using-the-ubuntu-live-cd/](http://odzangba.wordpress.com/2007/03/10/how-to-restore-grub-using-the-ubuntu-live-cd/)

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by Ub1476 on 2008-03-28
I can assure you that installing Linux OS is a really simple thing, but learning a new OS is another thing:)

The GRUB configuration file can be found in /boot/grub/menu.lst:

```
gksudo gedit /boot/grub/menu.lst
```

It's pretty good explained in comments how it work.

When you install a Linux OS, GRUB replaces the Windows bootloader. If you install Windows, the Windows bootloader replaces GRUB, but it doesn't add any existing OS, like GRUB does. In Ubuntu, I'm quite sure GRUB installs into MBR. Not sure how you can check it though...

I suggest you download [Super Grub Disk]("http://supergrub.forjamari.linex.org/") and burn it into a CD. This is an awesome tool, which can find and boot operativesystems, reinstall GRUB and more.

---

### Post by onthefence on 2008-03-29
Thanks both.

The Super GRUB Disk I will get for sure. Thanks.

And the bigpond article was exactly what I was looking for. Thanks.

Yes, in a single boot system, ubuntu is probably easiest to install, but as soon as you try multiboot, you run into all these other factors.:)

---

