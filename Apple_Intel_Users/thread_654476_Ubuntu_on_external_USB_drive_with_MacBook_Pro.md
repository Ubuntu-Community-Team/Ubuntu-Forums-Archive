---
title: "Ubuntu on external USB drive with MacBook Pro"
date: 2007-12-31
forum: Apple Intel Users
---

### Post by lotus49 on 2007-12-31
I have a MacBook Pro that won't boot from a USB drive and I am trying to find out if anyone else has been successful doing this.

I have tried booting Ubuntu and a version of Windows XP (modified to run on a USB drive - XP won't normally do this) from an external USB hard drive.  Both installations successfully booted on other machines.  I used rEFIt as a boot loader and with both OSs it saw the drive but failed to boot.

As a result of extensive research on the net I have come to the conclusion that the problem is the latest MacBook Pro firmware (Version 1.4 shown as MBP22.00A5.B07 in System Profiler) and this is what I am trying to confirm.

Has anyone successfully booted Ubuntu (or indeed any other OS) on a MacBook Pro with the latest (MBP22.00A5.B07) firmware?  If so, can you say what the spec of your machine is (I don't believe that this is a factor but I want to make sure if I can).

Even if you have tried and failed, replying to this thread will at least confirm that this is the problem.

---

### Post by PaulFXH on 2007-12-31
I know that this may not at all answer your primary question, but may be of interest to you and others nonetheless.
Also, I don't have a MBP but rather a MacBook C2D (2.16 GHz).
I already have three Linux OSes on the internal HD of the MacBook and these work fine.
However, I also had an external HD (Seagate 250 GB) on which I had previously installed quite a number of Linux distros to all of which I was able to boot from my Dell desktop (even though the usb drive was non-bootable to the Dell).
So, I decided to try to boot to Fedora 7 on the usb HD from the Mac. Initially, I put root in /boot/grub/menu.lst (in Ubuntu on the internal HD which is what I use to boot all of my Linux stuff on the Mac) to refer to the external drive. But, this just was not recognized.
OK, so then I put root to refer to the Ubuntu root partition on the internal HD and I installed the vmlinuz and initrd.img files from the Fedora /boot directory into the /boot of Ubuntu on the internal drive.
Note, however, that the reference to root on the kernel line in /boot/grub/menu.lst still referred to the Fedora root partition on the usb drive.
This booted fine and Fedora 7 now runs fine on my MacBook.
Obviously, if this works, there should have no problem booting Ubuntu similarly from the usb drive.
I can't speak for the MBP as I have no experience with it but I doubt if it's going to be very different.

---

### Post by lotus49 on 2008-01-01
This sounds like a setup I have done accidentally when I have been trying to configure an external USB installation and rather confirms the booting problems I have had.

You appear to be booting from the internal hdd but just mounting the root on the external hdd after the machine has booted.  This won't work for me partly because I want to leave my internal hdd untouched but mainly because XP is rubbish and isn't capable of making  the boot/root distinction as easily as Ubuntu can.

---

### Post by cyberdork33 on 2008-01-02
please see the faq thread. This is not straightforward and there is no obvious answer.

---

### Post by CarlJohanSveningsson on 2008-06-30
Hi all, lotus49,

I'm having very similar problems, described here:

[http://forum.onmac.net/showthread.php?p=13184#post13184](http://forum.onmac.net/showthread.php?p=13184#post13184)

Unfortunately I must agree with lotus49 that there may be an error connected to the computer model or firmware (since the above post was made I use firmware version MBP22.00A5.B07) - mostly it's lotus49 who has posted, but I have some bookmarks related to the issue here:

[http://del.icio.us/poquatelhar/MBP22.00A5.B07](http://del.icio.us/poquatelhar/MBP22.00A5.B07)

tidbits has a somewhat aged article describing the issues surrounding APT/GPT/MBR partition tables:

[http://db.tidbits.com/article/8405](http://db.tidbits.com/article/8405)

I would think I have tried most variations to get Linux to boot off the USB stick (also different models of sticks), including rEFIt on the main drive even though I don't want to have to touch that, rEFIt on a Mac partition on the stick, GPT or MBR partition tables on the stick... some make the linux partition not show up during boot, though bottom line it all ends with the seven (or in some cases more?) "Error: Not Found from LocateDevicePath" .

It would be truly terrible if I get this issue also when attempting other OS's, but I would anyway love to get Linux working like this as well, did you end up having any ideas?

---

### Post by lotus49 on 2008-06-30
If you look at this thread [http://ubuntuforums.org/showthread.php?t=510030](http://ubuntuforums.org/showthread.php?t=510030) you will see that I spent a **lot** of time trying to get this to work and I came to the conclusion (sadly not accurately contradicted by anyone) that this is just not possible with the current firmware.

I have very good reason to believe that, as things currently stand, the MBP C2D firmware is not capable of booting what Apple terms a "legacy os", which appears to mean not Mac OS X, from a USB drive no matter what you do.

If you don't mind writing grub to your internal disk or using a boot CD it works for Ubuntu at least.

I don't want to change my internal HDD and using a boot CD is ugly and hard to maintain when the kernel is updated so I eventually gave up.

---

### Post by CarlJohanSveningsson on 2008-07-01
Aha, thanks. Well, a boot CD at least partly defeats the purpose of a USB stick, but can work as a temporary solution. I did that with root=/dev/sda1 or something to use the USB?

Using grub could also be a temporary solution which works for me but not for my users. How "dangerous" is it to try to boot my machine off grub (I was nervous enough about rEFIt) and is there any way to make it safer?

I would just want to comment not to get too stuck on the MBP and this firmware version, as you can see I had issues not distinguishable before with a MacBook and different firmware, so better to search for the error message and see if the error can be figured out.

---

### Post by lotus49 on 2008-07-02
Using grub really isn't at all dangerous if you are careful and know what you are doing, but to understand why I didn't do this I need to explain a bit about what I was trying to achieve.

I already have another laptop running Ubuntu (as well as four desktops) and a very fine OS it is, so I don't really need to be able to dual boot my MBP.  The reason I was trying this was as part of trying to diagnose the difficulty I was having running XP from a USB drive.

Why would anyone want to run Windows?  It's a fair question but there is a game I want to play (Grand Prix Legends if you're interested) that runs on XP and I don't have any machines with any form of Windows installed on them.

Booting XP from a USB drive is not trivial but I managed it on another, slower, machine but failed on my MBP which would run it well.

I dislike Windows so much that I couldn't bring myself to pollute my beloved MBP with it hence the USB drive approach.  (In any case my HDD is almost full so there's no room.)

It is very frustrating that the most modern computer I have won't boot OSs other than Mac OS X from a USB drive whereas all the others I have do it fine.  Incidentally, OS X runs absolutely fine from a USB drive.

If you ever get anywhere with this, I would be very interested (but even more surprised) - good luck.

---

