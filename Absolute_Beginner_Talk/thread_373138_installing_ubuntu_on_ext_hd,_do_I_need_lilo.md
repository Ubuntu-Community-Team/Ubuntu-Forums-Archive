---
title: "installing ubuntu on ext hd, do I need lilo"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by makko on 2007-02-28
So, I have come a long way tonight. I partitioned 20GB for linux from my ext 320GBHD along with a 512 swap partition.
Next I started installing ubunto to the 20GB partition..all went okay. I then proceeded to boot the USB drive but the computer said no boot sector found then it proceeded to boot windows. I have just looked at the disk under the management section in windows and it says the 20gb partition is 100% free? what does that mean?

Just to recap:
Laptop HD has Windows XP Home No partitions.
EXT 320GB HD has 20GB Partition (where I want to install ubuntu) and 512 swap partition.

What do I need so that I can boot whichever one I want? Do I absolutely need to install a boot loader such as lilo.Is it possible to auto boot windows then boot into linux/get a boot menu by holding down a key?

Thanks...

---

### Post by confused57 on 2007-03-01
> **makko said:**
> So, I have come a long way tonight. I partitioned 20GB for linux from my ext 320GBHD along with a 512 swap partition.
Next I started installing ubunto to the 20GB partition..all went okay. I then proceeded to boot the USB drive but the computer said no boot sector found then it proceeded to boot windows. I have just looked at the disk under the management section in windows and it says the 20gb partition is 100% free? what does that mean?

Just to recap:
Laptop HD has Windows XP Home No partitions.
EXT 320GB HD has 20GB Partition (where I want to install ubuntu) and 512 swap partition.

What do I need so that I can boot whichever one I want? Do I absolutely need to install a boot loader such as lilo.Is it possible to auto boot windows then boot into linux/get a boot menu by holding down a key?

Thanks...
Windows doesn't recognize ext3 partitions, so disk management would recognize it as free space...be thankful grub wasn't installed to your Windows mbr.
You could try reinstalling grub to the external hd mbr, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
make sure to have your setup(hard drive boot order in bios,etc) exactly the way it was when you installed Ubuntu, before trying to reinstall grub.
e.g. if "find /boot/grub/stage1" returns
root (hd1,0), then enter
root (hd1,0)
setup (hd1)
quit

or if it returns
root (hd0,0), then
setup (hd0)

in other words, (**hdx**,y), **hdx** is how grub sees your external hd

Once you've installed grub to the external hd mbr, make sure bios is set to boot the external hd before the internal hd...if you get a grub menu, then there's a chance you can get Ubuntu working.

---

### Post by makko on 2007-03-01
Ooops I changed around the boot order so that it would boot up the hd first after installation..
Is it not definite that I can run ubuntu fromthe ext HD?
Does it make a difference that before the installation when setting up the partitions in GParted I never set flag on the install partition to boot. I have just done that now..

---

### Post by confused57 on 2007-03-01
> **makko said:**
> Ooops I changed around the boot order so that it would boot up the hd first after installation..
Is it not definite that I can run ubuntu fromthe ext HD?
Does it make a difference that before the installation when setting up the partitions in GParted I never set flag on the install partition to boot. I have just done that now..

Here's a couple of threads of people who have had success installing Ubuntu to an external hd:
[http://www.ubuntuforums.org/search.php?searchid=15432289](http://www.ubuntuforums.org/search.php?searchid=15432289)

When you install Ubuntu to an external hard drive, it's important that you set the external hard drive in bios as your first hard drive booted to(ahead of the internal hd)...and ensure that grub is installed to the external hd mbr(not the internal hd).  If grub is installed to the internal hd mbr, then you'd have to have your external hd connected in order to boot your computer, which you probably don't want...that's why I said it's good that grub wasn't installed to the Windows drive mbr.  
Yes, you should set the root partition as bootable when installing Ubuntu.   It would probably be easier to reinstall Ubuntu as I mentioned in this thread...or try to reinstall grub to the external hd mbr, as I described in my other reply.  I can't guarantee you'll be able to get Ubuntu installed & running on your external hard drive, but it shouldn't hurt anything to try.

You might want to download a copy of the Super Grub Disk(500 kb download):
it's a hand utility to have, if you need to restore your Windows mbr or reinstall grub & it can boot Windows & Linux...I'd burn a copy to cd(or floppy), before you try reinstalling Ubuntu or reinstalling grub, just in case something goes wrong that you're not able to boot either Windows or Ubuntu.

---

### Post by makko on 2007-03-01
Ok, I can't get my head around this.. 
I need to install GRUB to the MBR of the ext hd. How do I do this? I've googled and all the guides seem to be different variations of what I need to do..
I will try installing grub to the ext hd MBR from the live cd but first I will need a little explanation on all this  (hd1,0) hda/dev business..basically how does linux display drives??

Also, Would it be possible for me to not use a bootloader just have the MBR of the ext HD boot into linux automatically from selecting that drive in the bios because windows on another HD?

---

### Post by confused57 on 2007-03-01
> **makko said:**
> Ok, I can't get my head around this.. 
I need to install GRUB to the MBR of the ext hd. How do I do this? I've googled and all the guides seem to be different variations of what I need to do..
I will try installing grub to the ext hd MBR from the live cd but first I will need a little explanation on all this  (hd1,0) hda/dev business..basically how does linux display drives??
Linux(the kernel) recognizes your hard drives according to which controller they are connected to...for example, your root in the kernel could possibly be root=/dev/sda1 for your external hd, and your internal hd's will be  /dev/hda(or /dev/sda if SATA, if you have SATA, your external hd may be other than sda).
It's how grub recognizes your hard drives that is important in being able to boot your system.  The first booted hard drive(at install) is recognized as hd0, the second hd1, etc.
I think I've mentioned this, but if your internal drive is set in bios as the first hard drive in the boot sequence, it would be recognized as hd0 by grub...you don't want to install grub to your internal hd, so before installing(booting up the Ubuntu install cd), select your external hd as the first hard drive booted in bios...this "should" result in grub seeing your external hd as hd0 and will install grub to it's mbr...this way, if you disconnect your external hd, you can still boot to Windows, using Windows mbr...

---

### Post by makko on 2007-03-01
I am now in ubuntu live cd..
I just typed this into the grub promt: find /boot/grub/stage1
 and got : (hd1,1)
What exactly does this mean?

Also when I try and boot the usb drive it says there is no boot sector.. is this differant to MBR and even if grub is installed to the MBR will it not run because of there being no boot sector??

---

### Post by confused57 on 2007-03-01
> **makko said:**
> I am now in ubuntu live cd..
I just typed this into the grub promt: find /boot/grub/stage1
 and got : (hd1,1)
What exactly does this mean?

Also when I try and boot the usb drive it says there is no boot sector.. is this differant to MBR and even if grub is installed to the MBR will it not run because of there being no boot sector??

This might work, no guarantees...in bios, set your internal hard drive as first booted hard drive & your external hd second(the way you had it when you installed Ubuntu?).  Boot up the live cd, open a terminal:
```
sudo grub
find /boot/grub/stage1
```
which should return: root (hd1,1)
enter:
```
root (hd1,1)
setup (hd1)
```
hopefully, grub will be successfully installed to your external hd mbr
```
quit
```
to exit the grub prompt

Restart your computer from the live cd, remove live cd...go into bios and select your external hard drive to boot to first, you "should" get a grub menu.
In the grub menu, highlight your Ubuntu entry, press "e" to edit, then change root from (hd1,1) to **root (hd0,1)**, then press "b" to boot...see if this boots Ubuntu.

---

### Post by makko on 2007-03-01
ok I did all that with success right up to the point where I am booting from the external HD. I got the "NO BOOT SECTOR" error again. Is this something else that is missing? How do I add it?

---

### Post by confused57 on 2007-03-01
> **makko said:**
> ok I did all that with success right up to the point where I am booting from the external HD. I got the "NO BOOT SECTOR" error again. Is this something else that is missing? How do I add it?
For some reason, grub seems to be refusing to install to your external hard drive...the only other alternative I can offer is to try to reinstall Ubuntu to your external hd...make sure that your external hd is selected in bios as the first boot hard drive, before you boot up the live cd to install.
   You might want to glance through the explanations of  grub, mbr, mounting, etc on this site:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I can't think of anything else you might try, except to reinstall.

You might want to burn a copy of the Super Grub Disk, before you try reinstalling:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it can boot Windows or Linux & restore Windows mbr or Linux grub

---

### Post by makko on 2007-03-01
I've just tried all that confused thanks, but nothing has worked.
I have also tried nearly every function on SuperGrubDisk but the ext hard drive just won't boot.. something a bout a missing bootsector..

I am oficcially giving up.. thanks for all the help.

---

### Post by confused57 on 2007-03-01
> **makko said:**
> I've just tried all that confused thanks, but nothing has worked.
I have also tried nearly every function on SuperGrubDisk but the ext hard drive just won't boot.. something a bout a missing bootsector..

I am oficcially giving up.. thanks for all the help.
Sorry you couldn't get anything to work...you could try installing grub to the root partition on the external hd and trying a GAG boot floppy(or cd)...see the link in my last reply(Hermanzone)...or maybe try it later on, sometime in the future...GAG requires grub to be installed to the root partition...may not even work.

To install grub to the root partition, using the live cd:
sudo grub
find /boot/grub/stage1
root (hdx,y,)
setup (hdx,y)
quit

Here's someone who was able to get Ubuntu working on their external hd, using the alternate install cd:
[http://www.ubuntuforums.org/showthread.php?t=372962](http://www.ubuntuforums.org/showthread.php?t=372962)

---

### Post by lha on 2007-03-11
> **makko said:**
> I've just tried all that confused thanks, but nothing has worked.
I have also tried nearly every function on SuperGrubDisk but the ext hard drive just won't boot.. something a bout a missing bootsector..

I am oficcially giving up.. thanks for all the help.

In case you haven't completely given up, you could use [Ext2 Installable File System]("http://www.fs-driver.org/") or [explore2fs]("http://www.chrysocome.net/explore2fs") to take a look inside your Ubuntu partition. (Assuming you used ext3, the default option. Similar tools exist for some other filesystems, too.) Since you couldn't install grub on your external hd, why not install it on your internal hd? MBR isn't a good choice, but you can load GRUB for NT from Windows' boot loader. GRUB for NT can then load a kernel and boot Ubuntu. (In theory, at least.) [This great tutorial]("http://marc.herbert.free.fr/linux/win2linstall.html#grub-for-nt") has some instructions for you and a link to site from which you can download GRUB for NT. Use Ext2IFS or explore2fs to find out the correct options for menu.lst.

---

