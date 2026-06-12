---
title: "[SOLVED] Help me get my Mac OSX back"
date: 2009-01-10
forum: Apple Hardware Users
---

### Post by partitoman on 2009-01-10
Ok, so I did one of those very stupid things that is probably fairly easily fixable but is still a major pain in the butt, especially to someone who knows nothing about Mac OS or Ubuntu.

I was playing around with the Ubuntu LiveCD and wanted to try the USB drive installation. Instead of choosing "Create a USB startup disk" option like I should have, I started an "Install", mistakenly thinking that it would give me that option.

I stopped the install process before any damage was done, but when I tried to boot back into my Mac OS there was no boot disk present. I suspect that the Ubuntu install, even though I aborted it, still repartitioned my Mac HD.

So I booted back into the Ubuntu, and started up GParted. I wanted to check with the experts here before I did anything colossally stupid.

I see:

[html]/dev/sda1  |   fat32   | EFI | 200.00MiB | ... | boot
/dev/sda2  |   hfs+    |     |  74.21GiB | ... |
unallocated|unallocated|     | 125.53MiB | ... |[/html]I'm guessing sda2 is my MacHD, and that I need to set its flag to 'boot'. But I don't recognize the other partitions, and when I untag the 'boot' flag from sda1, it turns into 'msftres', something else I don't recognize.

I am running Ubuntu 8.10, and my Mac OSX was 10.4 (if I remember correctly--it's the OS just before the newest one).

Can someone please help me get my Mac OSX back? While I'm not a complete tech n00b, where partitions and other OSs are concerned I feel rather helpless.

---

### Post by Mazin on 2009-01-10
If Ubuntu had indeed repartitioned your hard drive, then you would have to reinstall OSX.

From what you posted, it looks like everything is still there.  Try booting your Mac with alt held down and see what hard drive icons show up.

---

### Post by partitoman on 2009-01-10
> **Mazin said:**
> If Ubuntu had indeed repartitioned your hard drive, then you would have to reinstall OSX.

From what you posted, it looks like everything is still there.  Try booting your Mac with alt held down and see what hard drive icons show up.
Thanks Mazin, but I can't get any alternative startup methods to work (i.e., holding down a button during startup doesn't do anything, whether it's the alt key or 'c' or 'd' or what have you). Have I somehow messed up the BIOS too?

---

### Post by Mazin on 2009-01-10
It gets problematic from here out.  Your firmware is fine; it's just that the boot loader or something got changed.  Try to see if Disk Utility on your OSX install disc can solve anything.  If not, then you'll have to backup your Mac partition and start over, I'm afraid.

You might be able to cajole [rEFIt]("http://refit.sourceforge.net/doc/c1s1_install.html") (a replacement loader for EFI computers) into booting OSX, but I have no experience with that.

---

### Post by Rog-Mahal on 2009-01-11
I'm not entirely sure, but I don't think you want to set your hfs+ partition to boot. That small fat32 partition is where your efi bootloader lives, and I think you want to keep it that way. What happens when you boot? Do you get any messages? Icons? I had some trouble with bootup when I installed my dual boot setup, it's a pain, but generally pretty fixable.

---

### Post by Mazin on 2009-01-11
Did you try using rEFIt's "sync partition tables" tool?

---

### Post by partitoman on 2009-01-11
> **Mazin said:**
> Did you try using rEFIt's "sync partition tables" tool?

I'm willing to try anything that'll work, but I'm a bit apprehensive about fooling around with things that I'm not at all familiar with, especially as the instructions won't even go into detail, stating simply that only advanced users should attempt this...

You *are* talking about overwriting the EFI with rEFIt, right?

---

### Post by Mazin on 2009-01-11
I was under the impression that a bootable rEFIt disc had tools you could use without actually installing rEFIt.  I could be wrong, though.

---

### Post by partitoman on 2009-01-11
> **Mazin said:**
> I was under the impression that a bootable rEFIt disc had tools you could use without actually installing rEFIt.  I could be wrong, though.

I haven't tried it, but I'm doubtful that I can boot from the rEFIt disc since I can't even boot from the installation disc. Or could I work off the disc image, which I can download from within Ubuntu?

And what would it offer me that GParted can't?

---

### Post by Rog-Mahal on 2009-01-11
You're talking about two very different tools. refit is just an efi bootloader with some additional tools to improve its functionality,. All it does (essentially) is give a gui to your bootup selection. 

Syncing the partition tables is only useful if you have two operating systems installed. I believe it just makes sure that where refit thinks the linux os is and where grub lives are the same. 

That being said, there's no harm in burning the refit rescue cd and seeing what kinds of options it gives you. 

gparted is simply a partition editor, it has nothing to do with the bootup process, it just shrinks, expands, reformats partitions. It won't help you if something with your bootloader was messed up.

What exactly does happen when you turn your computer on?

---

### Post by partitoman on 2009-01-11
Thanks for clearing that up, Rog-Mahal. I think I will try to create a rEFIt disc from Ubuntu.

> **Rog-Mahal said:**
> What exactly does happen when you turn your computer on?

When I turn my computer on, first I get the "on" chime, then the whitish-grey screen, then black screen with a blinking underscore cursor in the upper left corner. That's it. No amount of key presses before, during or after power-on does anything.

Is there anything else that you might find helpful?

---

### Post by cyberdork33 on 2009-01-11
> **Rog-Mahal said:**
> I'm not entirely sure, but I don't think you want to set your hfs+ partition to boot. That small fat32 partition is where your efi bootloader lives, and I think you want to keep it that way.
Well, not exactly, there is actually nothing in there unless you put it there, or is your are doing a firmware update. but you do what to keep the boot flag on the EFI partition. the bootloader is in the firmware.

Actually, it doesn't look like there is anything wrong with your partitions at all!

> **Mazin said:**
> Did you try using rEFIt's "sync partition tables" tool?
I would try this too.

> **partitoman said:**
> I'm willing to try anything that'll work, but I'm a bit apprehensive about fooling around with things that I'm not at all familiar with, especially as the instructions won't even go into detail, stating simply that only advanced users should attempt this...

You *are* talking about overwriting the EFI with rEFIt, right?
rEFIt does not "overwrite" EFI. It is just an executable that your firmware starts and it shows a nice little gui for choosing your OS and provides some tools that can be helpful (like the partition sync tool).

> **Mazin said:**
> I was under the impression that a bootable rEFIt disc had tools you could use without actually installing rEFIt.  I could be wrong, though.Yes you can make a rEFIt CD:
[http://refit.sourceforge.net/doc/c1s5_burning.html](http://refit.sourceforge.net/doc/c1s5_burning.html)

> **partitoman said:**
> And what would it offer me that GParted can't?
Although gparted and rEFIt are completely different types of applications, rEFIt allow you to sync the MBR and GPT partition tables... gparted does not do this.

I would guess that the problem is that you used the startup disk utility in OSX to select booting from the Ubuntu CD... well Ubuntu has not utility to set it back. Holding Alt/Option during the startup process should bring up a menu where you can select what drive to boot from.

---

### Post by partitoman on 2009-01-12
> **cyberdork33 said:**
> 
I would guess that the problem is that you used the startup disk utility in OSX to select booting from the Ubuntu CD... well Ubuntu has not utility to set it back. Holding Alt/Option during the startup process should bring up a menu where you can select what drive to boot from.

This is in fact exactly what had happened, and I'm embarrassed to report that the problem had nothing at all to do with Ubuntu or partition.

Believe it or not, it was a *keyboard* problem. I was not aware of this, but apparently the new thin metal Apple keyboard has an issue with Mac Minis -- it doesn't function before OS bootup. So all I had to do was use another keyboard, and finally press 'Alt/Option' to boot into the harddrive, then use the startup disk utility to set it back to the Mac HD.

And that was it! I can't believe how close I came to taking some drastic measures, including blowing out my entire system.

My apologies for dumping this on the Ubuntu community! Thanks again for all your help.

---

### Post by Mazin on 2009-01-12
I learned something about those fancy thin Apple keyboards. :)
Could you mark this thread as "SOLVED" (I think it's under Thread Tools)?

---

