---
title: "Dual Boot system won't boot up when Ubuntu HDD is disconnected..."
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Earthwormzim on 2007-06-11
Hello, 

I think the title of the post pretty much sums up my problem.  But, just in case it's not totally clear...I just recently installed Ubuntu on my second hard drive, with Windows XP already on my first (primary) hard drive.  

Today, though, I disconnected my Ubuntu drive so that I could connect another hard drive from another computer in an attempt to recover some data off it that I inadvertently deleted, using a program that was installed in Windows on my primary hard drive.  But, it would not boot without the Ubuntu drive being connected.  Grub would show up, but then it would just give some error, and wouldn't boot.  I'm guessing that it has something to do with Grub getting installed on the Ubuntu drive...and when it is not present, it can't boot.

Anywho...my question is this:  if I'm correct (that the system won't boot because Grub is installed on the secondary/Ubuntu hard drive), then how do I make it so that it will?  Do I (somehow) uninstall Grub on my Ubuntu hard drive, and re-install it on my Windows drive?  If, however, this is not the problem...then...any suggestions?

Thanks for your time, should you choose to help me out.

Robert

---

### Post by Earthwormzim on 2007-06-11
OK...I found something about "Super Grub Disk".  I'm gonna download and burn the .iso in XP, and see what it can do for me.

---

### Post by locke.dragon on 2007-06-11
i can't help you solve the problem but i think i know why the problem is there.  (to all the ubuntu pros out there, please correct me on this if i'm wrong.)  my guess is that when you installed ubuntu, it installed grub on that second hard drive and that made your computer unable to boot without going through grub.  am i right?  or am i totally wrong?

---

### Post by p_quarles on 2007-06-11
There's got to be some kind of hard drive data recovery boot disk out there. Have you done any looking around for something like that? 

Anyway I, too, am fairly certain that grub is part of the Ubuntu installation.

---

### Post by Bohlio on 2007-06-11
I think your right, When you installed, The MBR points to your second hard disk to boot up, when your second disk isnt there, well then you have problems :-P
If you install grub directly to your MBR that should fix it. 
(I think, calling on the "ubuntu pros" for confirmation :-P)

---

### Post by veerakumar on 2007-06-11
The problem is grub's image stage2 is on 2nd hdd and stage1 is in
Master Boot REcord of 1st hdd
use floppy or cd to boot grub from.
take floppy or cd image from grub's site
Then
change root to first hdd
chainloader +1
boot

---

### Post by Earthwormzim on 2007-06-11
> **locke.dragon said:**
> i can't help you solve the problem but i think i know why the problem is there.  (to all the ubuntu pros out there, please correct me on this if i'm wrong.)  my guess is that when you installed ubuntu, it installed grub on that second hard drive and that made your computer unable to boot without going through grub.  am i right?  or am i totally wrong?

Yes, this is exactly my problem.

> **Bohlio said:**
> I think your right, When you installed, The MBR points to your second hard disk to boot up, when your second disk isnt there, well then you have problems :-P
If you install grub directly to your MBR that should fix it. 
(I think, calling on the "ubuntu pros" for confirmation :-P)

But, if I install Grub on my first hdd, then will there be a conflict between the two Grubs when both hdds are connected?  In other words, should I un-install the first (the one on the second hdd...with Ubuntu on it)?

---

### Post by Earthwormzim on 2007-06-11
> **veerakumar said:**
> The problem is grub's image stage2 is on 2nd hdd and stage1 is in
Master Boot REcord of 1st hdd
use floppy or cd to boot grub from.
take floppy or cd image from grub's site
Then
change root to first hdd
chainloader +1
boot

Looks kind of confusing, but I'm willing to give it a try.  I'll let you know what happens when I do it.

---

### Post by Earthwormzim on 2007-09-14
OK, I maybe wrong...but can't I just edit the menu.lst file instead of going through the process of burning grub to a live cd and booting from it?  If so, what exactly do I change in it?  Here is exactly what is in my menu.lst file.  If booting is the only way...then ho-hum, guess I'm going to have to do what I have to do.

```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=052346d7-1e5e-44f0-910e-84d8f7dbab96 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=052346d7-1e5e-44f0-910e-84d8f7dbab96 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=052346d7-1e5e-44f0-910e-84d8f7dbab96 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=052346d7-1e5e-44f0-910e-84d8f7dbab96 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by confused57 on 2007-09-14
If you want your first hard drive to boot independently of grub, you'll need to install Windows IPL to this drive's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
The easiest methods are Super Grub Disk or a Windows install cd(not a recovery cd)

If you're able to set your bios to boot first to your Ubuntu drive, you could use the Ubuntu live cd to install grub to the Ubuntu drive's mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

However, to boot first to your Ubuntu drive, you'll need to change root from (hd1,5) to (hd0,5)...if you decide to install grub's IPL to this drive's mbr and get a grub boot menu, highlight your first Ubuntu entry, press "e", then highlight the line with root, press "e" again, change root from (hd1,5) to (hd0,5), press "enter", then press "b" to boot...this change is temporary, but if it works you can make it permanent in your /boot/grub/menu.lst.   You could then add an entry to grub to boot Windows from grub, e.g.:
```
title   Windows XP
rootnoverify  (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

---

### Post by veerakumar on 2007-11-08
Try changing BIOS sequence to primary hard drive.
After that please explain what is going on.

SFX: [http://www.spreadfirefox.com/?q=affiliates&amp;id=211983&amp;t=1](http://www.spreadfirefox.com/?q=affiliates&amp;id=211983&amp;t=1):popcorn:

---

### Post by adrian15 on 2007-11-15
Hi,

    You can solve your problem by trying to boot your Linux system from Windows' boot.ini but it is not as easy as it seems because it involves two hard disks. I have asked my Super Grub Disk collaborators to write a howto for your particular situation.

   You can try to join the [supergrub mailing list]("https://listas.ensanjose.net/listinfo/supergrub") to encourage them to do it or you can wait till I get their work back and I put here a link.

adrian15

---

### Post by MQMike on 2007-11-16
First, obviously, your BIOS supports “boot from USB,” otherwise, you wouldn’t be posting this.  Second, HOW does your BIOS do it?

On mine (Intel D915GAVL), I first boot up using the external HDD.   Then in BIOS setup, I include the external USB HDD in the list of hard drives, and I put it right after the CDrom but before my regular first-to-boot hard drive (that would be your Windows drive).

My external drive does not work under hot-plugging because my motherboard does not support eSATA.  So I have to shut down the PC, connect and turn On the external HDD, turn on the PC, the BIOS does the POST sequence, and since the external drive is connected, BIOS detects it and it boots from it.  Sometimes, it doesn’t, and then I have to re-boot and it will work.  Rarely have I had to intervene and enter BOS setup to force BIOS to boot from the external drive.

Now, some BIOSs won’t work that way.  They require you to manually intervene each time by entering BIOS setup and forcing the boot to the external drive.

OK, with that all said . . .

Here’s what I would do if I were you, to keep this simple.

Connect the external USB HDD to your PC and boot up to your Ubuntu OS.
Get a terminal.
Type sudo grub.
That gives you a GRUB prompt, like grub>.
Then type these commands at the GRUB prompt:

grub> root (hd0,0)
grub> setup (hd0)
grub> quit

That will set GRUB up in the Master Boot Record (MBR) of your external USB HDD.

Next, fix your Windows MBR:  Re-install the Windows bootloader to the MBR of your internal drive.

That should do it.

When you turn on the PC with the external drive connected (and turned On), your PC should boot from it (assuming you set up BIOS to do so).  If BIOS doesn’t work that way in your PC, then manually intervene by entering BIOS setup and forcing it to boot from the external drive.

Modification:  You could edit the menu.lst in /boot/grub in Ubuntu on the external drive to include a boot entry for Windows; then even if the external drive is connected, and your PC boot from it, you could boot into Windows using that GRUB boot menu that appears.  The entry for Windows would be:
title Windows on the internal HDD
rootnoverify (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1

When you turn on the PC with the external drive NOT connected, the PC will, of course, use the Windows bootloader NTLDR, to boot into Windows.

That should do it.


Another solution would be the following:

On the Windows drive make a small, dedicated partition just for GRUB files.
Set up GRUB there and in the MBR of the Windows drive.
Configure GRUB to boot both Windows on the hd0 drive and Ubuntu on the external drive hd1.
That should also work.  GRUB would then be your bootloader for both Windows and Ubuntu.
(If you want detailed help with this solution, just post back here and I’ll give you my 2 cents worth.)

---

