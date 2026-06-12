---
title: "How do I remove a message that's flooding my logs? - &quot;BUG: scheduling while atomic&quot;"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by ubunuby on 2007-08-22
I dont know why but my logs are being flooded with this message and its going a dozen times a second

> BUG: scheduling while atomic: swapper/0xfffe0000/0
 [schedule+1528/2704] __sched_text_start+0x5f8/0xa90
 [handle_fasteoi_irq+155/240] handle_fasteoi_irq+0x9b/0xf0
 [do_IRQ+69/128] do_IRQ+0x45/0x80
 [common_interrupt+35/48] common_interrupt+0x23/0x30
 [default_idle+0/96] default_idle+0x0/0x60
 [cpu_idle+141/208] cpu_idle+0x8d/0xd0
 [start_kernel+869/1056] start_kernel+0x365/0x420
 [unknown_bootoption+0/608] unknown_bootoption+0x0/0x260

I googled around for it but I didn't find any solution. I can only find a post in german about it being a problem with Nforce4 motherboard and USB. Is there a way I can stop logging this message so my log files dont explode and hang my system?

It's happening in my message, kern and syslogs.

---

### Post by cmnorton on 2007-08-22
Sorry, I don't have an answer, but found a few more references. This part of your log:

[schedule+1528/2704] __sched_text_start+0x5f8/0xa90

shows up here

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg314029.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg314029.html)

There are more references. I just listed the first.

I'd keep looking using different lines in your log file. I took your first line and searched, and as you had noted in your post there was only one reference on a German web site. Other lines have provided a more fruitful search.

As another example,  this part of the log

[unknown_bootoption+0/608] unknown_bootoption+0x0/0x260

yieled quite a few searches, including this:

[http://ubuntuforums.org/showthread.php?p=3192761](http://ubuntuforums.org/showthread.php?p=3192761)

Good luck.

---

### Post by ubunuby on 2007-08-22
Hey thanks for taking the time to help me look! I was only thinking of searching for the first BUG: line. From what I read they mention something about this in Gutsy, I hope its fixed by then.

---

### Post by ubunuby on 2007-08-24
I can't find any issue related to mine, because all my devices are seemingly working as they should, and I don't have any of those things they are talking about.

I don't care about fixing the problem, please if anyone could show me how to edit my log config so that I can just omit this message entirely, then my system doesn't hang from log pressure.

---

