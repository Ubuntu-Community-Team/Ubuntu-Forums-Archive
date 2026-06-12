---
title: "PC restarts at when GRUB starts"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by studiodaz on 2006-08-07
Hi I am new to ubuntu and Linux.

After installing from the live CD onto a 2nd hard drive (win XP already on my 1st) I restart and can then load into ubuntu. 
After booting into Windows XP and restarting again I can no longer start the computer. 

It just keeps restaring after GRUM flashes on the screen.

Because the computer would not boot into an OS I have tried installing GAP. I can now load into windows but ubuntu just seems to show a bank screen with a flashing "_".

The live CD seems to work ok apart from I can not get my ASUS wl-138G v2 wifi pci card to connect, but I guess I should leave this for another post:-k .

---

### Post by tomplast on 2006-08-07
About the boot problem I would like to advice you to take a look at [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) and see if that helps. It guides you through the process of installing grub manually from the live cd. 

I don't know the cause of your problem (hopefully someone else maybe have a clue) but reinstalling Grub would at least correctly would at least tell if it's GRUB or the Ubuntu installation which is damaged.

---

### Post by studiodaz on 2006-08-07
that fixed GRUB and got me back into ubuntu but after booting up in windows again and then restarting the GRUB is broken again.

Would putting the ubuntu hard disk as master and the windows as 2nd fix this?

---

### Post by tomplast on 2006-08-07
> **studiodaz said:**
> that fixed GRUB and got me back into ubuntu but after booting up in windows again and then restarting the GRUB is broken again.

Would putting the ubuntu hard disk as master and the windows as 2nd fix this?

I don't know but I think that you would need to reinstall GRUB on the first partition on the first harddrive (Ubuntu after your change I assume) because GRUB needs to be on the first harddrive.

---

