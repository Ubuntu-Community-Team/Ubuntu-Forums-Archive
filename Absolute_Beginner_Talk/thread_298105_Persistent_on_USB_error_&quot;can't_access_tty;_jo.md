---
title: "Persistent on USB error &quot;can't access tty; job control turned off&quot;"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by Lxs on 2006-11-12
Laptop with WinXP, wishing to use Ubuntu Edgy with persistence on 256Mb USB key.
My end desire being to have Trac utilities ([http://trac.edgewall.org/](http://trac.edgewall.org/)) setup on the persistent USB, for simple deployment to my domain.

This is what I have done so far:

Followed instructions on [https://help.ubuntu.com/community/LiveCDPersistence](https://help.ubuntu.com/community/LiveCDPersistence)
- used sdb/sdb1 instead of sda/sda1 in the various commands (as sda appeared to be my laptop harddisk at 60Gb in size!).
- used ext2 instead of ext3, it is a USB key that does not reap benefits of ext3 (will try ext3 if things still don't work)

Following reboot, hitting <F6> and appending "persistent" to end of argument list.... sadly there is a boot error:


> /bin/sh: can't access tty; job control turned off
(initramfs)


Had a look in the casper.log file, which showed the following:

> 
mount: Mounting /dev/sdb on /cow failed: Invalid argument

Can not mount /dev/sdb on /cow


going to take a look at my menu.lst to see if there is anything interesting there...

Not sure how to continue... would be grateful for tips and ideas!
thanks in advance!

---

### Post by XEmacs on 2006-11-13
Hi Lxs,

good to see you here, too.

I would expect that it has got to do with the order in which the linux system boots and inserts kernel modules.

As you have stated during regular operation /dev/sda is your laptop's SATA (I assume) hard disk. At boot time the SATA module may not be loaded, yet. So just your boot loader knows how to get the boot image without telling the kernel how it got it in the first place (bugger, ain't it mean?). So when trying to access the USB key as "mass" storage will be probably mapped to /dev/sda. Whereas on a running system setting it all up nicely the earlier accessed SATA block device would be mapped to /dev/sda, so you'll have it all backwards.

Try telling the system that it'll find the USB key using /dev/sda instead, and hopefully that'll work then ...

Have phun trying it out,

your old fashioned but still fancy editor XEmacs

---

### Post by Lxs on 2006-11-14
Morning XEmacs!
...how can this be done when I am loading from LiveCD? (i.e. the load options are already set) surely this would require modification to the iso image...

Are there other steps that I could take?
Lxs

---

### Post by dissdigg on 2006-11-14
Not a solution (sorry) but a similar problem.

I have a system w/ no hard drive and a BIOS that cannot be upgraded to boot from USB.

I plan to run a LiveCD install w/ a 1 gb usb thumbdrive for persistence.

If the system loses power in the middle of the night, I wont be there to type F6 and "<space>persistence" when it reboots.

I'm assuming I too will have to edit the .ISO so it will automatically add "persistence" to the boot options.  Can anyone point me in the right direction here?  Thanks!

---

### Post by Lxs on 2006-11-17
dissdigg, have you tried a text search in the source code?

This would be my starting point, using the text from the default string that is displayed after boot + <F6>. There may be hints in the source code for a way to make the cd-boot always use persistence.

- - -

As for my troubles, my next task is to investigate more the reason why the mount fails of /dev/sdb onto /cow

Lxs

---

