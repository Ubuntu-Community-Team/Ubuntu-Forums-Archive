---
title: "Macbook keyboard not working (at all times)"
date: 2007-03-01
forum: Apple Intel Users
---

### Post by JGJones on 2007-03-01
Good morning everyone.

My laptop:

Macbook 1.83GHz Core Duo with 60GB HDD and 1GB of RAM.

It is dualbooting between Ubuntu Feisty Fawn and OSX - this is working.

I originally installed Edgy Eft on this Macbook and dist-upgraded to Feisty Fawn. This was working until a few days ago when I did the daily apt-get upgrade.

This included the new kernel versions. I then rebooted the system.

Keyboard now no longer work. At all. Even in command line (recovery mode). And this is true for all kernel version. No keyboard means there's no way I can work on Ubuntu at all. I'm not too fussed since I am aware that Feisty Fawn was still at "alpha" stage when I upgraded to it, but it was very stable for me during my use of it.

However I was surprised to not have a working keyboard at all, so I wondered if anyone had any possible solutions, perhaps making use of a boot CD to repair it etc without needing to reinstall?

Many thanks.

---

### Post by xoai on 2007-03-01
I have the same issue as yours. Now I have to login with safe mode. I am sure the Xorg runs correctly because I am still able to type username and password to login. Anyone has more information?

---

### Post by JGJones on 2007-03-01
No, I don't have the same issue as you.

The keyboard simply does not just work. In GUI or in command line or in safe mode or any other times - it does just not work - I cannot type at all, and so I can't exactly fix Ubuntu without a keyboard :) (it's fine on OSX)

---

### Post by incubus on 2007-03-01
Since your keyboard is not working at all, it's going to be very hard to change anything.  But you already know that.  : )

How about downloading a Feisty live CD, and booting it to get access to your system?

I have a kind of similar problem with my macbook: most of the times I start it (with rEFIt), my keyboard doesn't work till the kernel is loaded.  In other words, I can't do anything with GRUB.  It's very annoying and I haven't found a solution yet.

But back to your problem, I would search around for different solutions.  Then boot a live CD and see if you can fix it from there.  Some people have complained about xorg, it could be just a few lines there.

If all else fails, you may have to reinstall.  Upgrading to Feisty at this point is risky.  A fresh install, on the other hand, may save you from incompatibilities.

incubus

---

### Post by egh on 2007-03-03
You need to modprobe usbkbd. You'll need to add this to /etc/modules so it gets done on startup.

The difficult part will be doing this since you can't use the keyboard. If you have ssh installed, you can ssh into your machine.

If you don't, boot with a livecd. Mount /dev/sda3 (or whatever your filesystem is) on /mnt.

sudo chroot /mnt su

Then:

apt-get install openssh-server

Then you can reboot into the system where the keyboard doesn't work and modprobe usbkbd.

---

### Post by apol on 2007-03-26
This is great because that works, but I can't use fn keys with that module... :(

---

### Post by JGJones on 2007-03-26
incubus and egh - many thanks for your replies - I'll give both a go.

Right now I've noticed if I do any kernal upgrades, it'll stop working so I'm still on the .9 version, even though it's up to .12 or .14 (2.6.10.something? can't remember off top of my head, I'm in OSX for video editing atm)

So I'll switch to .latest and then do the above and report back if any joy.

Many thanks

(ps time for some envy...my wife have just gotten a brand new Macbook Pro this morning....sigh...)

---

### Post by JGJones on 2007-04-08
SSH'ing into my macbook does work and I was able to modprobe usbkbd successfully to have it working under the latest kernal but there's a snag...

As mentioned already - Fn key no longer works  - this does have the nice bonus of making the F1-F12 the default keys instead of pressing fn-F1-F12 to get the result BUT it also means I no longer have access to the DEL key by pressing fn-backspace - that's a key I use a lot.

Thanks all for the help and I hope someone know a solution to fixing the Macbook keyboard in Ubuntu? 

Cheers

---

### Post by siepo on 2007-04-08
You need the following line in some file in /etc/modprobe.d/options:

options hid pb_fnmode=2

This used to be an option for usbhid. You may have to regenerate initrd with:

update-initramfs -c -k `uname -r`

---

