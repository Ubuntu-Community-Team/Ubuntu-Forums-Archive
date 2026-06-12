---
title: "Installing Ubuntu on a Power Mac G4"
date: 2009-04-04
forum: Apple Hardware Users
---

### Post by joshdudeha on 2009-04-04
Hello.

I used to have ubuntu on my pc for a year, until my dad needed windows.
Now, I have a Power Mac G4 MDD.
I like it and everything, but BOY I want ubuntu back.
I miss it a load, and I would love it.

I have the Alternate install CD for powerpc processors for the latest ubuntu, but I want to know how to install it before I bother.
I have Mac OS X Tiger on my hard drive.
And I have another hard drive, but it just has my music on it really.
I want to know, is it easy to partition on a mac? bearing in mind i want to keep mac os on the other drive. Easy to install?
I want to know how you boot between each system when you start up, that's the main thing I'm wondering about.
Is it similar to x86 Ubuntu?

Thank you for your help.

---

### Post by joshdudeha on 2009-04-04
please, anyone? :(

---

### Post by stmiller on 2009-04-04
Read the powerpc sticky. You pretty much pop the disc in and install same as x86.

---

### Post by joshdudeha on 2009-04-04
I have done.
But i'm not very clear on it :/

---

### Post by mkvnmtr on 2009-04-04
The way I have installed a few times on my ppc mac is probably the easiest for a beginner. Boot the mac install disk. Go to disk utility. Reduce the size of the mac partition enough to give yourself the free space to install Ubuntu. The first time I did it I left 15Gb unformated. Then exit the mac install disk. Then boot from the Ubuntu disk. When you get to the point that it asks how you wish to install choose to install into the largest free space. That should give you a good dual boot. After you gain experience you might wish to do it a little differently but the first time this method will go smoothly.

---

### Post by joshdudeha on 2009-04-05
Sweet, thanks.
If the installation goes wrong.
How would I correct or remove ubuntus partition and have it back to normal for a bit?

---

### Post by mkvnmtr on 2009-04-05
The very worst thing that could happen is that you would have to reinstall your mac os. Takes about an hour. You should of course have everything backed up so there is not much you can do without using an axe that won't fix pretty quick.

---

### Post by joshdudeha on 2009-04-05
Ok. thanks (:

---

### Post by cyberdork33 on 2009-04-06
There are some specifics about the powerpc version that are a little different than than the x86 due to the lack of support of the powerpc architecture by various companies. Most notably, Flash and Java. You can also find more info here:
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

Also, there are communities of Linux on PPC users out there that can help you get what you need working... There are several users that pop in here that are active at:
[http://www.ppclinux.info/](http://www.ppclinux.info/)

---

### Post by joshdudeha on 2009-04-06
Thank you for your help.
I think I'm just going to put the mac downstairs and have the pc up here so I can put linux on, the normal way.
Thanks for help though

---

### Post by stream303 on 2009-04-06
You've got some nice options available.

IF that external drive is a bootable firewire type (not just usb), you can install OSX to the external firewire, and use the internal drive for Linux.  In this case, after installing osx to the external drive, boot up holding down the "alt / option" key, and choose the firewire for boot for osx.  Done!  Then you can install Ubuntu on the internal drive, and perhaps dedicate the entire internal drive when partitioning by using "Use the whole disk" and it will figure out the partitioning for you.

Now when you boot, you can either choose OSX or Linux from the yaboot boot menu, or when you power up you can again hold down the alt-option key and choose which disk to boot from.

If that external drive is just usb and not bootable like firewire, you may want to reinstall as a dual-boot to the internal.

What you can do here is reinstall OSX to the internal drive, but when you do, FIRST go to the top bar and use OSX's disk-utility to partition the internal drive for say half of it.  Use the sliders up and down to adjust how much of the disk you want to use for OSX, and leave the rest as "free space".  THEN continue on with the rest of the osx install.  I typically just run a 50/50 partitioning for my dual boot.

Once that works, go ahead and install Ubuntu onto the "free space".  Now when you boot, you will be presented with a choice of either osx or Linux.

(Tip - if you reinstall, grab the latest "combo update" from Apple to get OSX patched to the very latest in one step rather than going though incremental system upgrades.)

OR if the external is a firewire, you could install Ubuntu to that, but it will take some manual editing of yaboot.conf and perhaps your fstab to get it going, however as a first step, I'd suggest either the dedicated osx to the external, and Ubuntu to the internal, or do a dual-boot on just the internal drive.

Whew!  Nice to have options - since I tend to hack around with a lot of ppc distros, I just stick to dedicating my external firewire for OSX, and then mess around with my internal drive strictly for Linux.

---

