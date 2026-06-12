---
title: "GRUB failed to install"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Rezn on 2008-04-18
Hi

I'm trying to install Ubuntu 8.04 beta alternative as I have a 8800GTX but every time GRUB fails to install so I have to use LILO but then I don't have the option to boot into Vista.

I tried using one of the guides on here for reinstalling GRUB but it doesn't work as GRUB didn't install in the first place.

How can I fix this?

---

### Post by quirks on 2008-04-18
Do you get any error messages? They might be helpful when looking for a solution.
How have you tried to reinstall GRUB, using Synatics?

quirks

---

### Post by zvacet on 2008-04-18
Use LILO  and when yo uare running ubuntu type this in terminal

```
sudo fdisk -lu
```

and remember on which partition is Ubuntu.After that try [this.]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub")If configuring network with DHCP failed it is not important.On next step select don´t configure network now and proceed.

---

### Post by Rezn on 2008-04-18
Thanks for the help guys.

Sorry I didn't explain more I was trying to post before Ubuntu locked up again.

I was getting a /target error.

Everything else installed fine.

I will try what has been suggested tomorrow.

Thanks

---

### Post by bag123 on 2008-05-01
Folks,

I have the same problem.  The alternative install CD failed to install GRUB in /target/ location and so as an alternative, I was forced to install Lilo.

I'm not dual booting but never really got on with Lilo so I'd like to replace it with the standard GRUB boot.

I have successfully managed to remove Lilo with the command lilo -u

I followed a wiki and forum post that explained how to reinstall GRUB if you'd lost it through booting an install CD etc.  ([http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html))

I managed to follow that with no problems.  This led to me getting all the right signs and responses - and upon checking /boot I can see that it is now there.

However, when I boot back into my system, I just get a GRUB prompt.  No list to choose from, just a basic GRUB prompt.  And I'm completely lost at this point.  I can't boot it through ('cos I don't know what I'm doing) and it gets just stuck.

Any ideas on what's missing that means GRUB goes directly to a prompt and doesn't give me a nice splash screen and a choice of kernels etc...?

Thanks,

Bag.

---

### Post by AndyCee on 2008-06-02
The GRUB menu is a file located as /boot/grub/menu.lst ('l' for larry).

Check to see if this file exists. It should contain the details of the menu. This thread has some useful info:

[http://ubuntuforums.org/showthread.php?t=798198](http://ubuntuforums.org/showthread.php?t=798198)

---

