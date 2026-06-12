---
title: "Kubuntu Gutsy won't boot"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by BeholdMyGlory on 2008-03-09
So, I played around a bit with Kubuntu, changing it's themes and appearence, and then i decided to install splashy. But I just couldn't get it to work, to I tried what Xian suggested i post #4 in the following thread: [http://ubuntuforums.org/showthread.php?t=660332](http://ubuntuforums.org/showthread.php?t=660332)

But, when rebooting, it just got. Black. And black. Nothing BUT black. So, i went into recovery mode, removed splashy and changed /boot/grub/menu.lst back, removing all "vga=0x314".

So, I rebooted, the bootsplash shows up, and seems to load, but when the bar is full, it just does nothing for maybe half a minute, and then shows messages and behaves exactly like for the person in this thread: [http://ubuntuforums.org/showthread.php?t=660332](http://ubuntuforums.org/showthread.php?t=660332)

Of course I searched around a bit, trying to find a solution, and found:
```

Ctrl+Alt+F1 to get into terminal

sudo dpkg-reconfigure -phigh xserver-xorg
startx

```

It seems to work, I see my desktop and, well. Can do everything I normally can (exept shutting off the computer, for some reason, i have to typ sudo shutdown or sudo reboot in terminal)
*BUT,* when rebooting, i get the *exact same message*. Really frustrating.

So, anyone?

---

### Post by smartboyathome on 2008-03-09
Did you add vga=791 to your grub's menu.lst? If not, add it to the end of the line to get it to work correctly.

---

### Post by BeholdMyGlory on 2008-03-09
No, that didn't do the trick. It actually reurned me to the whole NothingButBlack-thing.
So, still having to execute startx every time i boot up...

---

### Post by smartboyathome on 2008-03-09
Ok, what about refreshing initramfs?
```
update-initramfs -u -t -k `uname -r`
```

---

### Post by BeholdMyGlory on 2008-03-09
That just seemed to add vga=791, which, again, made my screen go totally black right after bootsplash, no messages or anything.
Oh well. I'll look into it more tomorrow, right now I have to sleep. Worst case scenario is just a reinstall, anyway(thank god I just recently got a 80GB iPod that I can use as backup :P).
Thanks for your efforts, though.

---

### Post by smartboyathome on 2008-03-09
One more thing, check over the FAQ page for splashy - especially [this portion]("http://splashy.alioth.debian.org/wiki/faq#splashy_just_doesn_t_work"), and see if it helps.

---

