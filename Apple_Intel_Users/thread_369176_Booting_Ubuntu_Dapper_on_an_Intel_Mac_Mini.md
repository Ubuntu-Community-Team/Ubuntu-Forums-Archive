---
title: "Booting Ubuntu Dapper on an Intel Mac Mini"
date: 2007-02-24
forum: Apple Intel Users
---

### Post by garlito on 2007-02-24
Hi all,
I'm trying to install Ubuntu in my Intel Mac Mini. I was told that it's possible to do it after changing the partition table label to a msdos type one. I did, but when I complete the instalation process, my new ubuntu system can't boot, it show me a folder whith a question mark inside.

What can I do? Is it MacOs X necessary to run Linux in a Mac Mini?
Thanks in advance.

---

### Post by cbrain on 2007-02-24
Hi.

A folder with a question mark in means that you mac isn't set to boot from anywhere. Try holding down alt and selecting your boot location from there.

I hope that helps!

This is my first post!

---

### Post by entangled on 2007-02-25
garlito
You have run the ubuntu install and it all seemed OK? 
You get this problem when trying to reboot for the first time?

The mini usually does display a question mark for a time at first boot. Have you waited a few minutes? After it has worked once the boot time will be quicker, but it always shows a question mark.
There is a possibility that your version of grub cannot deal with the a20 gate on the mac. I thought this problem was fixed over a year ago in grub, but it might still be a problem. When I first did this I had to get grub version 0.97 and install it onto the hard disk by booting the live CD and getting grub from a USB stick.

If I can find precise instructions for grub upgrade I will post later.

---

### Post by entangled on 2007-02-25
I got the info on this from
[http://ubuntuforums.org/showthread.php?t=233243](http://ubuntuforums.org/showthread.php?t=233243)

There it said use a20-patched grub 0.97-1ubuntu10. We are now on grub 0.97-11ubuntu14.

If you do have the grub problem then boot will start but you get a black screen or a message about grub stage 2 failing.
Someone reported getting a black screen at first boot but OK after that.
Don't be afraid to re-install ubuntu to get it to work. Keep trying. 
I install Windows 2000, XP, 2003 frequently at work and that doesn't always install either.

---

### Post by garlito on 2007-02-25
Thanks cbrain and entangled, it works fine now.

The first problem was I forgot to put the flag "boot" to my root partition. The second was about grub and I solved it using the patched version provided by Entity in that howto.

I've got now Ubuntu and Windows XP as I wanted, thanks to all of you :)

---

### Post by cocoia on 2007-02-25
Congrats garlito, I hope it all works out for you! :)

---

### Post by entangled on 2007-02-25
I'm glad it works now. 
I missed the essential word 'Dapper' in the title. The Dapper installer is, I think, pre-patch as far as grub is concerned. I think subsequent grub versions work OK because I have upgraded to Edgy and grub still works without getting a patched version.

---

