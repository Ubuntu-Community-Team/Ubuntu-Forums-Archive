---
title: "Installing Dual Boot"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by iain_colin on 2007-07-25
Hey Everyone.

Im a complete noob to all of this so sorry if i seem a bit overwhelmed.

Basically my story is that i have really enough of windows and the fact that it keeps crashing, although i do need to keep it for long story reasons. I only have a 40GB hard drive and at the moment 15 of this is taken up by the windows installation, and this is the bare minimum i can have. I do have a 160GB external hard drive, however, as i have learnt it is not the easiest thing to do to install on to it and then boot off of it. When i install Linux, i need to have one partition that can be accessed from both windows and Linux easily, as i have tons of documents, music and pictures.

Does anyone have ideas on doing this quickly and easily, because i have tried using the LiveCD and it doesnt seem to run very well on my DVD Drive, and i want to try Ubuntu out for a couple of weeks before deciding if i want to keep it permanently.

As well as this, i have a coupl of other questions, sorry!

1. Is there any VirtualCD software out there for linux e.g. Alcohol?

2. Do i have to download the source code packages from Ubuntu? Can i download them from XP and then run them in Ubuntu?

Thanks very much, and sorry to bother you!

Iain

---

### Post by logos34 on 2007-07-25
Does your Bios support booting from USB device?  If so, then booting ubuntu from that external may be easier than you think (it used to be a nightmare not so long ago but things have changed dramatically).  Editing your grub bootloader config files can sound confusing but it's actually fairly straightforward.  

Is this a laptop? 

Edit: and you can make a shared fat32 partition you can read+write to from either side.  Or just install fs-driver in windows (r+w to linux ext2/3) and ntfs-3g for linux

Check these out:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by meierfra on 2007-07-25
You might want to give wubi a try:

[http://wubi-installer.org/]("http://wubi-installer.org/")

---

### Post by iain_colin on 2007-07-25
> **logos34 said:**
> Does your Bios support booting from USB device?  If so, then booting ubuntu from that external may be easier than you think (it used to be a nightmare not so long ago but things have changed dramatically).  Editing your grub bootloader config files can sound confusing but it's actually fairly straightforward.  

Is this a laptop? 

Edit: and you can make a shared fat32 partition you can read+write to from either side.  Or just install fs-driver in windows (r+w to linux ext2/3) and ntfs-3g for linux

Check these out:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)


As far as i know t does,  managed to get DSL onto a USB stick and boot off of that so it should work with my hard drive. Would the GRUB be on the internal or external, as it is a laptop, and i dont have it plugged in sometimes, so the option to boot into ubuntu would be virtually useless. 
On the filesystem side, im trying to get it so that there is one partition for the windows stuff that linux cannot under any crcumstances touch, while there is the document one. Sadly my document part is in NTFS at the moment, as i have files over 4 gb big lol.

Thanks for the sites, i have looked at them in the past.
As far as Wubi is concerned, i am downloading the iso now ( I Love bigpond :D), but if i wanted to use it on a disk, i have had problems in the past, as the drive wont read properly!

Iain

---

### Post by logos34 on 2007-07-25
> As far as i know t does, managed to get DSL onto a USB stick and boot off of that so it should work with my hard drive. Would the GRUB be on the internal or external, as it is a laptop, and i dont have it plugged in sometimes, so the option to boot into ubuntu would be virtually useless.
On the filesystem side, im trying to get it so that there is one partition for the windows stuff that linux cannot under any crcumstances touch, while there is the document one. Sadly my document part is in NTFS at the moment, as i have files over 4 gb big lol.

You would put grub on the MBR of the external drive.  That way when it's not connected you boot into windows by default. And segregating the OS's in this way ensures that if anything ever gets borked on one side you can still boot into an operable OS.  When you plug the USB drive back in you will have to enter the bios and make it first in boot order again.  To make one of the ntfs partitions untouchable, just comment out or delete the entry in /etc/fstab so it doesn't mount in linux, or disable ntfs-3g for that partition (so you can't write to it).  Are you talking about the C: drive with system files?

---

### Post by iain_colin on 2007-07-25
> **logos34 said:**
> You would put grub on the MBR of the external drive.  That way when it's not connected you boot into windows by default. And segregating the OS's in this way ensures that if anything ever gets borked on one side you can still boot into an operable OS.  When you plug the USB drive back in you will have to enter the bios and make it first in boot order again.  To make one of the ntfs partitions untouchable, just comment out or delete the entry in /etc/fstab so it doesn't mount in linux, or disable ntfs-3g for that partition (so you can't write to it).  Are you talking about the C: drive with system files?

Yep, C has the System Files and is 15gb and D has my documents and is 22 Gb

I had a look at DaBruGo's tut on external and installing and frankly it really seems a bit confusing? Am i right

---

### Post by meierfra on 2007-07-25
> As far as Wubi is concerned, i am downloading the iso now


Wubi is an exe file. You don't need  a cd-room drive for it. In fact I used wubi on an old laptop, whose cd-room is broken.

---

### Post by logos34 on 2007-07-25
> Yep, C has the System Files and is 15gb and D has my documents and is 22 Gb

I had a look at DaBruGo's tut on external and installing and frankly it really seems a bit confusing? Am i right

Yeah, but that howto dates to '05...You shouldn't have to worry about loading usb modules, initramfs, chrooting and whatnot--at least I didn't and I've booted feisty on two different external drive (well make that internal hard disks mounted in usb caddies).  The confusing part is making sure grub doesn't install to 'hd0' windows/internal drive and the (hd1,0) to (hda0,0) switch in menu.lst--you can't boot into ubuntu until you edit menu.lst an device.map.  But you can edit those files easily by booting from the live cd and fixing them.  Then you should be good to go.

---

### Post by iain_colin on 2007-07-26
Thanks very much, ill try that later! I wish id had a look at this sooner, you guys are much better than the support windows can offer me! Congrats

When i said i was downloading the ISO i meant the Feisty one, so it wouldnt cost a bomb on bandwidth from the official site.

---

