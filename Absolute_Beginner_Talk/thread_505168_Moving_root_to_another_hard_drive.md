---
title: "Moving root to another hard drive"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by grishenko2000 on 2007-07-20
I recently decided to delete my Windows partition because I was only ever using linux.
I used the GParted LiveCD to delete / copy / move stuff around and I got it all working fine.
Previous Configuration:
(sort of it was a while ago when i changed everything)
hda1     Windows Partition ~ 67Gb
hda2     Swap Partition       ~  2Gb
hda5    Linux root Parition  ~  5Gb

Anyway now my configuration is
hda1    Linux root Partition  ~ 34Gb
hda2    Swap Partition        ~  2Gb
hda3    /home Partition        ~ 38Gb

(I also have a 250Gb hdb but that doesnt really matter)

I manually edited Grub so that it would boot from the new hda1.
title		Ubuntu, kernel 2.6.15-27-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-686
savedefault
boot

Recently when the Update manager installed the kernel 2.6.15-28-686 it reconfigured grub menu.lst to:
title		Ubuntu, kernel 2.6.15-28-686
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-28-686 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-686
savedefault
boot
Attempting to boot from the old setup.
When I restarted with the new kernel it didnt boot and it ment that I had to manually change all the entries in grub to a root (hd0,0) and root=/dev/hda1

Is there anyway which I can change some settings so that each time a new kernel is installed I dont have to manually reconfigure the grub file?

Cheers
Matt

---

### Post by louieb on 2007-07-20
in the automagic section there is something called **groot** it sets the grub root. Also you need to look at the **kopt**  line also those line contain replacement text when Grub Update is run. I'm pretty sure thats what happened to you with the last kernel install. :confused:

---

### Post by grishenko2000 on 2007-07-20
ok cool Ive changed those things Thanx.

I cant think of any way to test to see if it will work installing a new kernel.
So I think ill sit back and wait for a couple of months and revive this thread if it doesn't work.

Thanx again
Matt

---

