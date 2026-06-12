---
title: "Xbuntu 6.06.1 not booting on Wallstreet G3"
date: 2006-11-12
forum: Apple PPC Users
---

### Post by john8520 on 2006-11-12
I recently installed Debian on my PB Wallstreet. Almost everything worked fine, except sound, sleep, and power management. So, I have decided to give Xbuntu a try, but every time I boot, it, well, doesn't boot.

Here is what I have - Wallstreet II, 14.1", 233MHz G3 w/ L2 cache, 384mb RAM, and a 20gb HDD (7gb for mac os, the rest for xbuntu). I'm using BootX v1.2.2, and Xbuntu 6.06.1. I have dragged the kernel (vmlinux) from Xbuntu_PowerPC_dapper/casper/powerpc to /System Folder/Linux Kernels. I have dragged the ramdisk (intrid.gz) from the same location to the root level of the mac partition. 

In BootX, I have the kernel set on "vmlinux", the ramdisk set on "intrid.gz", the ramdisk size is 8192, and my kernel arguments are "video=atyfb:vmode14:,cmode:24". No other options are set.

I then click "Save to prefs" (well, only once, the first time) and then click "Linux". The mac os appears to freeze for a second, then goes to a screen with white one black, and rolls by a bunch of info. Then it stops, and the last few lines are info are:

```

Nov 11 23:54:10 (none) _0_ Engine: signal_handler: ***
Nov 11 23:54:10 (none) _0_ Engine: signal_handler: *** Signal: Aborted
Nov 11 23:54:10 (none) _0_ Engine: signal_handler: ***
Aborted
  No volume groups found
Done.
Begin: Waiting for root file system... ...

```

It seems to just hang there for about three minutes, then puts out (directly below the code I posted above)

```

ALERT! Does not exist. Dropping to a shell!


BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built in shell (ash)
Enter 'Help' for a list of built in-commands.

/bin/sh: can;t access tty: job control turned off

```

Then it just leaves me with a root (#) prompt.

I'm sorry if I left anything out, I hope I was detailed enough.

Any ideas on how to get this thing off the ground? I'd really like to try Xbuntu, it looks so cool. Debian and YDL3 are just too much of a pain to use.

---

### Post by Brian Smith on 2006-11-12
I think that the Live CD would run super slowly, and that the installation process might be hampered by running it from the CD.  6.10 has been released, why not take the additional excuse to download a new .iso or other Xubuntu 6.10 image?  Choose the "Alternate Install," which is this link: [http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/xubuntu-6.10-alternate-powerpc.iso](http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/xubuntu-6.10-alternate-powerpc.iso)

What's happening in your current process, I think, is that you are missing the specification of the root partition to the kernel.  You could try using something like root=/dev/hdc(or replace hdc with the proper device for your hardware configuration) 

I've just completed, well almost, a G3 Beige Xubuntu installation.... only to find that the hd I've installed to does not have enough room on it to finish booting!  ARRRRRGH!  Keep at it, and I will too, it's very promising to continue to use some modern apps with these old machines at a reasonably snappy pace!

---

### Post by john8520 on 2006-11-12
Alright, I'm downloading now. Looks like it'll be done in ~30 minutes. I didn't realize that what I was getting was a LiveCD, otherwise it would hev been a major pain to work with, thanks for linking me to the alternate install.

When you say "...you are missing the specification of the root partition to the kernel" do you mean that the ramdisk or whatever doesn't automaticly find the CD drive to get the installer files? What is /dev/hdc? The CD drive? 


Also, I plan on installing Xbuntu on my beige as well, if it goes well on the wallstreet, specs are 366MHZ G3, 256mb RAM, 20GB HD, Rage 128 pro. Only problem is, its not assembled at the moment. :roll:

---

### Post by john8520 on 2006-11-12
Hooray! I just got the CD burned (at 2x!) and the wallstreet booted right up off it! (well, off the ramdisk anyways) :D

It is installing now, I'll report back when its done.

---

### Post by john8520 on 2006-11-12
Well, I got it all installed, and I must say, I'm very happy with it. Its quite lightweight, and Boots in around 30-40 seconds (Not bad for a 233MHz computer!) So far it seems like everything is supported pretty well. Sound doesn't work though, and when I tried to wake it from sleep, it turned off... :? Also, the battery monitor doesn't seem to work, and it doesn't know my IP address, though I am clearly connected to the internet.

By the way, I'm using the 2.6.17 kernel that I got from here - [http://www.ppckernel.org/kernel.php?id=74](http://www.ppckernel.org/kernel.php?id=74)

---

### Post by Brian Smith on 2006-11-12
Nice going!
I've been waiting to post a response for you until I had my G3 up...  I'm not quite there yet:
[http://www.ubuntuforums.org/showthread.php?t=298371](http://www.ubuntuforums.org/showthread.php?t=298371)

Did you install xubuntu 6.06 server, then install xubuntu-desktop with aptitude?

Have fun with it.

---

### Post by john8520 on 2006-11-12
All I did was burn the CD you linked too, then boot from it, run through the install, and here I am. Very straightforward.

Right now I'm working on overclocking my 366MHZ Beige to ~450, then I think it will be a good cantidate for this.

---

### Post by Brian Smith on 2006-11-12
> **john8520 said:**
> All I did was burn the CD you linked too, then boot from it, run through the install, and here I am. Very straightforward.

Right now I'm working on overclocking my 366MHZ Beige to ~450, then I think it will be a good cantidate for this.

Well, after a good bit more effort, I do have it running.
In the end, I used a different monitor that shared more modes with the display adapter, and then had to do a sudo dpkg-reconfigure on the xorg to get my X up, but it did work and I learned a few things.  

Let me know how the overclocking goes, I would probably try that with mine, too.  Wouldn't it be nice to be able to monitor a temperature or two?  Let me know if you find a good way to do that!

If you need help with your Beige, let me know!

-Brian

---

### Post by john8520 on 2006-11-12
Congrats on getting it running!

Right now overclocking is being a bit of a pain, because this board is so stubborn with CPU speeds. I hope to get it to an 83MHz bus at 455 or 420MHz. As for temp monitoring, you can always get 3rd part sensors + monitors for relatively cheap.

---

### Post by krustybaguette on 2007-12-02
> **john8520 said:**
> Alright, I'm downloading now. Looks like it'll be done in ~30 minutes. I didn't realize that what I was getting was a LiveCD, otherwise it would hev been a major pain to work with, thanks for linking me to the alternate install.

My Wallstreeet is Powerbook G3 (233Mhz w/ 0 Cache) 320 MB RAM, 18 gb Toshiba hard drive 12" screen limited to 800x600 resolution in Mac OS 9.2.2

Have been trying to install Ubuntu 5.10 Breezy, 6.10 Edgy, and 7.04 Feisty Fawn. Just noticed that of the three iso's that I've downloaded and burned to CD's only the 5.10 is designated ubunto (vsn)install-powerpc.iso The Other's are desktop-powerpc.iso  Could this explain part of my problem getting ANY of them to install? 

> **john8520 said:**
> 
When you say "...you are missing the specification of the root partition to the kernel" do you mean that the ramdisk or whatever doesn't automaticly find the CD drive to get the installer files? What is /dev/hdc? The CD drive? 

I've been getting the  'busybox can't access tty'  error and tried guessing root=/dev/hdb using the Feisty Fawn disc. Got /dev/hdb does not exist, then the 'can't find tty' error again
> **john8520 said:**
> 
Also, I plan on installing Xbuntu on my beige as well, if it goes well on the wallstreet, specs are 366MHZ G3, 256mb RAM, 20GB HD, Rage 128 pro. Only problem is, its not assembled at the moment. :roll:
Final questions, for now...Do I need to download a different iso designated 'install-powerpc.iso' in order to install a later version of Ubuntu? I have 5.10 Breezy Badger with 'install-powerpc.iso' burnt to a CD. It has led to the 'can't find tty' error as well.  

What is the solution to the 'can't find tty' error?

Note: I couldn't make out the white on black stuff at all until I selected "no video driver" in BootX

---

### Post by krustybaguette on 2007-12-04
Well I've gotten past my initial trouble getting into the installer. I've tried three different distros, but have been concentrating on Feisty Fawn using the Alternative Install CD, burnt from downloaded .iso

To recap: My Wallstreet is the 233 cacheless Mainstreet model. I've got an 18 gb Toshiba hard drive and 320 MB of RAM installed. My OS 9.2.2 installation is on an HFS+ partition. From what I've been reading I probably will make my next attempt using HFS. 

Once I got the installer to start it got so late that I went to bed and let it finish doing its thing. When I awoke the screen about no bootloader can be installed was waiting for me. Anyway I messed up dropping out to the Busybox console and eventually gave up and went to work.

Last night I decided to try again and using the instructions "[[COLOR="Blue"]Ubuntu Breezy Badger on Old World G3 Mac PPC[/COLOR]]("https://help.ubuntu.com/community/Installation/OldWorldMacs")" I thought I'd gotten it ready for "first boot" Instead I ended up with a kernel panic and 'provide proper /dev/specification'  I should add that when I ran the installer for the second time the old installation was still on the hard drive so my partitioning was a bit strange and I ended up with an ext2 partition, and ext3 partition, and a swap. After a few aborted attempts to copy the real vmlinux and initrd.img files I thought I had succeeded but I couldn't tell whether my installation was on hda11 or hda12.

Also. I had previously installed Yellow Dog Linux on some PPC 5400 and 5500 all-in-ones and remembered their [[COLOR="Navy"]instructions about installation and partitioning[/COLOR]]("http://www.terrasoftsolutions.com/support/installation/archives/guide2.3.shtml"), so I dragged them out and created about an 11gb unallocated partition for Ubuntu and about 7gb for OS9. That partitioning seemed to eliminate the problem of being unable to get the installer to even start up, but when I tried to run the installer for the second time last night (without reformatting and partitioning) I ended up choosing the option to resize the existing partition, thus the mess I ended up with.

Now I think I should start over again, using the same 11gb unallocated partition for Ubuntu, and the remaining 7gb for MacOS9. On my first attempt with that configuration the installer said I didn't have enough space to "use largest remaining partition" and automatic partitioning. So I used the manual partitioning, and ended up not being able to choose the size of my swap partition, but I did at least have one. 

Well I've rambled on long enough (or too long). I hope someone can find something in this that will point me in the right direction as I really want to get this Wallstreet up and running soon. TIA

Krusty Baguette typing from Podunk, MA

---

