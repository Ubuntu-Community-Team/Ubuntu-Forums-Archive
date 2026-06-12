---
title: "Firewire possibilities?"
date: 2008-04-02
forum: Apple PPC Users
---

### Post by faelin on 2008-04-02
I have cloned both the Tiger and Leopard installation DVDs to a firewire drive. From there I can easily install either OS on a Mac without having the physical dvd.

Can I do something like this with the Linux Live CD's? 
Especially since my old PPC optical drive is far from the best, my thought was to run the live cd off of the firewire drive?
Any thoughts?

---

### Post by stream303 on 2008-04-02
These may help.  For booting with a firewire **CD** drive:

[http://ubuntuforums.org/showthread.php?t=698290](http://ubuntuforums.org/showthread.php?t=698290)

Note that there is no space in that commandline.

To install onto a firewire hard drive:

[http://ubuntuforums.org/showthread.php?t=314237](http://ubuntuforums.org/showthread.php?t=314237)

The simplest way I know to dual-boot is to just install OSX onto the firewire drive, and put Linux on the Internal drive.  At boot, hold down the Alt-Option key to choose, or if you install Ubuntu last onto the internal, yaboot should sense the OSX install and make it a boot choice in the yaboot menu.

Of course you could repartiton the internal drive, and do dual booting there too as an option, typically osx first, and then Ubuntu.

---

### Post by faelin on 2008-04-02
Thanks Stream303.
However, perhaps there is a misunderstanding. What I want is to runn the installation off of the firewire drive. Basically clone the Live CD to a partition on the FW drive.
I have done it with both the Leopard and Tiger disks. Then I hold down option on boot, select the installer, and run it just like it were a cd. The benefit is that th FW 400 would be faster than the Live Disk, or even the Mac Installer DVD (there is no disk check on the FW)
I hope this clears up what I want to do.
here's a reference to a forum decribing the technique. I tried it for the Live Ubuntu PPC Disk, but it did not work. My hope is that there is another way.
[http://www.macfixit.com/article.php?story=20070705094933652](http://www.macfixit.com/article.php?story=20070705094933652)

---

### Post by slacka-vt on 2008-04-02
Could you maybe use something like "Carbon Copy Cloner" or "Super Duper"
under Mac OS X to clone Ubuntu CD to a new partition ?
Either of these applications maintain "bootability".
Could be worth a shot and, I for one, am very curious to see if it works.

~s

---

### Post by faelin on 2008-04-02
slacka-vt,
that's a really good idea! 
however, i don't know if super duper will work. it will not read .iso or .cdr as source. i don't know if .dmg is bootable.
i don't know much about CCC either. so, it will give me some homework to look into. I am gonna hope for the best but plan for the worst.
surprisingly, i have not found much info out there about  doing this type of live cd cloning to a FW drive. i am sure i am not the oly one to think of. hopefully someone can shed more light.
thanks

update...
ok, i was wrong. super duper is copying the files just fin. i was looking for the image and not the disk... duh!
however., the computer doing the work is currently downloading the alternate-iso's in case that's the way i need to go. 
sheesh! i take my macbook for granted... it would be done with the download by now, but it still has 3 more hours on that imac...
so, i will not be able to find out until the morning if it worked or not.

---

### Post by faelin on 2008-04-03
OK. I did the super duper thing as I described above... alas, it did not work.
In fact, i could not boot anyting off FW except an Apple disk. I have a FW CD-RW drive attached for burning, but the iMAc would not even load the live disk or Alternate disk from it. 
There has to be a way to do this though. Let's say a classroom has a bunch of old iMacs and wants to install ubuntu, it would be faster to use firewire as an install source than an optical drive...
someone, somewhere, knows somehow... maybe they will find this forum and share with the class.
I do thank everyone for their help and input, though!

---

### Post by stream303 on 2008-04-03
> **faelin said:**
> I have a FW CD-RW drive attached for burning, but the iMAc would not even load the live disk or Alternate disk from it. 
There has to be a way to do this though. Let's say a classroom has a bunch of old iMacs and wants to install ubuntu, it would be faster to use firewire as an install source than an optical drive

If you just want to substitute using an external firewire cdrom drive for install rather than using an internal one which may be broken or dirty, you can do the following, although it uses a regular install iso image, burned as an iso like this:  (although in the case of a bad cdrom drive to begin with, one would have to download and burn an Ubuntu ppc image on another machine first - it can be a pc or osx, doesn't matter.)

1) At boot, we need to get into an OpenFirmware prompt.  Hold down the CMD-Option-O-F keys while powering up.  (CMD=cloverleaf key, and sometimes Option=Alt key.)  Helps to have three hands to do this. :)

2) At the open-firmware prompt  boot >
type
```
boot fw/node/sbp-2/disk:,\install\yaboot
```
with no spaces except for the one between boot and fw.

This will boot the install image from the external firewire cdrom, and installation can proceed.

I'm sure you are doing the iso burn correctly, but for the lurkers out there:

(You can't just copy an iso image to a cd, you need to burn it using an iso procedure.  (ie, in OSX, drag the iso image to the left hand pane of disk-utility, highlight it, click Burn, and choose a low burning speed)  For more info on burning, see
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

