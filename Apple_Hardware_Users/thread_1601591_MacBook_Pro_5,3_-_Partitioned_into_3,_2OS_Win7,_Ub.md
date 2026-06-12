---
title: "MacBook Pro 5,3 - Partitioned into 3, 2OS: Win7, Ubuntu"
date: 2010-10-20
forum: Apple Hardware Users
---

### Post by johnnymercury on 2010-10-20
Hi,
I've been having trouble with my experimentation and can't seem to find the solution to my problem anywhere on the internet.

My MacBook 5,3 runs:
Intel core duo P8800 @ 2.66GHz
4.0Gb RAM
250Gb HD

I divided my 250 HD into 3:
50 Gb - Ubuntu 10.10 64x.
50 Gb - Win 7 64x.
150 Gb - Free: I wanted to use this as a "warehouse" and keep all my files/music/videos/etc... here. It should be able to work on both OSs.  

So far I managed to break up the partition. I installed Ubuntu first, it loaded perfectly, managed to get it running on my mac smoothly after doing everything I had to do.

I then installed Win7, did all I had to do bla bla bla.

The big thing is: I can't choose to boot on Ubuntu, the computer turns on and goes straight to windows. 

I tried looking for boot loaders/managers, but no one explained how to install them, or if they did it didn't seem compatible with my setup. 

There might also be a minor issue:
the commutative drive is formatted to FAT32, i don't know if this is correct, but I can always re-do it.

Thank you for any feedback!
- JohnnyM

---

### Post by johnnymercury on 2010-10-25
no one??

---

### Post by linuxopjemac on 2010-10-27
are you using refit ?

---

### Post by johnnymercury on 2010-12-17
I tried to use refit, and it gave me two options: 
boot on windows 1, and windows 3.
windows 1 being the actual windows 7 OS, and windows 3 being Ubuntu. I tried ubuntu, but it didnt load - the screen just stayed black and I had to restart my computer after 30 min.

Any suggestions??

---

### Post by yugnip on 2010-12-19
He cannot use refit as he isn't booting mac osx. He needs a Grub menu.

Try booting while depressing the Option (alt) key.

---

### Post by johnnymercury on 2011-01-06
I found a solution for the dual-boot option on the Mac (without a mac OS)
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

However I still have no idea on how to create a commutable partition that would work for Ubuntu and Windows. Anyone?

---

### Post by johnnymercury on 2011-01-19
I guess what my question really is:
what filesystem should i choose for my blank partition that both windows 7 and Ubuntu would be able to read and write?
I found out that theres a program called ext2 ifl (Ext2 Installable File System For Windows) but it does not support windows 7. does anyone know any other option?

---

