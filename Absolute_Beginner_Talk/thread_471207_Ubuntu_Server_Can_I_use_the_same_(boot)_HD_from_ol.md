---
title: "Ubuntu Server: Can I use the same (boot) HD from old computer to new?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Cheese Sandwich on 2007-06-11
I've been using an old eMachine (w/ pentium or celeron, I don't recall) as a web server, & it recently died (I suspect due to a power supply issue).

Well I had recently installed a brand new hard drive in it, and it has Ubuntu server + xcfe installed on it, as well as the LAMP setup.

To replace this, I ordered a Dell PowerEdge SC440 w/ Dual Core Intel Pentium D 925 (they're giving the dual cores away for free for these, btw, instead of the usual Celerons - total price = $400).

Now: If I swap out the included hard drive with my old hard drive that has ubuntu server + LAMP already on it, & boot the thing up, will it "just work", or is there machine-specific configuration that's done during installation, making a new ubuntu install necessary or recommended?

---

### Post by dfreer on 2007-06-11
About the only things I can think of would be:
(1) different processor requiring a new kernel. However if you have the new generic kernel you should ok.
(2) different video card requiring different driver loaded in /etc/X11/xorg.conf. Although this isn't really a problem as long as you are comfortable with the CLI

you could pop it in and check :) shouldn't hurt anything, if nothing else simply put it back on the old server and then make a new installation enviroment.

---

### Post by az on 2007-06-11
> **Cheese Sandwich said:**
> I've been using an old eMachine (w/ pentium or celeron, I don't recall) as a web server, & it recently died (I suspect due to a power supply issue).

Well I had recently installed a brand new hard drive in it, and it has Ubuntu server + xcfe installed on it, as well as the LAMP setup.

To replace this, I ordered a Dell PowerEdge SC440 w/ Dual Core Intel Pentium D 925 (they're giving the dual cores away for free for these, btw, instead of the usual Celerons - total price = $400).

Now: If I swap out the included hard drive with my old hard drive that has ubuntu server + LAMP already on it, & boot the thing up, will it "just work", or is there machine-specific configuration that's done during installation, making a new ubuntu install necessary or recommended?

If it was installed using Edgy or Fiesty, then it uses UUIDs for the hard drive.  That means that if the hard drive is not the same device (sda1 instead of hda1, for example) Ubuntu will still mount it.  If you installed using Dapper or if your fstab does not use UUIDs, you will have to edit fstab by hand.

Your new computer need to boot it, so if the boot loader was on a seperate drive, you will need to reinstall the boot loader.  In that case, you may also have to configure the drives in /boot/grub/menu.list

Other than that, the only other thing you will need to reconfigure is the X server (graphics) since that is only autodetected during the install

The first time you boot, boot into recovery mode and run

dpkg-reconfigure -phigh xserver-xorg

then run

init 2
and you are good to go.

---

### Post by Cheese Sandwich on 2007-06-11
Thx for the replies, I'll do as you suggest.

Unfortunately, checking my order status, it looks like Dell isn't going to ship the new machine until the 21st!

Maybe I've been sent to the "back of the plane" in the super-economy rabble & livestock class, due to the bargain-basement purchase.

---

