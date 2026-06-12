---
title: "Cannot create a usb drive for Mac"
date: 2011-03-09
forum: Apple Hardware Users
---

### Post by kilaka on 2011-03-09
Hi.

I've created a boot usb drive but my macbook pro (6,2 intel) does't recognize it.

I got to the drive selection but can only select the hard drive.

I created it using two methods - Mac and Ubuntu.

Anyone encountered a similar problem?

Thanks.

---

### Post by kilaka on 2011-03-09
A friend of mine tried on on Windows with 3 different flash drives and didn't succeed as well.

Is there a general problem with booting from a thumb drive?

---

### Post by johnveix on 2011-03-14
I'm having the exact same problem as you, was going to post another thread but will post what I have here instead. Hopefully we can both get the help we need. :D



I've recently been trying to attempt to install Ubuntu on a partition on my macbook pro OS X 10.6.6.

I have attempted to create a bootable USB stick (as I currently do not have any CD's/DVD's to use). I have followed the guide on the Ubuntu installation page twice, word for word, command for command. Everything goes flawlessly, all the files are visible on the drive when I checked, and I have never received any errors in the terminal. The problem arises when I attempt to boot from the USB, it simply does not appear under the options when I attempt to boot. I have also checked the Start up Disk under system preferences.

I have attempted the installation on two different USB sticks, and the same problem on both, flawless to install to USB, but then it is somehow not booting.

I have checked with the USB company and directly from the website it says that the PNY attache is capable of this. It is the 4GB model.

With that being said, it's getting late and I'm sure this is a very simple fix, but I would greatly appreciate if any of the experts would lend a minute or two to an eager Ubuntu noob.

Cheers!

---

### Post by pindar on 2011-03-15
> **johnveix said:**
> With that being said, it's getting late and I'm sure this is a very simple fix, but I would greatly appreciate if any of the experts would lend a minute or two to an eager Ubuntu noob.
Cheers!

Unfortunately, no, there is no simple fix. Booting a mac from a usb stick can be extremely frustrating. It took me several attempts to get it working; you can find my solution in [another thread]("http://ubuntuforums.org/showpost.php?p=10478989&postcount=25") in this forum. Be warned though: there appears to be no clean solution that will work for all Apple hardware. Every now and then, people here post easier solutions that work for them like [here]("http://ubuntuforums.org/showpost.php?p=10556155&postcount=6"), but I have never been able to boot my mac mini or macbook this way. I can assure you that the method with grub 1.99-rc1 and reFit works on both my macs, but only with certain ubuntu versions (10.10, but not the alpha of 11.04).

Good luck!

---

