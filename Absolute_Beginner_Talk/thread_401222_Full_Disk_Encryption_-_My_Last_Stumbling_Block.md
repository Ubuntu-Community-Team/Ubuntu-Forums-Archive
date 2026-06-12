---
title: "Full Disk Encryption - My Last Stumbling Block"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by benenglishtx on 2007-04-04
I've made a sincere attempt over the last 6 weeks to completely replace all vestiges of non-free software on my home computer by using Ubuntu (Edgy at first, upgraded to Feisty to better handle my NTFS-formatted USB drives).  Things have gone quite well; I have mostly just minor issues that I assume I'll eventually resolve.

However, I have one last stumbling block and I'm hoping it's not a deal-breaker.  I insist on employing full-disk encryption on my computers.  (I realize this question has been recently asked in the context of using a USB key; I don't need that, nor am I interested in steganographic solutions.)  In the Windows world, I have some experience with the PGP whole-disk product.  I have very extensive experience with using SecureDoc from WinMagic.  I also own USB disk drives (by Flagstone) with strong encryption in hardware, which I expect to have no problem making work with Ubuntu.  In my former life as a Windows user, I have installed full-disk encryption dozens of times by simply inserting a disk, double-clicking a file, accepting some defaults, waiting through some reboots and overwrites, and composing a devilishly long and complex password.

Unfortunately, my first impression is that installing full-disk encryption to the two standard internal SATA drives in my Ubuntu machine is going to be far more difficult, involving a re-partition (and I so enjoyed just letting Ubuntu make those decisions at my initial install) and lots of typing in a terminal window.  That's really disappointing.  Compared to Windows, everything so far has been, at worst, reasonably do-able.  I'm finding most tasks in Ubuntu far *easier* than in Windows.  Whole-disk encryption, however, seems pretty darn offputting.

I see documentation and/or potentially useful information here:

[https://help.ubuntu.com/community/FullDiskEncryptionHowto](https://help.ubuntu.com/community/FullDiskEncryptionHowto)
[http://www.saout.de/tikiwiki/tiki-index.php](http://www.saout.de/tikiwiki/tiki-index.php)
[http://encryptionhowto.sourceforge.net/Encryption-HOWTO-4.html](http://encryptionhowto.sourceforge.net/Encryption-HOWTO-4.html)
[http://doc.gwos.org/index.php/TrueCrypt](http://doc.gwos.org/index.php/TrueCrypt)
[http://www.ubuntuforums.org/showthread.php?t=354624&highlight=disk+encryption](http://www.ubuntuforums.org/showthread.php?t=354624&highlight=disk+encryption)
[http://www.linuxjournal.com/article/2590](http://www.linuxjournal.com/article/2590)
[http://www.koeln.ccc.de/archiv/drt/crypto/linux-disk.html](http://www.koeln.ccc.de/archiv/drt/crypto/linux-disk.html)
[http://www.ubuntuforums.org/showthread.php?t=371123&highlight=disk+encryption](http://www.ubuntuforums.org/showthread.php?t=371123&highlight=disk+encryption)
[http://www.ubuntuforums.org/showthread.php?t=199824&highlight=disk+encryption](http://www.ubuntuforums.org/showthread.php?t=199824&highlight=disk+encryption)
[http://www.ubuntuforums.org/showthread.php?t=338511&highlight=disk+encryption](http://www.ubuntuforums.org/showthread.php?t=338511&highlight=disk+encryption)

Before I go further, I wanted to ask:  Am I missing something?  Is there a more streamlined way to go about this?  Is the documentation cited pretty much all I have to go on or are there additional pages I need to read before I begin?  And with the way security and encryption are becoming so incredibly important to more and more ordinary folks, why isn't there an "Encrypted Ubuntu" version that simply installs full-disk encryption by default?  (That last question may not be entirely serious but the need for such a thing seems like a no-brainer to me.)

In any event, I'm not asking anyone to lead me by the hand.  Before I start, I just want to ask: Do I have all the docs at hand?  In the alternative, is this one of those tasks where I could call someone, give them a credit card number, and get them to talk me through the process?  99.9% of the time, I am my own support desk but for this job I'd gladly pay for competent support.

Thanks in advance for any help, suggestions, or insight,

Ben in Texas

PS - As an aside, I know that it's tempting to observe that if you lose physical control of your computer, your data is compromised.  In practical terms, I don't accept that.  No one should any more.  Both the Windows products mentioned above as well as the quality hardware encryption solutions (that are available if you know where to look) are specifically designed to keep your data safe even when someone steals your computer and has all the time in the world to apply nearly all the tools and expert knowledge in the world to extracting your data.  These technologies are no longer limited to military users; in fact, the protection of "data at rest" is, in some business sectors in the United States, essentially mandated by law.  Every single bit on my drives should be encrypted all the time and accessible to me only if I type in some ridiculously long and complex password during the initial boot, before the OS loads.  That's not too much to ask and if I can't get it, I'll have to either buy some expensive hardware or go back to Windows.  I really don't want to do either of those things.

---

### Post by TDK800 on 2007-04-10
Hello Ben,

Did you find a successful solution for your data? I read ([https://help.ubuntu.com/community/FullDiskEncryptionHowto)](https://help.ubuntu.com/community/FullDiskEncryptionHowto)), but that tutorial seems to be for the weak cryptolook, not even the claimed stronger dm-crypt.

Actually both cryptoloop and dm-crypt in kernels prior to 2.6.10 are vulnerable, and even recent dm-crypt still suffers from a weak crypto implementation.

It's recommended NOT to use cryptoloop, LUKS, dm-crypt in kernels prior to 2.6.10, bestcrypt, truecrypt versions prior to 4.1, or loop-AES in single-key mode.

The recommended full disk encryption solution is loop-AES ([http://loop-aes.sourceforge.net/](http://loop-aes.sourceforge.net/)) in multi-key mode with encrypted swap! This achieves maximum available security for your data. Available ciphers are AES, Blowfish, Serpent, and Twofish.

Setting up loop-AES is not difficult, you don't have to patch the kernel (and never had to, actually). You can use it in combination with jounaling file systems, and there are lots of examples for different setups mentioned in the loop-AES.README ([http://loop-aes.sourceforge.net/loop-AES.README)](http://loop-aes.sourceforge.net/loop-AES.README)). You even can encrypt an existing (cleartext) partition non-destructively with loop-AES using aespipe ([http://loop-aes.sourceforge.net/aespipe)](http://loop-aes.sourceforge.net/aespipe)). Additionally there's the linux crypto mailing list ([http://mail.nl.linux.org/linux-crypto/](http://mail.nl.linux.org/linux-crypto/)) for help.

Hope that is of help and if You're successful, any tutorial contributions for setting FD encyption up in Ubuntu environment are greatly appreciated. :)

---

### Post by benenglishtx on 2007-04-12
> **TDK800 said:**
> Hello Ben,

Did you find a successful solution for your data?Thanks for the reply.

I had resigned myself to an implementation almost entirely in hardware.  The cost would, from my perspective, be somewhere between high and astronomical, adding a minimum of USD$500 to my new computer budget and conceivably several thousands more.

However, you've specifically answered my original question.  I did NOT have all the docs I needed before I start work.  I've subscribed to the mailing list and I'll be taking my time digesting everything that's been posted to it for the last couple of years before I make any decisions.

As for any potential tutorials, I expect to fully document what I do.  Understand that what I do will be known compatible with just a single computer run by a single user, but if anybody can profit from that, I'd be gratified.  Any such doc would be months in the future, of course.  That mailing list and the docs on sourceforge that you've so kindly brought to my attention will take a long, long time for me to fully digest.

Thanks again.  You can't know how much I appreciate your assistance.

Ben in Texas

---

### Post by kkass on 2007-04-23
I am also planning to try encrypting an entire partition.  I found a good HOWTO in the O'REILLY book Ubuntu Hacks.  In hack #70 the book walks you through setting dm-crypt.

---

### Post by george_koss on 2007-05-19
Well Ben, you've made the right decision to abandon M$ and take control of your own computer.  Right On, Brother!   Let me share with you (and the multitudes) some of my own experiences.  I've been using Loop-AES for years now, trying to keep my data safe, secure, and under control.    I've been building file servers at the rate of one every six months, and it looks like this trend will continue for a long time to come.   Let me start with hardware, and work my way up the stack to key management.

Principles:

1.  Don't use the same computer for hacking & data storage.  File System corruption is all too easy when the kernel goes "Oops".   The implication here is that the machine which stores the data is using a stable release, and once you verify it works... DONT TOUCH IT!   My file servers are headless, without a keyboard or graphics card, and only a serial port for the console.   This is a bit advanced for most people, so I won't expect everyone to do this.  I use a diskless machine (Asus M2A-VM) as a multimedia/surfing/hacking experimental platform, and whatever I do on this won't affect my file server.  Not only that, but the NFS root for the diskless machine is encrypted on the file server.     But diskless operation is pretty advanced, and with Feisty is a positive pain because of an Avahi bug, so I'm going to break my own recommendation and describe a file server (with encryption) usable for everyday useage as a home PC.   

2.  Recipe for a file server:  Antec Nine Hundred case, with 350 to 450 watt energy efficient Power Supply.   Fill it with from 5 to 6 Seagate Sata2 drives (400 to 500GB each).  Seagate has a 5 year warranty, and the replacement procedure is relatively painless.  Add Silent (no fan) NVidia graphics card (optional if you go headless).  Motherboard is AM2 with 6 SATA2 connectors, such as ASUS M2N-E or MSI K9N-SLI motherboard (NF570 chip provides the hex Sata2 interfaces).   Add DVD drive.  Add 65nm dual CPU AM2 processor with 1 to 2 GB of DDR2 PC5300 memory.  Use ECC ram if you live above 4000 feet or close to a magnetic pole.  I've never seen a bit error in the RAM, but you just know that someday a cosmic ray, solar flare, or reactor spill will make the ECC pay off.  Finally, add an APC backup power supply.  This is NOT optional.  Power failure is the fastest method to corrupt your data I can think of.  I choose APC backup units because it's dead simple to install the drivers.

3.  Assemble hardware and boot Kubuntu 7.04 AMD64 Desktop.  I originally chose KDE because I read a post by Linus once that disparaged Gnome.  You can make your own choice on this one, since it's semi-religious.  Now supposing you have 5 disks of 500 GB, partition all of them with partition 1 having 1024 cylinders, and partition 2 with the rest.  Each of the first partitions will have around 8 GB, which is enough for the OS, but not much else.  If you plan on installing a lot of applications, you might want to increase the partition size to 20GB.  Install the OS on /dev/sda1 using ext3 ( first partition of first disk ).  Set the swap to /dev/sde1 (first partition, last disk).   Ignore disks b, c, and d for the moment.  Install and reboot.

4.  Here I will admit that I have not mastered the art of encrypted Root file systems with Ubuntu.   I'm still trying to find time to attack this.   But the next best thing is a root RAID filesystem.    "sudo apt-get install mdadm"  will install mdadm for you, and then you can create the a root raid 1 device on the first partitions of drives b, c and d.   This is something new for my file servers, since in the the previous generation, I just installed a larger drive for disk 1, and then used it to hold the OS with no redundancy.   I have not yet given this new server the "yank" test, where I yank out drives randomly and see if it still boots.  I had trouble to get this to boot at first.  If it drops you to busybox with a timeout, try typing "mdrun" followed by control-D to see if that starts the raid device.   I had to insert a "sleep 10" command in the /usr/share/initramfs-tools/init script to get it to have enough time to start the raid device.   Once you get it booting from the raid device, you can add /dev/sda1 to the raid array with the --grow option in mdadm.  My thinking on raid1 boot partitions is that you can guard against bit-rot and bad updates by using the mdadm -fail command to take some of the partitions offline, to serve as live backups.  I'll probably write a script for cron that rotates the partitions offline on a weekly basis, so that one is always offline.  When the script puts a partition back-online, the raid rebuild process will automatically rewrite every bit of data on that disk partition, thus keeping it refreshed and letting the disk management firmware do its thing to remap sectors when they become flaky.   Don't forget to install "smartmontools".   These are invaluable for testing a disk, and checking the disk temperature.   I like to run my disks around 30C, and the Antec Nine Hundred case has enough fans in it to practically take off vertically.  

5.  Here is a tip for installing loop-AES on Feisty.   I had trouble to find the loop-AES source package but you can grab it here:  [http://http.us.debian.org/debian/pool/main/l/loop-aes/loop-aes-source_3.1f-2_all.deb](http://http.us.debian.org/debian/pool/main/l/loop-aes/loop-aes-source_3.1f-2_all.deb)
The previous release 3.1d did NOT work for me with Feisty.  Follow the usual instructions to build and install it with module-assistant.  Once you have loop-aes running ok, first thing is to setup an encrypted swap on /dev/sde1   Modifying fstab  will do the trick.  

6.  Finally, you can build the main raid5 device for the data storage, using the large partitions on /dev/sda2, /dev/sdb2, etc.   5 disks with 480GB in Raid5 will give you nearly 2TB of storage.   I heartily recommend the 65 key method for loop-aes.  I used to use Reiser3.6 as a file system, but have since moved to XFS.  Ext3 is fine for the root partition, but it is slow and has a lot of overhead for major file systems.   I have found that the software stack is a little clunky.  XFS on top of 65 key Loop-AES with 256 bit keys, on top of RAID5 with Sata2 drives gives me about 30 Mb/sec write performance, and 60 Mb/sec read performance with a 4200+ X2 AMD cpu.   Your mileage may vary.   A lot of performance is lost because loop-AES only operates on 4K chunks, while the Raid5 subsystem is using 64K chunks, while XFS is using something else.   I'm personally waiting to see if ZFS with encryption will provide a better, higher performance solution to the RAID5 with encryption problem.  

7.  Final tip.   Don't attempt to enable or use hibernate mode, and make sure all firewire ports are disabled or disconnected.   Firewire can be used to directly read memory from the machine, including the keys.

---

