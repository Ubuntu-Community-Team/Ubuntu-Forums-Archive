---
title: "macbook pro 1.1: reFit doesn't see ubuntu partition anymore!"
date: 2009-06-27
forum: Apple Hardware Users
---

### Post by gagginaspinnata on 2009-06-27
Hi man,
I had ubuntu 9.04 installed on a macbook pro (1.1) intel core duo 1.83ghz.
Everything went great. When  reinstalled windwos xp (I've triple boot), don't know why, refit doesn't see the ubuntu partition anymore!
I've cheked in mac osx the disk utility and, as you can see above, the linux partition is still here :P
[[img]http://img.skitch.com/20090627-gbsc4gmp7ufwtc7w7rqca1n7nm.preview.jpg[/img]](http://skitch.com/gagginaspinnata/biadb/immagine-1)[Click for full size](http://skitch.com/gagginaspinnata/biadb/immagine-1) - [color=#A7A7A7]Uploaded with [plasq](http://plasq.com)'s [Skitch](http://skitch.com)[/color]


How could I fix this issue?

---

### Post by Richardcavell on 2009-06-27
Hi.

First, don't repartition!  Don't mess with your partitions at all.  

Secondly, reinstall GRUB.  Use the Live CD and follow these instructions: [http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

Third try to reboot.  If you get 'No boot medium found', then you need to use gptsync.efi from the rEFIt menu.

If it's still not working, boot into OS X and make sure that rEFIt is blessed, and on your internal hard disk (best to keep it on your OS X partition I reckon).

Richard

---

### Post by gagginaspinnata on 2009-06-27
> **Richardcavell said:**
> Hi.

First, don't repartition!  Don't mess with your partitions at all.  

Secondly, reinstall GRUB.  Use the Live CD and follow these instructions: [http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

Third try to reboot.  If you get 'No boot medium found', then you need to use gptsync.efi from the rEFIt menu.

If it's still not working, boot into OS X and make sure that rEFIt is blessed, and on your internal hard disk (best to keep it on your OS X partition I reckon).

Richard

Firt of all I'd like to thank you :D

I'm writing you from the ubuntu 9.04 live cd. Following the guide you've linked when i prompt ```
root (hd0,1)
``` (I've tried also "sudo" instead of root) it says
```
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,1)

Error 21: Selected disk does not exist

grub> sudo (hdo,1)

Error 27: Unrecognized command

grub> sudo (sda3,3)

Error 27: Unrecognized command

grub> sudo (sda,1)

Error 27: Unrecognized command

grub> root (sda3,1)

Error 23: Error while parsing number

grub> 

```
And as you can see I've tried even "sda3" instead of hd0 cause sda3 is the partition where ubuntu is located:(
There is any other way?

---

### Post by Richardcavell on 2009-06-27
Hi,

The 'root' command here has nothing to do with sudo.

1.  Boot into your Live CD.
2.  Go into a Terminal.
3.  Type 'sudo grub'  [from a Live CD you shouldn't need a password]
4.  Type 'find /boot/grub/stage1'

It will give you something.  I'm guessing for you it will say (hd0,3)

5.  Type 'root (hd0,3)'  (or use the numbers it just gave you)
6.  Type 'setup (hd0,3)' (or use the numbers it gave you)
7.  Type 'quit'
8.  Now shut down and reboot.

I see that you're using Italian, but I don't think that changes anything.  The commands that you've quoted above are harmless and meaningless.  The error messages are expected.  You don't have a partition numbered 1 on your hard disk.  Somehow you've managed to end up with 0, 3,4 and the swap partition, which could be 2 or 5.  The hard disk is hd0 and the partitions are hd0,0 through to hd0,4 or hd0,5 depending on what the swap partition is numbered.  sda0 is a device file, and that's not relevant here.

Richard

---

### Post by gagginaspinnata on 2009-06-28
> **Richardcavell said:**
> Hi,

The 'root' command here has nothing to do with sudo.

1.  Boot into your Live CD.
2.  Go into a Terminal.
3.  Type 'sudo grub'  [from a Live CD you shouldn't need a password]
4.  Type 'find /boot/grub/stage1'

It will give you something.  I'm guessing for you it will say (hd0,3)

5.  Type 'root (hd0,3)'  (or use the numbers it just gave you)
6.  Type 'setup (hd0,3)' (or use the numbers it gave you)
7.  Type 'quit'
8.  Now shut down and reboot.

I see that you're using Italian, but I don't think that changes anything.  The commands that you've quoted above are harmless and meaningless.  The error messages are expected.  You don't have a partition numbered 1 on your hard disk.  Somehow you've managed to end up with 0, 3,4 and the swap partition, which could be 2 or 5.  The hard disk is hd0 and the partitions are hd0,0 through to hd0,4 or hd0,5 depending on what the swap partition is numbered.  sda0 is a device file, and that's not relevant here.

Richard

Wow I fixed the issue following you guide! Very thanks Richard :D

PS
It gave me an error:
[IMG]http://img526.imageshack.us/img526/2905/setud.png[/IMG]
but everything seems to work right so there is no problem :)
Thanks again!

---

### Post by Richardcavell on 2009-06-28
Hi,

Treat those messages as warnings, not as errors.  The output is exactly what you should have got.  I'm glad to hear that it's working now.  Your partition numbering scheme is a little unusual, but if it ain't broke, don't fix it.

Richard

---

### Post by gagginaspinnata on 2009-06-29
> **Richardcavell said:**
> Hi,

Treat those messages as warnings, not as errors.  The output is exactly what you should have got.  I'm glad to hear that it's working now.  Your partition numbering scheme is a little unusual, but if it ain't broke, don't fix it.

Richard


Thank you again, I'll let the partition as he is :guitar:

---

