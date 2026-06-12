---
title: "Startup problem"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Redattack34 on 2007-08-22
I've been thinking about dual-booting Linux alongside XP, so I downloaded and burned a LiveCD of the latest release, (7.04) just to see if it would work and try it out. After some restarting, I managed to get into the BIOS settings to get it to boot from the Linux CD.

It lets me get to the screen with an Ubuntu logo and an orange bar moving back and forth, but then it breaks. It shows a black screen with white text (much like the old DOS prompt or the newer windows command line, I don't know what it would be called in Linux) giving an error message:

```
/bin/sh: Can't access tty; job control turned off
ata 2.01: failed to set xfermode(err_mask=0x4)
```

There's a long number before the second line, I think it's a timer. Anyway, it repeats the second line several times, with a greater number at the beginning each time, and then gives the following line:

```
ata 2.0: failed to set xfermode(err_mask=0x40)
```

Then it stops doing anything, and I have to force it to shut down, eject the CD, and boot into windows.

I'm a complete noob to Linux, so I don't know what sort of information you'd need to help me get through this. I did run the md5sum on the .iso I got from the website, it checked out. The problem occurs with all three of the start modes that I've tried so far (including the 'Check CD' option). I downloaded the desktop 7.04 standard computer, if that helps.

As a side note, since I expect that I'll have to create a new partition in order to fully install it, would doing that cause any damage to the files on my existing windows partition?

Any help would be appreciated.

---

### Post by Hobo Joe on 2007-08-22
I can't help with the error, but I can tell you that as far as partitioning, it shouldn't cause problems.

First, make sure you have some extra space on your Windows partition, and before you partition DEFRAG. Defrag several times. If the data isn't thourougly consolidated then you could risk data loss.

But if you make sure to do that, you'll be fine.

---

### Post by alienexplorers on 2007-08-22
Have you tried the alternate cd.  Maybe it will let you boot and install ubuntu.

---

### Post by Redattack34 on 2007-08-22
Hobo Joe: Thanks for the information.

alienexplorers: I don't have an alternate CD. I don't want to install anything right away, I was hoping I'd be able to use a Live CD to try Ubuntu and see if I like it before I decide on anything.

---

### Post by pt123 on 2007-09-28
If you are getting failed to set xfermode on older CD drives try this solution:
[http://fak3r.com/2007/06/22/failed-to-set-xfermode-solved/](http://fak3r.com/2007/06/22/failed-to-set-xfermode-solved/)

In grub, “…at the end of this new menu item add it as an argument to the line:
```

# defoptions=quiet splash irqpoll

```


You just need to ad `irqpoll` to your grub line. So in so in /boot/grub/menu.lst I added irqpoll to the kernel line:
```

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=495b ro quiet splash irqpoll

```

---

