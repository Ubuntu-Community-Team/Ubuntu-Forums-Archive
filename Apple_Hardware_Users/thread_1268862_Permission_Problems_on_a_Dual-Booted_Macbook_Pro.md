---
title: "Permission Problems on a Dual-Booted Macbook Pro"
date: 2009-09-17
forum: Apple Hardware Users
---

### Post by 235711 Specimen on 2009-09-17
Hi, y'all.  This one's a bit of a doosie.

I've had a successful dual-boot running using rEFIt on my MacBook Pro for months, never really had any problems once I got it set up.  I've got three separate partitions (not counting the extra space allocated for rEFIt and behind-the-scenes stuff, as per usual dual-boot install): one for Mac OSX, one for Ubuntu 8.10, and one used as Shared storage space.

Last night, I was doing some permissions changing, trying to make it possible to access files in the OSX partition while running Ubuntu.  I don't know exactly how I did it, but something got messed up.

If I try to boot my computer normally, it goes straight to the Apple boot screen (with the apple logo and the little spinning wheel/circle thing), without giving me the rEFIt menu first.  It will stay like this for a few minutes, then the screen will go black and it will start again with the same display on the screen.

I've managed to boot my computer in three ways so far.

1) I can hold down "command+s" to go into a command-line only boot for mac
2) I can run Ubuntu from the install disk that I used to install it originally
3) I can use the Ubuntu install disk to access and boot from the first hard disk on my computer, which is my Ubuntu partition.

In poking around, one of the things I found was that my root user permissions had been changed.  I get the message:

"sudo: /etc/sudoers is mode ####, should be 0440"

From what I have read, this is bad.  I think it might be the reason that Mac won't just boot normally.  I'm not really sure how to fix it.  Any advice?

---

