---
title: "[Updated] How to create a live USB with or without persistence for mac and pc"
date: 2010-06-07
forum: Apple Hardware Users
---

### Post by Neds Moar Salt on 2010-06-07
This is an updated version of my tutorial.

[SIZE=4][CENTER]Screwed this guide up, now read:
[http://ubuntuforums.org/showthread.php?t=1683062](http://ubuntuforums.org/showthread.php?t=1683062)[/CENTER][/SIZE]

First things first, you will need:
[LIST]
[*]1GB or larger flash drive
[*]rEFIt (Link at the bottom)
[*]A linux installation, virtual machine, or live cd
[*]A Mac OS X installation/installation disk
[*]Administrator permissions
[*]gparted (comes on most linux live cd's)
[*]hfsplus/hfsprogs for hfs+ support in linux
[/LIST]

Alright

Step one (in linux):
[LIST=1]
[*]Format your USB key with an MBR partiton table.
[*]Add an 8MB ext3 partition named "GRUB" for simplicity.
[*]Add a 16MB hfs+ partiton.
[*]Use the rest of your disk as FAT32.
[/LIST]

Step two (also in linux):
[LIST=1]
[*]Mount your ext3 GRUB partiton
[*]Open terminal and do "sudo grub-install --root-directory=<mountpoint> /dev/myusb", of couse replacing <mountpoint> with the mount point and myusb with the correct sdX.
[*]If you get an error saying that there is no bios boot partition (which you shouldn't), open gparted and select the grub partition and select the flag "bios_grub".
[*]Close GParted if it is open and reopen it.
[*]Set the boot flag on the GRUB partition.
[*]Copy all of the contents of your live cd iso or cd (including the hidden folder ".disk") to your fat partiton.
[*]Skip the following steps in the step two if you don't want persistence
[*]In terminal create a zero'd out file called casper-rw in the fat partiton with "dd if=/dev/zero of=/media/LIVE/casper-rw".  Replace the /media/LIVE with the mountpoint again.
[*]Now type "mkfs.ext4 /path/to/casper-rw" and follow the instructions if there are any
[/LIST]

Step three (in mac):
[LIST=1]
[*]Open the rEFIt dmg and copy the "efi" folder to the hfs+ partiton.
[*]Locate the file called "enable.sh" in the efi folder
[*]Open a terminal and type "sudo " and then the path to the enable.sh.  (You can find it by dragging the file into the terminal)
[/LIST]

Step four:
[LIST=1]
[*]Reboot your computer holding the option key
[*]Select rEFIt on your USB drive (If it doesn't appear take it out and plug it back in or boot all the way up and then reboot again)
[*]Select "Linux on HD" that has a picture of a flash drive on it.
[*]You will now be at the GRUB prompt, so type the following: ```
root (hd0,3)
linux /casper/vmlinuz boot=casper persistent
initrd /casper/initrd.lz
boot
``` Of course take out the persistent part if you didn't use the persistence file.
[/LIST]

[COLOR=Red]LINKS[/COLOR]
rEFIt: [http://refit.sourceforge.net/](http://refit.sourceforge.net/)
Ubuntu live cd: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by logandzwon on 2010-09-20
This guide is great, but can someone add instructions to make a usb bootable of ubuntu server?

---

### Post by hydrox24 on 2010-12-30
Thanks for this great tutorial, I will try it soon and add another post when I have completed it.
Just thought I would notify anyone reading this tutorial of two things:

Persistence: "Persistence" in this case means the ability of the live cd to save settings/programs etc to the USB it's running off so that when you, shutdown it doesn't delete all changed settings and added data.
e.g. I install google chrome, and delete sample files off the desktop. With persistence built in, after I restart the OS those changes will still be there Chrome will be installed and working and the sample files will still be non-existent.
Without persistence built in, after restarting, there would'nt even be a trace of chrome and the sample files would be back again.
e.g Persistence is, generally, GOOD.

when Needs more salt says
> 
First things first, you will need:
1GB or larger flash drive
rEFIt (Link at the bottom)
A linux installation, virtual machine, or live cd
A Mac OS X installation/installation disk
Administrator permissions
gparted (comes on most linux live cd's)
hfsplus/hfsprogs for hfs+ support in linux

by hfsplus/hfsprogs he means that you need to have BOTH installed not one or the other.

That's all, hope I helped clear any confusions up.

---

### Post by hydrox24 on 2011-01-07
I get the following error upon entering the command to install grub:
```

alex@Alex-Linux:/media/GRUB$ sudo grub-install --root-directory=</dev/sdb1> /dev/sdb1
bash: /dev/sdb1: Permission denied

```
when I login into root using ```
sudo su
```it spits out the following message:
```

root@Alex-Linux:/media/GRUB# grub-install --root-directory=</media/GRUB> /dev/sdb1
install_device not specified.

```
Any help would be much appreciated...

---

### Post by zasf on 2011-01-07
> **hydrox24 said:**
> I get the following error upon entering the command to install grub:
```

alex@Alex-Linux:/media/GRUB$ sudo grub-install --root-directory=</dev/sdb1> /dev/sdb1
bash: /dev/sdb1: Permission denied

```

<..> is meant to be substituted with your path, for example:

```

alex@Alex-Linux:/media/GRUB$ sudo grub-install --root-directory=/media/sdb1 /dev/sdb

```

assuming that you mounted the grub partition /dev/sdb on the folder /media/sdb1

---

### Post by zasf on 2011-01-07
> **Neds Moar Salt said:**
> Step four:
[LIST=1]
[*]Reboot your computer holding the option key
[*]Select rEFIt on your USB drive (If it doesn't appear take it out and plug it back in or boot all the way up and then reboot again)
[*]Select "Linux on HD" that has a picture of a flash drive on it.
[*]You will now be at the GRUB prompt, so type the following: ```
root (hd0,3)
linux /casper/vmlinuz boot=casper persistent
initrd /casper/initrd.lz
boot
``` Of course take out the persistent part if you didn't use the persistence file.
[/LIST]

See [http://dl.dropbox.com/u/964347/Foto199.jpg](http://dl.dropbox.com/u/964347/Foto199.jpg)

I followed the guide but I'm stuck at step four. I have rEFIt installed on my system and when booting with the usb stick in, it show two new options:
[LIST=1]
[*] Boot Linux from partition 1 (linux logo with orange usb symbol)
[*] Boot legacy OS from (grey squares logo with orange usb symbol)
[/LIST]
neither of the two works. The linux logo brings to a blinking cursor that doesn't load anything.

Are you sure that no steps are missing with grub? How is it possible that grub loads without creating a config (with update-grub)?

When doing the enable.sh command, what is it meant for? Enabling rEFIt on the usb stick?

Thanks for the guide, I really would like to get this running

---

### Post by hydrox24 on 2011-01-07
> **zasf said:**
> <..> is meant to be substituted with your path, for example:

```

alex@Alex-Linux:/media/GRUB$ sudo grub-install --root-directory=/media/sdb1 /dev/sdb

```

assuming that you mounted the grub partition /dev/sdb on the folder /media/sdb1

thanks!

---

### Post by hydrox24 on 2011-01-07
Having similar problem 
This showed up the first time after booting legacy OS and is extremely similar to the screen that came up the first time I booted the Linux bit:
[http://dl.dropbox.com/u/6833827/P1070001.JPG](http://dl.dropbox.com/u/6833827/P1070001.JPG)

the second time I booted linux this shows up for an indefinite amount of time till I force shut down...
[http://dl.dropbox.com/u/6833827/P1070002.JPG](http://dl.dropbox.com/u/6833827/P1070002.JPG)

And I have the same screen as zasf:
> 
See [http://dl.dropbox.com/u/964347/Foto199.jpg](http://dl.dropbox.com/u/964347/Foto199.jpg)


---

### Post by zasf on 2011-01-08
I managed to boot Ubuntu on my MacBookPro7.1 on a usb stick but in a different way. There are parts of this howto that I don't understand (rEFIt for example) and other things that I changed. I'm not 100% happy with this solution yet, so I need to work a bit more on it but will post again soon

---

### Post by speedskater114 on 2011-01-29
I get really far with this tutorial:

I plug in my flash drive, and when I hold down Alt/Option on boot, I'm presented with Macintosh HD and rEFIt. When I click rEFIt, I'm then asked to:
1 - Boot Mac OSX from Macintosh HD
2 - Boot Linux from GRUB
3 - Boot Linux from   

As well as with buttons for the standard EFI Shell, Partitioning Tool, Shut Down, and Restart.

Point is, I can't boot Linux from any of the options. 
When I click option 2, it eventually loads a page that says that Macs don't boot Legacy OSes very well.
When I click option 3, I'm given a small yellow and black square that doesn't go away unless I manually reboot.
I'm glad that rEFIt is showing up from the flash drive at the very least, but I don't know why Linux isn't booting and how to get it working.

Help?!?!?


**EDIT: If I boot this on the latest generation macbook pro, option two eventually brings be to the grub shell, but then tells me that root (hd0,3) doesn't exist...

---

### Post by zasf on 2011-01-31
Sorry I had no time to update you guys on this topic.

I got this working buy installing rEFIt on my macbookpro, formatting a usb stick with a single ext3 partition and bootstrapping maverick into it. 

I actually don't know exactly why it works this way, further investigation is needed but I had really little time to play with it. I also noticed that grub is not able to boot with standard grub config (ie the one that gets autogenerated when doing 'update-grub') but works with
```
root (hd0,1)
linux /vmlinuz root=/dev/sdb1 ro single
initrd /initrd.img
boot
```
I read somewhere that rEFIt or the mac itself swaps some drives at during the boot, therefore the root command refers to the first hard disk, while the linux command to the second

More details this wiki page about [debootstrapping maverick]("http://www.bayesfor.eu/wiki/en/user/matteo_zandi/dev/deboostrap_install"):

If it works for you too or something is not clear, keep posting here

---

### Post by BMacK1311 on 2011-01-31
a

---

### Post by BMacK1311 on 2011-01-31
> **speedskater114 said:**
> I get really far with this tutorial:

I plug in my flash drive, and when I hold down Alt/Option on boot, I'm presented with Macintosh HD and rEFIt. When I click rEFIt, I'm then asked to:
1 - Boot Mac OSX from Macintosh HD
2 - Boot Linux from GRUB
3 - Boot Linux from   

As well as with buttons for the standard EFI Shell, Partitioning Tool, Shut Down, and Restart.

Point is, I can't boot Linux from any of the options. 
When I click option 2, it eventually loads a page that says that Macs don't boot Legacy OSes very well.
When I click option 3, I'm given a small yellow and black square that doesn't go away unless I manually reboot.
I'm glad that rEFIt is showing up from the flash drive at the very least, but I don't know why Linux isn't booting and how to get it working.

Help?!?!?


**EDIT: If I boot this on the latest generation macbook pro, option two eventually brings be to the grub shell, but then tells me that root (hd0,3) doesn't exist...

I'm at this point too. I get the "macbooks do not boot legacy oses very well..

---

### Post by ElevatorHappyFun on 2011-02-02
I ran into a snag. In 'Part 1' step three asks you to make a '16MB hfs+' partition. There is no option for that. Is hfs+ called anything else?  I successfully made the previous '8MB ext3' partition with no problems. I was using the Live CD option of 10.10.

Any thoughts?

Thanks in Advance, 
Russ K.

---

### Post by speedskater114 on 2011-02-03
> **ElevatorHappyFun said:**
> I ran into a snag. In 'Part 1' step three asks you to make a '16MB hfs+' partition. There is no option for that. Is hfs+ called anything else?  I successfully made the previous '8MB ext3' partition with no problems. I was using the Live CD option of 10.10.

Any thoughts?

Thanks in Advance, 
Russ K.


Make sure you've installed the hfsplus, hfsutils, and hfsprogs packages. For the first two, you can install via the terminal (sudo apt-get install hfsprogs or hfsplus), but for the third, do a quick google and download it manually. Then when you open up gparted and try to create a new partition you should have that option.

---

### Post by ipatch on 2011-02-03
Hey, Neds, appreciate the tutorial as I know how tedious it can be to put something like this together.  I have a few [COLOR=Red]*suggestions*[/COLOR] that I will include below in the text for the tutorial that could probably add some clarity.  Also, I did not see anyone reply in this thread stating that the tutorial worked for them, so I am little curious as to how many people got this working.  I worked through this tutorial myself, and I got stuck at the same point that a few people stated earlier in the thread.  When I booted my system holding down the "*option/alt*" key I was presented with the choice of rEFIt loaded on the internal drive on my computer, and the rEFIt loaded on the USB SD card.  When I loaded the rEFIt on the SD card, and then selected the Linux option from the FAT32 partiton I got the following error:
[SIZE=4][B]
Error Message:[/B][/SIZE]
```
The firmware refused to boot from the selected volume.  Note that external hard drives are not well supported by Apple's firmware for legacy OS booting
```**[Updated - by ipatch 3FEB11] How to create a live USB with or without persistence for mac and pc**             

[SIZE=3] Requirments:[/SIZE]
 
[LIST]
[*]1GB or larger flash drive
[*]rEFIt (Link at bottom)
[*]A linux installation, virtual machine, or live cd
[*]A Mac OS X installation/installation disk
[*]Administrator permissions
[*]gparted (comes on most linux live cd's)
[*]hfsplus/hfsprogs for hfs+ support in linux
[/LIST]

[SIZE=3]Step One (perform the following tasks in a Linux environment):
*[SIZE=2]*The following steps are easily performed using a GParted Live CD through Virtualbox.[/SIZE]*
[/SIZE]
[LIST=1]
[*]Format your USB key with an MBR partiton table.
[*]Add an 8MB ext3 partition named "GRUB" for simplicity.
[*]Add a 16MB hfs+ partiton.
[*]Use the rest of your disk as FAT32.
[/LIST]
[SIZE=3] Step Two (Linux environment):[/SIZE]
[LIST=1]
[*]Mount your ext3 GRUB partiton
[*]Open terminal and do "[FONT=Courier New]sudo grub-install --root-directory=<mountpoint> /dev/<myusb>[/FONT]", of couse replacing <mountpoint> with the mount point and myusb with the correct sdX.
[*]If you get an error saying that there is no bios boot partition (which you shouldn't), open gparted and select the grub partition and select the flag "bios_grub".
[*]Close GParted if it is open and reopen it.
[*]Set the boot flag on the GRUB partition.
[*]Copy all of the contents of your live cd iso or cd (including the hidden folder ".disk") to your fat partiton.
[/LIST]
*Optional Steps: Enabling persestance support on Live USB*

[LIST=1]
[*]In terminal create a zero'd out file called casper-rw in the fat partiton with "[FONT=Courier New]dd if=/dev/zero of=/media/LIVE/casper-rw[/FONT]".  Replace the /media/LIVE with the mountpoint again.
[*]Now type "[FONT=Courier New]mkfs.ext4 /path/to/casper-rw[/FONT]" and follow the instructions if there are any
[/LIST]

[SIZE=3]Step Three (Mac OS X):[/SIZE]
[LIST=1]
[*]Open the rEFIt dmg and copy the "efi" folder to the hfs+ partiton.
[*]Locate the file called "enable.sh" in the efi folder
[*]Open a terminal and type "[FONT=Courier New]sudo /path/to/enable.sh[/FONT] " (You can find it by dragging *enable.sh* into the terminal)
[/LIST]
 [SIZE=3]Step Four:[/SIZE]
[LIST=1]
[*]Reboot your computer holding the *option/alt* key.
[*]Select rEFIt on your USB drive (If it doesn't appear take it out and plug it back in or boot all the way up and then reboot again)
[*]Select "*Linux on HD*" that has a picture of a flash drive on it.
[*]You will now be at the GRUB prompt, so type the following: ```
root (hd0,3)
linux /casper/vmlinuz boot=casper persistent
initrd /casper/initrd.lz
boot
``` *Note:* Take out the persistent part if you didn't use the persistence file.
[/LIST]
 [SIZE=3][COLOR=Red]LINKS:[/COLOR][/SIZE]
rEFIt: [http://refit.sourceforge.net/](http://refit.sourceforge.net/)
Ubuntu live cd: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
GParted: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
VirtualBox: [http://www.virtualbox.org/](http://www.virtualbox.org/)
Explanation of mounting a partition: [http://www.tldp.org/HOWTO/html_single/Partition/#mounting](http://www.tldp.org/HOWTO/html_single/Partition/#mounting)

---

### Post by BMacK1311 on 2011-02-03
I was able to test this on 2 more macbooks. The first was a santa rosa (3:1?) and one other was older and one was newer (apologize for not knowing the versions...)

On both I ran into the same problem. I choose refit, then Linux on HD, and when it loads into grub I see:

```
error: no such device: ab0c38dc-f184-4db3-bdcf-649565e779cae.
grub rescue> _
```I figure this is the grub prompt referred to in the last step of the tut, so I enter:

```
root (hd0, 3)
```and it spits back:

```
unknown command 'root'
```I figure something went wrong at the grub install step earlier in the tutorial, but I don't know what.

---

### Post by BMacK1311 on 2011-02-03
Success!

I had installed GRUB at a non-existent mount point. I modified the tutorial to show what I did, but this means that the tutorial was 100% correct and works - I interpreted it incorrectly. Now to test on my other 2 test MacBook Pro's. Thanks Neds.

> **Neds Moar Salt said:**
> This is an updated version of my tutorial.

First things first, you will need:
[LIST]
[*]1GB or larger flash drive
[*]rEFIt (Link at the bottom)
[*]A linux installation, virtual machine, or live cd
[*]A Mac OS X installation/installation disk
[*]Administrator permissions
[*]gparted (comes on most linux live cd's)
[*]hfsplus/hfsprogs for hfs+ support in linux
[/LIST]

Alright

Step one (in linux):
[LIST=1]
[*]Format your USB key with an MBR partiton table.
[*]Add an 8MB ext3 partition named "GRUB" for simplicity.
[*]Add a 16MB hfs+ partiton.
[*]Use the rest of your disk as FAT32.
[/LIST]

Step two (also in linux):
[LIST=1]
[*]Mount your ext3 GRUB partiton
[*]Open terminal and do "sudo grub-install --root-directory=/media/GRUB /dev/sdb" - Modification by BMacK1311: the tut says to name the partition GRUB, making the mount point /media/GRUB at /dev/sdb
[*]If you get an error saying that there is no bios boot partition (which you shouldn't), open gparted and select the grub partition and select the flag "bios_grub".
[*]Close GParted if it is open and reopen it.
[*]Set the boot flag on the GRUB partition.
[*]Copy all of the contents of your live cd iso or cd (including the hidden folder ".disk") to your fat partiton.
[*]Skip the following steps in the step two if you don't want persistence
[*]In terminal create a zero'd out file called casper-rw in the fat partiton with "dd if=/dev/zero of=/media/LIVE/casper-rw".  Replace the /media/LIVE with the mountpoint again.
[*]Now type "mkfs.ext4 /path/to/casper-rw" and follow the instructions if there are any
[/LIST]

Step three (in mac):
[LIST=1]
[*]Open the rEFIt dmg and copy the "efi" folder to the hfs+ partiton.
[*]Locate the file called "enable.sh" in the efi folder
[*]Open a terminal and type "sudo " and then the path to the enable.sh.  (You can find it by dragging the file into the terminal)
[/LIST]

Step four:
[LIST=1]
[*]Reboot your computer holding the option key
[*]Select rEFIt on your USB drive (If it doesn't appear take it out and plug it back in or boot all the way up and then reboot again)
[*]Select "Linux on HD" that has a picture of a flash drive on it.
[*]You will now be at the GRUB prompt, so type the following: ```
root (hd0,3)
linux /casper/vmlinuz boot=casper persistent
initrd /casper/initrd.lz
boot
``` Of course take out the persistent part if you didn't use the persistence file.
[/LIST]

[COLOR=Red]LINKS[/COLOR]
rEFIt: [http://refit.sourceforge.net/](http://refit.sourceforge.net/)
Ubuntu live cd: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by ipatch on 2011-02-03
> **BMacK1311 said:**
> I was able to test this on 2 more macbooks. The first was a santa rosa (3:1?) and one other was older and one was newer (apologize for not knowing 

The [Santa Rosa ]("http://www.everymac.com/ultimate-mac-lookup/?search_keywords=MacBookPro3,1")a la MacBook Pro 3,1 is the same machine I tried performing this tutorial on with no luck.

Here is the output after I installed Grub to the GRUB partition of the SD card.  Do you see any issues with this install?

[IMG]http://ipatch.penguinmilitia.net/wp-content/uploads/2011/02/sudo-grubInstall.png[/IMG]

---

### Post by BMacK1311 on 2011-02-04
I'm probably not qualified to answer that question, but our Apple guy says this method probably will not work for the 3,1. I am now trying to use the grub efi loader for it. If that doesn't work, I'm going to try elilo. Grub testing on macbooks can be found at [Testing on MacBook Pro]("http://grub.enbug.org/TestingOnMacbook"). I'm trying to follow the guide but I'm very new to this and I'm not sure which text to replace with which paths or mount points - the same problem I ran into with this tutorial.

---

### Post by ipatch on 2011-02-04
> **BMacK1311 said:**
> I'm probably not qualified to answer that question, but our Apple guy says this method probably will not work for the 3,1. I am now trying to use the grub efi loader for it. If that doesn't work, I'm going to try elilo. Grub testing on macbooks can be found at [Testing on MacBook Pro]("http://grub.enbug.org/TestingOnMacbook"). I'm trying to follow the guide but I'm very new to this and I'm not sure which text to replace with which paths or mount points - the same problem I ran into with this tutorial.

Hey, this is where I am currently at, [[COLOR=Blue]thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1681729")

---

### Post by speedskater114 on 2011-02-05
> **Neds Moar Salt said:**
> 

6. Copy all of the contents of your live cd iso or cd (including the hidden folder ".disk") to your fat partiton.
7. Skip the following steps in the step two if you don't want persistence
8. In terminal create a zero'd out file called casper-rw in the fat partiton with "dd if=/dev/zero of=/media/LIVE/casper-rw".  Replace the /media/LIVE with the mountpoint again.
9. Now type "mkfs.ext4 /path/to/casper-rw" and follow the instructions if there are any

You can also use ***Startup Disk Creator*** found under System->Administration to create this.

And yes, thank you Neds.

---

### Post by Neds Moar Salt on 2011-02-07
Hey everybody, my CORRECT guide [http://ubuntuforums.org/showthread.php?t=1683062](http://ubuntuforums.org/showthread.php?t=1683062)

---

### Post by ipatch on 2011-02-09
> **Neds Moar Salt said:**
> Hey everybody, my CORRECT guide [http://ubuntuforums.org/showthread.php?t=1683062](http://ubuntuforums.org/showthread.php?t=1683062)

Dude, no offense or anything, but why start/create an entirely new thread on this subject when you could edit/refine the one you have already created?

---

### Post by pindar on 2011-02-21
I spent a Sunday afternoon on this and am reporting what I found out; maybe it's interesting to someone, maybe it's just so I'll remember myself in 6 months... The problem seems to be that different apple hardware reacts in different, totally unpredictable ways, and what works in constellation A doesn't work in constellation B. Moreover, what works with distribution/version X will not necessarily work with distribution/version Y. That's why there are dozens of threads and howtos, all with a small number of "hooray, it works" and a large number of "doesn't work for me" attached... My hardware is a macbook 1,1, and I'm able to boot it from a usb stick with a ubuntu iso on it. Here's what worked for me (my macbook already has refit installed):

[LIST=1]
[*]Partitioned the stick in gparted with a gpt partition table. 2 partitions: 1 as hfsplus, 2 as fat32. 
[*]Mount partition 1, create directory EFI/boot (capitalization might be important).
[*]Build grub 1.99rc1 according to instructions on [this website]("http://grub.enbug.org/TestingOnMacbook").
[*](This was a tricky part, it took me a while to find the right magical incantation.) From within this new grub2, build a grub.efi with this command: ../grub-mkimage -O $EFI_ARCH-efi -d . -o grub.efi -p "" part_gpt part_apple part_msdos hfsplus fat ext2 ls normal chain boot configfile ohci loopback linux multiboot search iso9660 (some of these mods may be unnecessary, but some combinations wouldn't boot, so I won't touch these again...)
[*]Copy the resulting grub.efi to partition 1 EFI/boot directory.
[*]Mount partition 2, copy a ubuntu iso to it under name ubuntu.iso.
[/LIST]
After booting, refit would recognize the usb stick and list it as bootable. After booting off of it, grub would kick in. I haven't been able to write a grub.cfg that would be able to boot directly, but could boot from the grub command line with these commands:
```

loopback loop (hd1,msdos2)/ubuntu.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu.iso noeject noprompt
initrd (loop)casper/initrd.lz
boot

```
The last two commands before "boot" take a few seconds to complete. Booting complains about something "no suitable mod found, booting however," and boots to a functioning desktop - sort of. This works with linux mint 10 (based on ubuntu 10.10). It does not work with a natty alpha iso - go figure.

I haven't yet tried any persistence; this was important for me because the cd drive in the macbook doesn't work any more, so I just needed a method to install ubuntu to it. But I'm very happy that I got this working, at least I can install a new version of linux on this baby.

---

### Post by indifference on 2011-03-27
Hello,

I was able to reach the "no suitable mod found, booting however" but I didn't do much more.

> **pindar said:**
> I spent a Sunday afternoon on this and am reporting what I found out; maybe it's interesting to someone, maybe it's just so I'll remember myself in 6 months... The problem seems to be that different apple hardware reacts in different, totally unpredictable ways, and what works in constellation A doesn't work in constellation B. Moreover, what works with distribution/version X will not necessarily work with distribution/version Y. That's why there are dozens of threads and howtos, all with a small number of "hooray, it works" and a large number of "doesn't work for me" attached... My hardware is a macbook 1,1, and I'm able to boot it from a usb stick with a ubuntu iso on it. Here's what worked for me (my macbook already has refit installed):

[LIST=1]
[*]Partitioned the stick in gparted with a gpt partition table. 2 partitions: 1 as hfsplus, 2 as fat32. 
[*]Mount partition 1, create directory EFI/boot (capitalization might be important).
[*]Build grub 1.99rc1 according to instructions on [this website]("http://grub.enbug.org/TestingOnMacbook").
[*](This was a tricky part, it took me a while to find the right magical incantation.) From within this new grub2, build a grub.efi with this command: ../grub-mkimage -O $EFI_ARCH-efi -d . -o grub.efi -p "" part_gpt part_apple part_msdos hfsplus fat ext2 ls normal chain boot configfile ohci loopback linux multiboot search iso9660 (some of these mods may be unnecessary, but some combinations wouldn't boot, so I won't touch these again...)
[*]Copy the resulting grub.efi to partition 1 EFI/boot directory.
[*]Mount partition 2, copy a ubuntu iso to it under name ubuntu.iso.
[/LIST]
After booting, refit would recognize the usb stick and list it as bootable. After booting off of it, grub would kick in. I haven't been able to write a grub.cfg that would be able to boot directly, but could boot from the grub command line with these commands:
```

loopback loop (hd1,msdos2)/ubuntu.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu.iso noeject noprompt
initrd (loop)casper/initrd.lz
boot

```
The last two commands before "boot" take a few seconds to complete. Booting complains about something "no suitable mod found, booting however," and boots to a functioning desktop - sort of. This works with linux mint 10 (based on ubuntu 10.10). It does not work with a natty alpha iso - go figure.

I haven't yet tried any persistence; this was important for me because the cd drive in the macbook doesn't work any more, so I just needed a method to install ubuntu to it. But I'm very happy that I got this working, at least I can install a new version of linux on this baby.

---

### Post by janna109 on 2011-06-10
Wow, I got this working on a macbook pro 7,1 (already had grub and refit installed on this laptop; not sure if that made a difference). I pretty much just followed the original tutorial, except I used root=(hd1,2) instead of root=(hd0,3).

Thanks, Neds Moar Salt!

---

