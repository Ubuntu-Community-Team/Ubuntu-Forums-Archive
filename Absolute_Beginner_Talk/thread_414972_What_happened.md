---
title: "What happened?"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by LaidbackBill on 2007-04-20
While checking out my new installation and desk top I decided to throw in a cd.  I guess the default program  is "sound juicer".  Every thing seemed to work right as a browsed around the desktop changing background color etc.  Upon finishing up I removed the cd and shutdown the computer.
This morning when I started up again I had no hard drive to boot from.  I shutdown, inserted the live cd and rebooted, option for hard drive and all is well.  But I don't want to go thru this each time a play a cd, so what did I do wrong?  I would think that some how the harddrive became unmounted.  Explanation please.
Bill

---

### Post by Pobega on 2007-04-20
I don't quite understand what happened, but I'll give it a shot;

Is the GRUB bootloader booting? If so, what partition is your Ubuntu install on? And what is the GRUB bootloader's options listing it as?

---

### Post by LaidbackBill on 2007-04-20
When I started up first thing this morning the hard drive wasn't listed in grub, only the cd drive.  That's when I inserted the "live cd" and checked "boot from hard drive "and all was well, if that is more clear.  I restarted another time just to check it out and it now starts from the hard drive normally
Thanks

---

### Post by lamalex on 2007-04-20
boot into Ubuntu from your cd and check your /boot/grub/menu.lst to make sure it's still intact with your Ubuntu install.

---

### Post by orb9220 on 2007-04-20
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

### Post by LaidbackBill on 2007-04-20
I guess I didn't explain my action very well.  I now have no problems with loading.  Everything seems to be working fine although I will checkout another episode with "sound juicer" to see if I can recreate the problem.  Ubuntu is on a stand alone installation and grub seems to be working fine again after rebooting with the "live cd" in the drive and checking "boot from hard-drive".  I've restarted the computer at least four times now with no problems,goes to grub and loads fine.  I thought that maybe I did something with "sound-juicers" that may have done something to grub and didn,t want to insert the "live cd" each time after using the cd drive.  Thanks for the responses, I love this forum!  I will get back if I recreate the problem.
Many thanks Bill

---

