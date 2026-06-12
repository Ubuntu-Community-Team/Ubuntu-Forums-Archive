---
title: "in need of extremely fast help"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by Rioku on 2008-04-19
Ok so I had set everything up on my ubuntu installation..infact the best iv ever had an installer (using 8.04)
had awn dock...all the effects loads of cool programs...and I got so attached to it... I decided I would continue using it.. so everything I have done over the past few days are in my installation...

I used the wubi installer if this will help with my problem

the problem is I just turned off my laptop.. went out for an hour came back and boot it up.. got the normal windows vista or ubuntu boot I chose ubuntu but this time it wouldnt start!

Error 15 : file not found

Can anyone help me with a real simple way to fix this if it is fixable? (please say it is I have college work on there for monday -_-)

---

### Post by crashcoredump on 2008-04-19
If you just need the files you can run LiveCD and boot the machine and transfer the files you need for Monday..

Then you can use the CD to repair the boot partition.

Good Luck,

---

### Post by crashcoredump on 2008-04-19
There is also this post,,,


[http://ubuntuforums.org/showthread.php?t=297261](http://ubuntuforums.org/showthread.php?t=297261)

and this

[http://sudan.ubuntuforums.com/showthread.php?t=644773&page=2](http://sudan.ubuntuforums.com/showthread.php?t=644773&page=2)

---

### Post by pietjanjaap on 2008-04-19
Grub cannot find the harddisk.
So start pc**,(get into grub bij getting menu of windows and ubuntu or bij pushing esc)**
then push "e"
This is to edit the harddisk number.
go to the hd nr and change it to all the numbers you think is possible.
Like: (hd0,0)
(hd0,1)
(hd02)
(hd1,0)
(hd1,1)
after each change try to boot.

Remember the number wat works.
In ubuntu go to menu.lst and change the hd number.
\boot\grub\menu.lst

change only this where is (hd0,0)

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		**(hd0,0)**
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=677d311a-d8e2-44c6-8cd9-928fd76406ab ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		**(hd0,0**)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=677d311a-d8e2-44c6-8cd9-928fd76406ab ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		**(hd0,0)**
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=677d311a-d8e2-44c6-8cd9-928fd76406ab ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		**(hd0,0)**
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=677d311a-d8e2-44c6-8cd9-928fd76406ab ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		**(hd0,0)**
kernel		/boot/memtest86+.bin
quiet

---

### Post by Rioku on 2008-04-19
ah I could do that yeah i completely forgot about live CD's -_-

But how do I fix this issue? since I used wubi? can someone please tell me what to do to fix the actual OS as I put allot of hard work into setting it up

Atleast I supose The college work issue is solved

---

### Post by Vadi on 2008-04-19
I would recommend asking this in the Wubi forum ([http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234))

---

### Post by Vadi on 2008-04-19
Actually, you don't need to post there, there are two threads about this already. Check them out.

---

### Post by Freddie.Ruddick on 2008-04-19
Have you tried booting off (for example) a Knoppix LiveCD. It would let you mount your drives and copy anything useful off them, before you look into reinstalling or whatever.

---

### Post by Vadi on 2008-04-19
Wubi uses the windows bootloader, so other livecd's / grub reinstallation doesn't matter here I think.

---

### Post by Rioku on 2008-04-19
your right the LIVE CD is useless :( oh man I need this issue fixed and soon..

Please if anyone knows a way to fix this help me out. Thanks for everyone whos put some help in so far

---

### Post by Meskarune on 2008-04-19
Maybe you could download a windows live cd?

---

### Post by Rioku on 2008-04-19
*bump* sorry ... just really need this sorted

---

### Post by Rioku on 2008-04-19
A windows Live CD? is this even real? how would that help me?

---

### Post by Vadi on 2008-04-19
Did you read the threads in the Wubi forum about this like I said?

---

### Post by jrharvey on 2008-04-19
YES!!!! try the wubi forum. There is a guynamed "AGO" who monitors that section who is very good about answering questions right away.

---

### Post by Rioku on 2008-04-19
yes I tried the wubi forum.. no luck no one is replying to any of the error 15 threads..

---

### Post by Rioku on 2008-04-19
nevermind ignore this thread.. just gonna uninstall and re install

---

### Post by Meskarune on 2008-04-20
> **Rioku said:**
> A windows Live CD? is this even real? how would that help me?

If you'd only use google, you could answer your own question. :)

But if you want to fix your bootloader you need to re-install it. And that could be done from a window's live cd. But I think I might have found an easier solution for you:

[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

Its a program you can start from a disk, usb or floppy  that allows you to repair both windows and linux boot loads.

---

### Post by Vadi on 2008-04-21
That's all cool, but this is *wubi* we're talking about, not a "real" installation. He has no grub. Wubi uses the windows bootloader.

There are still threads in the wubi forum about the error 15, but if what, I'd recommend that you just reinstall Ubuntu on it's own patrition this time, since you've gotten comfortable in it with Wubi.

---

### Post by Meskarune on 2008-04-21
Super grub disk also edits the windows boot loader. :)

---

