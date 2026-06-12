---
title: "HOW-TO: Dual-boot MBP with Ubuntu encrypted"
date: 2008-03-28
forum: Apple Intel Users
---

### Post by sunbird on 2008-03-28
[LEFT]I wanted to setup Gutsy x64 on my Macbook Pro v. 3.1 (Santa Rosa), but I also wanted to use full-system encryption for ubuntu. I'm keeping the OS X partition for firmware upgrades, etc.

** [SIZE="5"]Existing Guides[/SIZE]**
Your primary resources should be the [Macbook Pro]("https://wiki.ubuntu.com/MacBookPro") and (if you have Santa Rosa) [this page, which noties specific differences for the Macbook Pro v. 3.1]("https://wiki.ubuntu.com/MacBookPro/SantaRosa"). There are also some existing guides [here]("http://ubuntuforums.org/showthread.php?t=582406") and [here]("http://news.softpedia.com/news/Encrypted-Ubuntu-7-10-68383.shtml") for doing single-boot and windows dual-boot encryption, respectively.

** [SIZE="5"]Getting started[/SIZE]**
I started with a completely clean install of Mac OS X, mostly because I wanted to keep it as small as possible. If you go this route, you should be sure to click on "Customize" before starting the install and uncheck everything except the required system software. If you do this, you can keep you OS X partition down to 10 Gigs and have the rest free for Ubuntu.

If you'd rather keep your existing setup, copy anything that you want encrypted onto an external drive (or 2!), and try to delete apps and data that you don't want. Of course, you can always keep stuff on your HFS+ partition if you want, but my plan is to shift to Ubuntu, so I cleaned everything out.

Download the Gutsy 7.10 AMD64  Alternate CD from [the Ubuntu site]("http://releases.ubuntu.com/7.10/"). When it's finished, check the [MD5]("http://releases.ubuntu.com/7.10/MD5SUMS") (don't know how? Click [here]("https://help.ubuntu.com/community/HowToMD5SUM")). Then burn the image to a CD using disk utility (more info [here]("https://wiki.ubuntu.com/BurningIsoHowto")).

And, of course, **BACKUP, BACKUP, BACKUP** everything before going any further. I did 3 different backups, but I'm paranoid.

** [SIZE="5"]Doing the install[/SIZE]**
Follow the instructions in the [Macbook Pro wiki]("https://wiki.ubuntu.com/MacBookPro") for installing rEFIt and running bootcamp to resize your partitions. Now put the Alternate CD in the drive and boot from it.

Select the option to install Ubuntu using the text interface.

Refer to the [Macbook Pro wiki]("https://wiki.ubuntu.com/MacBookPro") for the first several steps (i.e. language, keyboard setup, etc.). (Note: the wiki is written for the live CD, so the interface will be different). Now the partition utility will come up. You should see something like this (note that the sizes will be different depending on how much space you left for OS X):
[/LEFT]

```
3.1 kb FREE SPACE
209.7 MB fat 32 EFI System P /media/EFI
11.8 GB hfs+ Apple_HFS
134.2 MB FREE SPACE
107.9 GB UNTITLED 2
3.6 kB FREE SPACE

```

[LEFT]Delete the untitled partition. Now select the free space. You are going to create 3 partitions. The first one should be 200MB, formatted from the beginning. Make the partition type Ext3 (or your preference of a non-encrypted filesystem). Make the mount point /Boot. Leave the other options as defaults. Click on Done. 

The second partition is your primary. Allocate all except 1-3 GB (depending on how big you want your swap) to this partition. Format at the beginning. Now, go to &#8220;use as&#8221; and select &#8220;physical volume for encryption. Keep the remaining options as defaults. _Note:_ Leave erase data as &#8220;No.&#8221; Your data will be overwritten with random data later. Click on Done.

The final partition is swap. Select the remaining free space. Set the options to be identical to those above, i.e. encrypted, other options as default.

Your partition map should look like this (obviously, sizes may vary depending on your setup):
[/LEFT]

```
3.1 kb FREE SPACE
209.7 MB fat 32 EFI System P /media/EFI
11.8 GB hfs+ Apple_HFS
200.0 MB ext3      /BOOT
104.0 GB crypto
3.8    GB  crypto

```

[LEFT]Select &#8220;Configure encrypted volumes.&#8221; Now select your primary encryption volume and configure as follows:[/LEFT]

[IMG]http://dtto.net/photos/ubuntu/crypt1.jpg[/IMG]

[LEFT]Now select &#8220;Erase data on this partition.&#8221; This will write random data throughout your drive. _Note:_ If you're having second thoughts about dual-boot, now would be the time to stop. 

Go outside and run some errands. This will take some time (on my machine it took about 1 min/gig).

Now it will ask for your passphrase. To be strong, your passphrase should be over 20 characters in length, a mixure of upper and lowercase characters, and some symbols. _The passphrase is the weakest link, so don't botch the whole operation by using a bad passphrase._ Write it down someplace safe. If you forget it, your data will not be recoverable.

Now configure your other encrypted volume for swap as follows:

[IMG]http://dtto.net/photos/ubuntu/crypt2.jpg[/IMG]

Select &#8220;Erase data on this partition.&#8221; This one shouldn't take so long.

It will ask for another passphrase. Same rules as above &#8211; make it strong!

You're almost done! Your setup should look something like this now:

[IMG]http://dtto.net/photos/ubuntu/crypt3.jpg[/IMG]

Scroll to the bottom and select &#8220;Finish partitioning and write changes to disk.&#8221;

Now... go outside, stretch your legs, and wait for the install to finish.

** [SIZE="5"]After the install[/SIZE]**

When you startup the first time, you may have the same trouble that I had, which is that grub will not display the prompt asking you for your passphrases. If that happens to you too, just wait about 20 seconds, enter your / passphrase, then wait another 20 seconds and enter your /swap passphrase. 

In my first boot, I was stuck in low-graphics mode (which is a marked difference from installation from the Live CD, in which graphics for my MBP 3.1 worked out-of-the-box). But after installing all of the updates from update-manager, the graphics issue was resolved.

To fix the blank screen at boot:

[/LEFT]
```

sudo gedit /boot/grub/menu.lst

```

[LEFT]Now search for &#8220;additional options&#8221; and add &#8220;no&#8221; in front of &#8220;splash&#8221; so it reads:
[/LEFT]

```

## additional options to use with the default boot option, but not with the 
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet nosplash

```

[LEFT]Now type:[/LEFT]

```

sudo update-grub

```

[LEFT]On reboot, you should now see the screen during bootup so you know when to enter your passphrases.

You'll also want to do all the other fixes and tweaks noted in the other wikis to get all the other bells and whistles working.[/LEFT]

---

### Post by cyberdork33 on 2008-03-28
adding to FAQ

---

### Post by ronocdh on 2008-03-29
Great post. Extremely clear and not at all long-winded. Thanks for adding it, too, cyberdork!

---

### Post by waggygee on 2008-04-27
Im running OSX10.4 on my 2006 MacbookPro... will i need to get bootcamp or anything?

---

### Post by cyberdork33 on 2008-04-28
Please post in the new forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

