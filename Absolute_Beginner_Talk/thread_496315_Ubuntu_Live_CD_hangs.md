---
title: "Ubuntu Live CD hangs"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by hi67 on 2007-07-09
Hello, this is my first time trying out Ubuntu. I'm getting this when using the live CD to try it out:

[http://img294.imageshack.us/my.php?image=ubuntu2zk8.jpg](http://img294.imageshack.us/my.php?image=ubuntu2zk8.jpg)

The system just hangs there, I can move the mouse around but can't get anything to happen. It gets to this stage after the installation progress bar completes. The CD should be fine, I've checked its integrity and used it on another computer without problems there.

I'm using an AMD Athlon 64 X2 with a GeForce 7800 GT. I've tried both the 32 bit and 64 bit Live CD's with the same result.

Any suggestions are appreciated =]
Thanks

---

### Post by ramjet_1953 on 2007-07-09
First things first.

1. did you burn the image as an iso image, or just burn the file as a data CD?
It MUST be burnt as an iso image. Most burning programs have the option, in one of the dropdown menus to burn it as an iso (9660) image.

2. You must burn ANY iso SLOWLY. No faster than 4 X on high quality media.

3. If all of the above is OK, try booting the live CD with the no acpi option.

4. Failing this, download the alternate CD and load Ubuntu this way. It is a text based installer and overcomes problems with a graphical interface. After install, you can then install the driver for your graphics card.

Regards,
Roger 8)

---

### Post by loserboy on 2007-07-09
its the video card, i have the 7800GT as well, strange though. since feisty fawn that hasn't been a problem for me, is there any chance you are using the 6.10 (edgy) version?

in feisty I just have to boot in safe graphics mode then after the install the restricted driver manager kicks in

---

### Post by hi67 on 2007-07-09
Thank you for the replies.
I'm pretty sure the CD is alright since I've used it on another machine to boot ubuntu without problems, but I'll take your advice and do it again at the slower 4x speed since I'm pretty sure I did it at a faster speed earlier. And yes loserboy I'm using feisty, not edgy. Unfortunantly "safe graphics mode" doesn't even get as far as normal mode since safe graphics mode is locking up at the loading screen whereas normal mode locks up after the loading screen. Tomorrow I'll try out the new CD and if that doesn't work maybe some of the ubuntu variants.
Could you link me to the "alternate" text-based CD installer that you mentioned? That sounds like a good idea but I don't see it on ubuntu's site.

Thanks again for your input =]

---

### Post by loserboy on 2007-07-09
Try this  [https://wiki.ubuntu.com/EdgyKnownIssues/59618](https://wiki.ubuntu.com/EdgyKnownIssues/59618)

it's for edgy, but I really think thats the problem, plus it won't hurt anything if it doesnt work

---

### Post by zero244 on 2007-07-09
My experience with CD's etc is they can work one minute and not the next.
Try waiting a little while to make sure its not still completing the process. When I installed Ubuntu the last time I thought it was stalled.....then it suddenly finished the process fine.
You might try burning another copy its nice to have a second copy just in case.
I personally don't consider optical media any more reliable than a floppy disk. Sometimes they will last for years, sometimes just months.
Critical disks I always make at least two burns.
Also you usually get no notice when a optical drive dies.........so take a look at your cd\dvd drive.

---

### Post by hi67 on 2007-07-09
Thanks loserboy, that fixed it :D

---

### Post by loserboy on 2007-07-09
yay!

that really needs to be reported, that was suppose to have been fixed a while ago, but it seems some of the 6 and 7 series nvidias still have problems

---

