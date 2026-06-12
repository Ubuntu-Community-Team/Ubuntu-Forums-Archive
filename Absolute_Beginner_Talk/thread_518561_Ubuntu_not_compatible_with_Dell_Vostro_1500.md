---
title: "Ubuntu not compatible with Dell Vostro 1500"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by tashmooclam on 2007-08-06
I posted previously about the difficulty installing Ubuntu on the brand new Vostro 1500. 
The hard drive was partitioned for me by Dell, 20gb Windows, 100gb for Ubuntu.
I first did a DVD Ubuntu install attempt with 7.04 and got an error message doing the normal install.
So, I retried with install choosing "safe graphics mode". 
Finally, I tried to install Ubuntu 7.04 using Text Mode. This seemed to work.
I was able to get the screen allowing me to choose to start up Windows or Ubuntu, so I had achieved "Dual Boot" capability. 
After I chose to start Ubuntu, the screen went **black.** I could see that something was running the hard drive, but the screen was black. 
I wondered if perhaps I had done the manual partitioning incorrectly. 
I re-installed Ubuntu using the text method.
This time, I let Ubuntu have the entire hard drive, eliminating Windows entirely.
After the install, I started Ubuntu from the hard drive.
Another black screen.
Whether or not someone had another kind of experience with a Vostro 1500 Dell, I would avoid this machine for the time being.

---

### Post by anewguy on 2007-08-06
This sounds like a default video driver problem.  I do not remember the specifics right now, but you can press a function key (F6??) on the grub menu and then add to the boot for Linux telling it to use VGA mode.  You may want to try searching for that in this forum, as that's where I saw it.  In the mean time, I'll go searching and see if I can find what I'm talking about.:)

---

### Post by anewguy on 2007-08-06
Okay, so far I haven't been able to find the VGA thing yet, but here is something to try:

at the grub boot menu, highlight the Ubuntu entry you want to boot then press "e" - this says you want to edit the entry.  You should see something like this:

root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a42ae918-d19e-4605-aea6-7114c5ee4164 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic



Move down, using the arrow key, until the "root" line is highlighted, then press "e" again to edit it.  You want to change "splash" to " nosplash  noapic".   Then press "esc" until it says you can boot - just select that option and boot.  Please post back with the results of this test.  In the meantime, I'll keep searching for that VGA thing - it would go on the same line I think.:)


EDIT:  Okay, it looks like you just add " vga=771" after the "nosplash noapic " mentioned above.  Please let us know what happens!

---

