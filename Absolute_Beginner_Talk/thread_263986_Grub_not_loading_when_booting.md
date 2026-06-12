---
title: "Grub not loading when booting"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by mistywindow on 2006-09-24
I've installed Ubuntu 6.0.6 on a Windows PC as dual boot. Windows is on one of 2 SATA drives. Ubuntu is on a dedicated IDE drive. 
Installation goes smoothly, grub is installing.
When rebooting Windows boots up. Grub does not load.

I suspect that grub is installing on the IDE drive, but that is not the boot disc. Is this likely?

I've installed ubuntu twice with the same result. If I install Acronis OS Selector under Windows, it then picks up the Ubuntu installation and runs grub when Linux is selected as the boot OS.

How can I fix this?

---

### Post by jpkotta on 2006-09-24
> **mistywindow said:**
> I've installed Ubuntu 6.0.6 on a Windows PC as dual boot. Windows is on one of 2 SATA drives. Ubuntu is on a dedicated IDE drive. 
Installation goes smoothly, grub is installing.
When rebooting Windows boots up. Grub does not load.

I suspect that grub is installing on the IDE drive, but that is not the boot disc. Is this likely?

I've installed ubuntu twice with the same result. If I install Acronis OS Selector under Windows, it then picks up the Ubuntu installation and runs grub when Linux is selected as the boot OS.

How can I fix this?

GRUB probably is installing on the IDE drive.  My BIOS does the same thing, and you can't even tell it what HD to boot from.  If you can set your BIOS to boot from the IDE drive, everything should work fine.  Otherwise, I can help you configure it to load on the SATA drives.

OTOH, It sounds like you've already fixed it with this Acronis thing.

---

### Post by mistywindow on 2006-09-24
Thanks jpkotta,

The Acronis OS Selector is painfully slow to start.
I would prefer to boot it using GRUB from the SATA drive if possible.

I'm wondering if I'd be better off creating free space on the boot SATA drive and reinstalling Ubuntu there.

---

### Post by gonegolf on 2006-09-24
Hi, I have somewhat a similar problem.  My installation:

1. SATA: Win XP
2. Primary IDE: DVD Writer (because firmware update requires this to be the primary drive)
3. Secondary IDE: Ubuntu 6.06 on whole partition

I have tried the same thing-tried setting the bios to read first to no avail.  Tried switching on only the the secondary drive but still cannot boot it.

Unfortunately, I do not have Acronis.

Anyone can help? Thanks

---

### Post by Herman on 2006-09-24
We have a MBR in each hard disk, but the BIOS normally only reads the MBR in the first hard disk  for instructions about how to boot the computer up.

Most of the time the hard disk that the BIOS thinks is the first hard disk, and the one Grub calls the first hard disk are the same, but sometimes not.

It won't do any harm to install Grub to  both or all of your hard disk if you want to. You can also install Grub to the first sector of any Linux partition as well.

I would open a terminal and then open a Grub shell from there with a sudo command 'sudo grub'```
sudo grub
``` That will give you a grub shell and you will have a grub> prompt.
The next step is to check what hard disks Grub can see and what Grub calls them, you can use 'Tab completion for that. Just type root (hd    
and leave an empty space after that and then press your Tab key once or twice and you should get a list of your hard drives, and maybe even a list of some of your partitions too. :D
So let's say Grub told you you have an (hd0), a (hd1), and a (hd2).
Probably Grub is already installed in what Grub thinks is your first hard disk, (hd0). Try installing Grub to (hd1) and (hd2) as well and see what happens.
You should also find out for sure which disk and partition Ubuntu is on acccording to Grub, to do that, try typing 'find /boot/grub/menu.lst' ```
find /boot/grub/menu.lst
```You should get an answer like (hd1,0) or something like that. 
Next, you need to tell Grub which is your Ubuntu partition, some computers have several Linux partitions, so Grub doesn't assume anything, it needs to be told for sure which partition will be the 'root' partition for this job. Let's say it's (hd1,0) for example, (your second hard disk, number 1 partition) so you do it like this, 'root (hd1,0)' ```
root (hd1,0)
```Then you install Grub to a MBR, like this, 'setup (hd1)' ```
setup (hd1)

``` After you press 'Enter', Grub should give you some feedback, similar to this, > [FONT=Bitstream Vera Sans Mono]Checking if "/boot/grub/stage1" exists... yes[/FONT]
          [FONT=Bitstream Vera Sans Mono]                                 Checking if "/boot/grub/stage2" exists... yes[/FONT]
          [FONT=Bitstream Vera Sans Mono]                                 Checking if "/boot/grub/e2fs_stage1_5" exists... yes[/FONT]
          [FONT=Bitstream Vera Sans Mono]                                 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  15 sectors are embedded.[/FONT]
          [FONT=Bitstream Vera Sans Mono]                                succeeded[/FONT]
          [FONT=Bitstream Vera Sans Mono]                                 Running "install /boot/grub/stage1 d (hd1) (hd1)1+15 p (hd1,0)/boot/grub/stage[/FONT]
          [FONT=Bitstream Vera Sans Mono]                                2 /boot/grub/menu.lst"... succeeded[/FONT]
          [FONT=Bitstream Vera Sans Mono]                                Done.[/FONT] So you know that Grub is successfully installed in the MBR of number 2 disk now. You can do the same with (hd2) if you like, and even do (hd0) again to make sure. That should fix your problems. :D ...and , oh ,yes, type 'quit' to exit the Grub shell.

By the way, you can actually boot up from a non-first MBR with the right Grub commands too, if you can get a [Grub Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"). I just installed Grub to my MBR in my second disk to test these commands while I'm typing this post up and then I booted my second disk's MBR by chainloading it.  I used 'root (hd1)', and 'chainloader+1' and 'boot', and up came my Grub menu from a different Ubuntu's Grub than the one I have installed in the first disk. :D

Have fun and enjoy yourselves,
Regards, Herman :D

---

### Post by mistywindow on 2006-09-24
Very much appreciated Herman.
I was fairly certain what the problem was.
Now I know how to fix it and fill in a lot of learning blanks to boot - excuse the pitiful pun.
Thanks very much. :grin:

---

### Post by jpkotta on 2006-09-24
Once you figure out what partition is what, you should edit /boot/grub/menu.lst to make your changes permanent.  If you don't edit this file, you will have to redo everything after a kernel update.  See this [page ]("https://help.ubuntu.com/community/GrubHowto?#head-92178081fe4541430c264adfedcca91f4f920512")for details.

---

### Post by mistywindow on 2006-09-26
[FONT="Verdana"]Problem solved for my particular setup::D

The info may be useful to Gonegolf.

Windows mbr is on SATA 1, Ubuntu is writing its mbr to IDE 1.

I can get around this by selecting the appropriate HDD at bootup. With this Abit mobo's BIOS I can press ESC to go into a boot selection menu (not the same as the F8 boot menu).

What I didn't realise until I tried it, is that if I select HDD from that menu, I then get another menu enabling me to select ***which*** HDD.

Voila! I can boot from the IDE drive into GRUB. And it's much quicker than OS Selector.

This is the best of all worlds. I don't have to mess up my Windows mbr with GRUB or OS Selector, I can retain Windows as my default OS and it boots as normal. If I wish to remove/reinstall Ubuntu or Windows, I don't get mbr problems.

I've kept a copy of your solution Herman. Thanks for that, it will be useful to me as a learning tool for future problems - I have a queue of people wanting an Ubuntu installation.
[/FONT]

---

