---
title: "ibook g3 wake on Xubuntu - scrambled screen"
date: 2006-11-28
forum: Apple PPC Users
---

### Post by blithe on 2006-11-28
Hi there,

After getting Xubuntu installed on my ibook g3 700mhz - Running Edgy 6.10 and I've encountered a problem with sleep/wake.

pbbuttonsd seems to be working fine - The computer goes to sleep just fine, but when waking I get a gray scrambled screen, then a black screen, then a scrambled color screen where it finally hangs and requires a hard power cycle.

I combed the other threads but really didn't seem to have much luck. I tried the solution listed in this thread: 

[http://ubuntuforums.org/showthread.php?t=2368&highlight=ibook+wake](http://ubuntuforums.org/showthread.php?t=2368&highlight=ibook+wake)

But the problem persists. I'm also not getting any of the other wake-up messages that I think I should be getting? Just a frozen locked screen.

Can anyone shed any light on this subject?

Thank you,

Blake

---

### Post by ssam on 2006-11-29
does crtl + alt + f1, then crtl + alt + f7, do anything?

---

### Post by blithe on 2006-11-29
> **ssam said:**
> does crtl + alt + f1, then crtl + alt + f7, do anything?

Nothing. I would also like to note that the caps lock key is turned on for some reason after attempting to wake.

I have enclosed a picture of the scrambled screen. Sometimes this varies in color and the lines may appear in different places, but the general idea is the same.

---

### Post by blithe on 2006-11-29
Also, Here's a video I took of the whole sleep/wake process. Maybe it'll give you a better understanding of the problem.

[http://djblithe.com/video/wake-freeze.avi](http://djblithe.com/video/wake-freeze.avi)

Thanks!

---

### Post by blithe on 2006-12-05
I'm going to snap a bump on this. I after trying for several more days (Mostly taking shots in the dark at randomn xorg.conf settings) I'm still having this problem.

---

### Post by blithe on 2006-12-17
I think I've narrowed it down to a problem with pbbuttons. When I kill X, and close the lid on the ibook, upon waking it goes to a blank black screen, and is then unrecoverable.

Does anyone have a working pbbuttonsd.conf file that they use with an ibook G3?

Thanks in advance.

---

### Post by weiln on 2007-01-02
My iBook does this exact same thing.  Anyone found a solution?

---

### Post by drewsimon on 2008-01-20
I have the same problem. :(

---

### Post by mkr55 on 2008-02-23
Same on mine...

---

### Post by Dekunuts on 2008-02-23
I compiled my own kernel for my G3 and now everything works flawlessly. Also my new kernel is 15MB in size compared to 60+ of the normal one If you want to take the plunge, read this : 
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

