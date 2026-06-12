---
title: "Having trouble trying to boot back to OS X"
date: 2009-08-20
forum: Apple Hardware Users
---

### Post by Mitchell314 on 2009-08-20
Hello.

First of all, I was using OS X leopard on a Macbook, and I installed Ubuntu 9.04. Also, I joined and read the instructions after I installed Ubuntu on my Mac, and it's a wonder I got as far as I did while not knowing what I was doing.

Anyways, I installed Ubuntu (Jaunty, I think) on my Mac. I winged it, and there was much crying, reinstalling, and rebooting involved, but I managed to get a partition set up and installed. Great, but now every time I boot up, it automatically goes to Ubuntu. I want to get back to OS X, but I can't figure out how. I didn't overwrite it's partition. I can see "Macintosh HD" in my menu under Places. It's there, and I'm pretty sure everything in it is intact. I've tried browsing it, but then it occured to me that it was a very silly thing to do. Besides, I really couldn't do much with it at all anways. So, everything is set up and good, but I just want to boot up in OS X.

For example, here's what happens when I boot:
First, I see a featureless light blue screen. Then, after a little while, it goes black. It stays that way for a couple seconds, then some text shows up on the screen saying something like "Grub stage 2 loading." Then Ubuntu pops up. Finis.

Here's how I installed it. I actually had quite a few failed attempts and reinstalls, but I'll just post what I did that worked since I don't want to be typing all night.
I had Boot Camp create a 32 gigabyte partition for Windows. Then I rebooted with an Ubuntu DVD, and choose the advanced partition option. I deleted the Windows partition, and a failed Ubuntu partion that was created from a previous attempt to use the Window partition (thinking back, that might not have been a good idea). Installation goes fine. And that was pretty much it.

I've tried Grub, but my attempts with it weren't successful (kept saying it could not find the disk. I was trying (hd0,0) ). But that's most likely due to my ignorance with it. I've looked into /boot/grub/menus.lst, and it only shows Ubuntu. I'm a newbie to Linux, and I really like it, but I would also really like to use my original operating system.

So, to summarize my main question, how do I boot back into OS X? Or rephrased to be a little more general if you like, how do I boot a different OS/kernel in a different partition?

---

### Post by NielsAMD on 2009-08-21
Hello,

Try this:
Hold down the alt(option)-key when booting. You should see the two partitions and choose the mac partition.

Hope this helps you.

Niels

---

### Post by Mitchell314 on 2009-08-21
Thank you, thank you, thank you. I tried holding down c on boot up, but that didn't work. Alt-option did the trick. Now I feel stupid, but I've got both systems to work with. Thanks.

---

### Post by NielsAMD on 2009-08-21
You're welcome.

Also, if you dont want to keep pushing the button every time you want to choose an operating system, try installing rEFIt.
[http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html)

After you installed it (see link for instructions) it will bring up a menu on startup, allowing you to choose between the Operating Systems installed on the computer.



Niels

---

