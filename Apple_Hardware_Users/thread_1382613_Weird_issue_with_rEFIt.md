---
title: "Weird issue with rEFIt"
date: 2010-01-16
forum: Apple Hardware Users
---

### Post by Romu on 2010-01-16
Hi all,
I'm decided to give Ubuntu a try on my Macbook Pro 5.3. I figure out I will be able to install and run Ubuntu from an external USB HDD, am I right?

I know I could run OSX from a USB HDD with my old Ubuntu only Macbook Pro 2.1, but I don't know if I can the inverted configuration.

So I downloaded rEFIt 0.13 and when I run the rEFIt.mpkg I get and error message: "PowerPC not supported" telling me rEFIt is only for Intel based Macs :shock:[http://ubuntuforums.org/images/smilies/icon_eek.gif](http://ubuntuforums.org/images/smilies/icon_eek.gif)

Any idea?

Thanks.

---

### Post by linuxopjemac on 2010-01-16
rEFIt is for Intel machines. I don't know where you install too, but it's certainly not a macbook, but probably an iBook or PowerBook. You need a PPC version of Ubtuntu, with a yaboot bootloader.

---

### Post by Romu on 2010-01-17
Do you really think I don't try to install it on a Macbook Pro 5.3? Do you really think there is no "MacbookPro" written on the computer I'm working on this very moment? Have a look at the following screenshot, I hope it will convince you.

[IMG]http://forums.futura-sciences.com/members/romut-albums-divers-picture3852-capture.jpg[/IMG]

Have you some more constructive answers?

---

### Post by linuxopjemac on 2010-01-17
Romu, excuse me. Some people here on the forums do make mistakes like this. I don't know your level. I never heard of such an error. I read on the net that sometimes refit thinks it sees PowerPC as it was booted into Leopard in 64-bit mode. Try to boot into 32-bit mode and retry to install rEFIt.

[http://sourceforge.net/tracker/index.php?func=detail&aid=2850892&group_id=161917&atid=821764](http://sourceforge.net/tracker/index.php?func=detail&aid=2850892&group_id=161917&atid=821764)
[http://sourceforge.net/tracker/index.php?func=detail&aid=2917218&group_id=161917&atid=821764](http://sourceforge.net/tracker/index.php?func=detail&aid=2917218&group_id=161917&atid=821764)

---

### Post by Romu on 2010-01-17
You're my God, thanks a lot for the tips. Indeed yes, I tried to benefit from the 64 bits Kernel. I will rollback my mac.

So you know the answer for my first question, will rEFIt allow me to boot Ubuntu on a USB HDD?

Thanks again for the help.

---

### Post by linuxopjemac on 2010-01-17
That depends what kind of Mac you have. I have a MacBook 2,1 and its version of EFI doesn't allow it. I don't know about your Mac, but I guess it will work as I saw some newer models which did. Here you will find a guide for a MacBook Pro 3,1. Maybe it works for your Mac too.

[http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick](http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick)

Please let us know if it works for your type of Mac.

---

### Post by Romu on 2010-01-17
Thanks for the guide, I will give it a try. But I won't try on the Macbook Pro 2.1 which is now used by my wife.

My own one is a 5.3. I'll post here a result as soon as I can.

---

### Post by Romu on 2010-01-22
Ok, I tried and failed :(

I tried with a USB HDD and Ubuntu 9.10 32 bits. The problem is pretty simple, when booting the Live CD, I see the USB HDD into Nautilus, but GParted and the Installer as well don't see it.

I don't explain this behaviour, I tried to make this HDD GUID and MBR type, and no way, it is invisible by GParted and the Installer.

Any idea? Pretty strange isn't it?

I'll try with a simple USB key to see if the problem comes from my HDD or not.

---

