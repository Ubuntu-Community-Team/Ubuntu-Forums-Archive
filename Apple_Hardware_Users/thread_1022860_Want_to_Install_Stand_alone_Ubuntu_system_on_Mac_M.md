---
title: "Want to Install Stand alone Ubuntu system on Mac Mini"
date: 2008-12-27
forum: Apple Hardware Users
---

### Post by skhalil on 2008-12-27
Hello, guys!

I have owned this Intel Core2Duo macmini for about an year now and I have been using Ubuntu and Leopard as dual boot through out the year. Now I want to switch completely to Ubuntu and want to Install it as a single operating system. After doing a lot of googling I didn't find any work around for this. Can you guys help me in this regard. I want to use Ubuntu as the only OS on my mini and want to help it without using boot camp. Please help me out. I want to save my precious hard disk space from the leopard partition.

---

### Post by damis648 on 2008-12-27
I don't know if that's possible, I think Leopard controls EFI which it needs to do it order to boot.

---

### Post by mkvnmtr on 2008-12-27
I would think you can just install from the disk but don't take my word for it until you have talked to some people that have done it. What I know you can do is strip you mac os down and instal it on avery small partition. On my G4 IBook I got down to less than 3 GB from ^ gB on a normal install and put it on a 5 GB partition. You should have the option of leaving out a lot of bundled software like garage band and some language support for languages you never use. That way you will have the OS but it won't take up much space.

---

### Post by Captain- on 2008-12-27
Yes, you can run Ubuntu by itself without having Leopard/Tiger (Mac OS) installed.

Some Linux distros support EFI natively, I believe.  Others may still rely upon BIOS (which Macs do not have).  Be sure before you take the plunge, though.  See more info at: [http://www.mactel-linux.org/wiki/EFI]("http://www.mactel-linux.org/wiki/EFI")

What you can do is setup Boot Camp and rather than installing Windows, just install Ubuntu from the CD/DVD and install the boot loader if asked.  When you setup partitions, the 200 MB partition is Boot Camp.  The hfs/hfs+ one is your Mac OS installation.  When you install Ubuntu Linux you can choose from several file systems like ext2, ext3 journaled, etc.  From an end user perspective, it might not really matter which one you choose unless you have specific needs that a certain file system provides.  I went with ext3 journaled and have had no trouble with it.  In the past I've also used ext2 and reiserfs successfully.  You should setup a swap file, I usually go with a size about equivalent to the installed RAM memory.  If you tell Ubuntu to use the entire disk, it will basically take care of all the partitioning/swap file setup, etc. for you.

Be advised that you won't be able to install any firmware upgrades for your Mac without a native Mac OS X installation.  Apple does not provide such updates in a Linux compatible format.

I know that others have removed OS X and run Windows (as the sole OS) so you can do the same with Linux.  You may not even need to use Boot Camp at all (I do not believe it is required to accomplish this).  You may wish to leave a small installed copy of Mac OS (Tiger or Leopard) and simply rarely use it, if that is your preference.  You can set the default boot up OS to be Ubuntu, and use it for 99.999% of the time and things that you do.

---

### Post by Rog-Mahal on 2008-12-27
You DO NOT need an EFI partition to boot a Mac successfully. I singlebooted my Macbook 2,1 for about a year. If you so choose, you can wipe your entire hard drive and install Ubuntu on it. If you choose to do this, the only side effect is a delay during boot up. Macs look first for an EFI partition to boot from, if they don't find one, it switches over to looking for a Legacy boot system (Linux, Windows). 

That being said, do you want to keep your OS X partition/data? If so, you might want to look into [rEFIt.]("http://refit.sourceforge.net/") I think you can configure it to work with existing partitions, however I only used it when doing fresh installs. You can configure it to boot to your Linux partition, and even set the boot timeout to zero so it automatically does it. I highly recommend it instead of BootCamp. If you have any questions, I'd be glad to help.

---

### Post by pxwpxw on 2008-12-27
> **skhalil said:**
> Hello, guys!

I have owned this Intel Core2Duo macmini for about an year now and I have been using Ubuntu and Leopard as dual boot through out the year. Now I want to switch completely to Ubuntu and want to Install it as a single operating system. After doing a lot of googling I didn't find any work around for this. Can you guys help me in this regard. I want to use Ubuntu as the only OS on my mini and want to help it without using boot camp. Please help me out. I want to save my precious hard disk space from the leopard partition.

This post is one way to do what you want.

 Apple Intel Users FAQ #21

[http://ubuntuforums.org/showthread.php?p=5166788#post5166788](http://ubuntuforums.org/showthread.php?p=5166788#post5166788)

As an alternative to using the rEFIt cd Partition sync, you can use the Ubuntu live cd to install the Linux refit package and run gptsync from there, but note that you will need the Mac OSX install dvd to 'bless' the grub bootloader partition which gets the fast start.

---

### Post by skhalil on 2008-12-28
Guys, I am happy to announce that I have now got stand alone Ubuntu system on my mac mini with complete blue tooth and wifi support out of the box. The procedure is simply easy. You have to use the entire hard drive wiping out all the mac os components using the guided way of the Ubuntu partitioner. The boot delay is not too much for me. It may be about 5 to 8 seconds only which is tolerable. Well thanks for ur advices.

---

### Post by levelup3 on 2008-12-30
is really useful for me

---

