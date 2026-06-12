---
title: "Dual booting?"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by dillbertdabomb on 2006-08-10
Ok Can sombody please tell me how to set up window and ubuntu to dual boot? and I wnat to use lilo if possible. I am a noob so can you do it step by step, or link me to something?

---

### Post by Lord Canti on 2006-08-10
If you are using windows now, then just install ubuntu from the live cd, and GRUB (if you don't mind) will be installed at the same time. That's what I use.

---

### Post by shoot2kill on 2006-08-10
you need to me more specific, what system do u use now...

linux, windowze...?

x86, 64bit, mac..???

---

### Post by Herman on 2006-08-10
> Ok Can sombody please tell me how to set up window and ubuntu to dual boot? and I want to use lilo if possible. I am a noob so can you do it step by step, or link me to something?dillbertdabomb, you can use either the 'Desktop live/install CD to install Ubuntu Dapper Drake version with, in dual boot with Windows. That has the nice new graphical installer and partitioner which is easier for new users (new to Ubuntu). It installs Grub to MBR automatically, I understand, (which I recommend anyway).

Otherwise, you can use the 'Alternate' install CD, which allows you a lot more options, but most new users (to Ubuntu) find that one more complicated. I have a website dedicated to helping new users with the 'Alternate install CD, complete with illustrations, just click on the following link, [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

The 'Alternate' Install will allow you to choose between Grub or Lilo, or even continue the install with no bootloader at all. You can choose to install Grub or Lilo to MBR, the first sector of a partition, or to a floppy disk or somewhere else.
I use Grub installed to MBR, and like Lilo installed to a partition, we can have both and boot with either one.

Grub bootloader is the best, and it is the one that most of us use, so it's easier to get help with if you have any problems. 

All the best, and good luck with it, Regards, Herman :D
[URL="http://users.bigpond.net.au/hermanzone/"]
[/URL]

---

### Post by dillbertdabomb on 2006-08-10
windows, 64 bit proceeser (amd atholon64)

---

