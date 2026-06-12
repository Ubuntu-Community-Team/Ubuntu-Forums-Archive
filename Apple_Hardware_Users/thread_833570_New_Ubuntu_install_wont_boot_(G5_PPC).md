---
title: "New Ubuntu install wont boot (G5 PPC)"
date: 2008-06-18
forum: Apple Hardware Users
---

### Post by AluKa on 2008-06-18
Hi everyone :)
  I'm new to linux, and I've been trolling these boards for a week trying to find a solution to my problem with no success.

Anyway, here's what's going on...

I have a PPC G5, and I've managed to install 8.04 from the live cd in a single boot environment.  When I turn the machine on, it displays Yaboot stage 1 with the options for linux and CD.  When I select linux the screen goes black for a second, then it displays the Yaboot stage 1 message with the linux and cd options again.  I have no idea how to proceed :(

The output of sudo fdisk -l /dev/sda is
/dev/sda
        #                    type name                  length   base      ( size )  system
/dev/sda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/sda2         Apple_Bootstrap untitled                1954 @ 64        (977.0k)  NewWorld bootblock
/dev/sda3         Apple_UNIX_SVR2 untitled           308427735 @ 2018      (147.1G)  Linux native
/dev/sda4         Apple_UNIX_SVR2 swap                11743303 @ 308429753 (  5.6G)  Linux swap

Block size=512, Number of Blocks=320173056
DeviceType=0x0, DeviceId=0x0


and I've attached my yaboot.conf (as yaboot.txt).

Thank you!

---

### Post by stream303 on 2008-06-19
Thanks for posting that yaboot file.  There is no device listed, so that is why it is failing - we can find it manually.  This usually happens when installing to an external firewire drive, or on some models with dual hd controllers.

Which model do you have and are you installing to an internal or firewire drive?

[http://www.everymac.com/](http://www.everymac.com/)

To save a bit of time to find your openfirmware path, you can issue this from the commandline:

```
ofpath /dev/sda
or
find /proc/device-tree/ -name "*disk*"
```

To help out, my device line in /etc/yaboot.conf looks like this, although yours will probably be different:

```
device=/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:
```
Note that the line above has a colon manually added to the end.

Once you edit the /etc/yaboot.conf, you need to make the system aware of the change:

```
sudo ybin -v -C /etc/yaboot.conf
```

You *might* need to issue
```
sudo mkofboot -v -C /etc/yaboot.conf
```

AND just to top things off, there is the possibility of having to manually specify a UUID in your /etc/fstab, and possibly re-edit your yaboot.conf again for video purposes.  Let's see how this goes first.

---

### Post by AluKa on 2008-06-19
Ok, here's what I've got so far....

This install is on the primary (only)SATA drive in the machine.  

I'm pretty sure that it's the Apple Power Macintosh G5 2.0 DP (PCI-X)(M9032LL/A) model.

When I issued the ofpath /dev/sda command the first time I saw /disk@0:

I ran the find /proc/device-tree/ -name "*disk*" command and received a list of several devices such as

/proc/device-tree/ht@0, f2000000/pci@7/k2-sata-root@c/k2-sata@1/disk@0
and

/proc/device-tree/ht@0, f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0

I changed the device line in my yaboot.conf to the k2-sata@0 value and ran the ybin and mkofboot commands.

Rebooted and no luck... same symptoms.  I checked the ofpath /dev/sda again and it still says /disk@0:

Thank you for your help :)

---

### Post by stream303 on 2008-06-19
> **AluKa said:**
> This install is on the primary (only)SATA drive in the machine.  

I'm pretty sure that it's the Apple Power Macintosh G5 2.0 DP (PCI-X)(M9032LL/A) model.

Great!  It looks like that model is the lower-end model and while it may support two drives, it only has one hd-controller.  This actually should make things easier.

> device=/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0**:**

Try the procedure again, and don't forget to add the trailing colon.

**UPDATE:** I noticed that for some reason the original quote here included a space between the comma and and the f.  Make sure you don't have any spaces between ht@0,f2000000 ... fixed in these quotes now...

If that doesn't work, try the other line and again follow up with the ybin and/or mkofboot command:

> device=/ht@0,f2000000/pci@7/k2-sata-root@c/k2-**sata@1**/disk@0**:**

If neither of these work, you might try physically moving the drive to the other position, (and maybe changing drive jumpers from CS to Slave if necessary) and either doing a reinstall, or trying both these lines again with a followup ybin / mkofboot.

Ah, question:  Is this drive oem, or a recent replacement?

Some of the powermac guys have reported success this way.  Since you have only one hard disk, and partitioning shows that you have dedicated the entire drive to Ubuntu, you've got nothing to lose. :)  If you go the route of trying a total reinstall, when it comes to guided partitioning, just tell it to "use the entire disk" which will wipe out everything and start over.

If all else fails, you can put ubuntu on an external firewire which actually works quite well - once yaboot.conf has been edited, but we can cross that stream later if you like.

One way or another, you can get that nice G5 ppc box running Ubuntu!

---

### Post by AluKa on 2008-06-19
Well, I tried it all and still no luck :/  I tried switching around the device from the sata@0 to sata@1, tried physically moving the drive from one port to another, and tried switching it back to sata@0 after moving it, performing the ybin and mkofboot commands each time.

Could resetting the PRAM help?  I'm really at a loss for what to do at this point...

---

### Post by stream303 on 2008-06-20
Well, I always reset the pram if I make any hardware changes to the system.  If that is a replacement drive, it might be nice to know you are starting from a clean slate.

I DID notice one thing about my quotes:  Both examples had a SPACE between the comma and the f in the device line, whereas there should be NO space, ie ...**ht@0,f2000000** .....  Doublecheck to see if you have a space in that line and remove it and try both procedures again.  I don't know where that space came from, but thought I'd mention it just in case your lines have a space in them.

You may have to set the boot disk manually in openfirmware, and I'd have to look up some things about OF and yaboot like disk-aliases, (aka hd: sd: ultra0 and the like).  I'm hoping it's just a space in that device line - crossing fingers. :)

---

### Post by AluKa on 2008-06-20
I didn't have a space in there either :/   I just tried reinstalling again and directly copy/pasting the info from the find command into the yaboot to make absolutely sure that I had the syntax right, but still no success.  I think it's the openfirmware too, because the ofpath /dev/sda has always been  /disk@0: (even when I moved the drive).

BUT, I don't know anything about OF :P

---

### Post by stream303 on 2008-06-20
I think this thread might be just the ticket:

[http://ubuntuforums.org/showthread.php?t=439629](http://ubuntuforums.org/showthread.php?t=439629)

The key issue might be to change / comment out your /etc/yaboot.conf with these key lines:

```

boot=/dev/sda2
ofboot=sd0:2
# device=/disk@0:
device=hd:
# partition=3
# root=/dev/sda3

```

(I'm not absolutely sure that the last line, root=/dev/sda3 need to be commented out - I'd have to do some more research, but some users seem to run without it.)

and run
```
sudo mkofboot -v -C /etc/yaboot.conf
and
sudo ybin -v -C /etc/yaboot.conf
```

---

### Post by AluKa on 2008-06-20
Progress!   I added/modified the lines you suggested and now i get past the stage 1 boot!  After selecting L for the stage 1 boot, i get a message that says "welcome to yaboot version 1.3.13 and it asks me to make a selection.  The only two options i have are Linux and old, but neither of them work.

When I select linux the message I get is hd:2,/boot/vmlinux: Unknown or corrupt filesystem.  I read the thread you linked to see if I had missed anything, but nothing stood out...

Thanks so much for your help :)

---

### Post by stream303 on 2008-06-21
Ok, looks like it is at least finding the hd with the device=hd: line.  Even though you are specifying a correct device line, there is something amiss with yaboot and we have to use the built-in openfirmware alias of hd: instead.

This makes me think that changing the ofboot line would also be beneficial.  I got this from reviewing the gentoo document about yaboot and saw the comment about G5.  I'd change it to:

```
ofboot=hd:2
```

See: [http://www.gentoo.org/doc/en/handbook/handbook-ppc.xml?part=1&chap=10#manual_yaboot](http://www.gentoo.org/doc/en/handbook/handbook-ppc.xml?part=1&chap=10#manual_yaboot)

I would probably add back in these:

```
partition=3
root=/dev/sda3
```

Although at this stage, I have a feeling that this might work better (along with the previous ofboot=hd:2 example)

```
partition=3
root=hd:3
```

and follow with the mkofboot and ybin again.

It seems like a pain, but I think that powermac controller and yaboot aren't getting along so we might have to make peace with OF aliases only.

---

### Post by AluKa on 2008-06-21
More progress!  I think victory is close at hand :)  Stage one boot loads, I press L, get to the boot loader, where I type Linux and press enter.  There's a brief pause, then the ubuntu splash screen comes up!  BUT, the color is heavily distorted, and the progress bar just moves back and forth for about 5 minuts before bringing me to a new command prompt called initramfs.  I tried browsing around, but I don't think this console is in root drive...  So close!

---

### Post by stream303 on 2008-06-21
Ok, looks like we're past hd detection with device=hd; and also past detecting the boot partitiong with ofboot=hd:2.  Now to tackle root and the kernel image.

You could try this at the initramfs prompt:

```
**modprobe ide-core**
(then follow up with:)
**exit**
```

However, I'd like to back up a bit and see which option you used in your /etc/yaboot.conf for the root line.

Which one of these did you use?
**root=/dev/sda3**
or
**root=hd:3**

If you didn't try both, I would try the other option, (don't put both in your yaboot.conf) followed by mkofboot and ybin commands again.  (although at this stage, I think we can just start using ybin only - but stranger things have happened. :)

Don't worry about the ugly colors - that is typical for the ppc splash screen which can get fixed later, typically with "nosplash" in the append= line in yaboot.conf.

---

### Post by AluKa on 2008-07-05
I've been out of town for the last week, and decided to start working on this again last night.  It works!  I'm actually posting this from a working install :)

Thank you so much for your patience and help!

I had been using root=hd:3 since most of the other pathing in the yaboot.conf was the OF values, but I changed it to /dev/sda3 and it booted right up.

Thanks again ;-)

---

### Post by stream303 on 2008-07-05
Congratulations!  Thank YOU for hanging in there and helping to confirm that when it comes to PPC Powermacs, using aliases in yaboot.conf seems almost mandatory.

Can you post the final output of your /etc/yaboot.conf ?

I'm pleased to see that the video card didn't seem to give you any trouble - your model appears to come with an ATI Radeon 9600:

[http://www.everymac.com/systems/apple/powermac_g5/stats/powermac_g5_2.0_dp.html](http://www.everymac.com/systems/apple/powermac_g5/stats/powermac_g5_2.0_dp.html)

Should you feel like it, I'd definitely back up your golden /etc/yaboot.conf, and also /etc/X11/xorg.conf on some other media.  You may want to take a look at the following for tweaking your Radeon card:

[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

Then again, you could just leave well enough alone! :)

Thanks again for the great feedback.

For peace of mind, I'd check to see if both cores are running by running **top** in a terminal and hitting the **"1"** key, or install **htop** for a nice ncurses graphical version.

---

### Post by AluKa on 2008-07-05
The working yaboot.conf is as follows:

> ## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/sda2
ofboot=hd:2
#device=/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@1/disk@0:
device=hd:
partition=3
#root=hd:3
root=/dev/sda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
defaultos=linux


image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="nosplash video=ofonly"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash video=ofonly"

As for the video, I have a spare geforce 7950 that I'm planning on using after I do a little more research.

Checked the cores as well, both are operational!  This has been quite a learning experience for me, thanks again for the instruction...

---

### Post by stream303 on 2008-07-06
Thanks for posting your yaboot.conf.  Keep us informed on how that new video card performs!

---

