---
title: "Grub to Floppy During Install"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by confused57 on 2006-06-04
I prefer the "text-install" method, and when I'm asked to install grub, I always choose the mbr.  Rather than doing an install just to find out, if I select "no" when I'm asked, does a menu with an option appear, that allows installing grub onto a floppy to boot the OS into?  I know I could always go into grub/menu.lst and add the entry to boot the OS, if I don't install it to the mbr.

---

### Post by confused57 on 2006-06-04
I was hoping someone would read this who had tried it before.  I was wondering if it was possible to load grub to floppy during install...which if it is, would allow a dual boot without loading grub to the windows mbr.  Maybe just put in the floppy to boot into Ubuntu, with no floppy load into windows?
I'll try it eventually, but hoped someone had already tried it.

---

### Post by catlett on 2006-06-04
Sorry to leave you hanging I hope you didn't try to  email me, as well as post, and think I was being rude (fathers B-Day today)
BTW Yes it will give you an option. It will ask you to put it on ubuntu's partition or a floppy. The floppy will have all the options that a regular grub menu would have i.e. be able to boot to windows.
Actually I would recommend this because you can easily install grub to your mbr after you boot in from the floppy. Once you write the new grub to yoiur mbr you will now have a grub floppy as a failsafe.
Choose not to put grub on the mbr, then choose to put it on a floppy. Once you boot into grub from the floppy open the terminal and enter ```
sudo grub-install /dev/hda
``` Grub will then install to the mbr.

P.S. That is for an ide drive. I don't know how a sata is recognised i.e. is it hda as well?  If you have satas thern you can use the grub specific labeling sudo grub-install (hd0,0)

---

### Post by confused57 on 2006-06-04
catlett,
   Thanks a lot, I wasn't sure about it 'cause I'd never tried to install grub anywhere but the mbr...sounds like another option for someone who doesn't want to install grub onto their mbr until they learn their way around the Linux OS.   Sure saved me a lot of time trying it out for myself.  Having a grub floppy backup sounds like an excellent idea...never know when it would come in handy.

Hope your dad had a Happy Birthday...family has to come first.

Thanks again

---

### Post by netwench on 2006-06-09
Hello,

i'm looking for a clarification on this, if you would please. 

i have winxp on my master drive, i wish to install ubuntu on a separate slave drive.  both are pata. i do not wish to write to the mbr on the windows drive; actually, i'm wondering if it's possible to completely disconnect the windows drive when i put in the ubuntu drive and install ubuntu- will the install solidify the drive "letter" (hda instead of hdb as it should be as a slave?) and does it even matter? i have read other posts here where they told the install not to touch hda but windows was corrupted anyway- i really really don't want to risk this- it's a copy of windows which i've had to call microsoft to activate and i'd really like to avoid doing that again.

i wish to put grub on a floppy only, which i understand can be done with the alternate install cd. so when i put it on a floppy, how will i know what linux has called the drive? hda vs. hdb? 

and is the alternate install cd the same as desktop- as in, graphical and most likely follows all the same instructions that are listed for desktop installs (other than what i choose to change)? 

sorry for such newbie questions...
thanks so much for your help!

---

### Post by confused57 on 2006-06-09
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Check out this thread, it's how I have my system set up and grub is not installed to the mbr of windows.  I think it may be what you're looking for, grub will only be installed on the Ubuntu drive, if you install with the windows drive disconnected...then connect the Ubuntu drive as master and the Windows drive as slave.  Mine automatically boots to Windows, but I can select to boot to Ubuntu in the Grub menu during startup.

You may want to try the Dapper desktop cd, which is the live cd that you can install from using the GUI espresso.   This may be the best method for someone just starting out, and you'll find out if your hardware is compatible with Ubuntu.

The Dapper alternate cd uses a text installer, which is pretty easy to use and it does allow you to specify where to install grub if you're installing it to dualboot with another OS.   I read in another thread that it doesn't offer the option with SATA drives, but yours are PATA so it shouldn't be a problem.

FYI,  if you had both hard drives connected when attempting to install Ubuntu, the primary master drive would be listed as "hda" and the slave drive would be listed as hdb...you would select which drive to install Ubuntu.  Both drives connected during install with the alternate cd, Ubuntu installer would detect the "other" OS and offer to install grub to the mbr of windows...which you don't want to do. 

If you installed Ubuntu as the only drive connected, I don't think it gives you the option of where to install grub.  Connected to the master IDE controller it would be "hda".  Hope this helps, ask if you have any questions...preferably before you start installing.

---

### Post by brentoboy on 2006-06-09
netwench,

fear not
no matter how bad you mess up your mbr, you can repair the windows bootloader.

google "fixmbr" that is a utility that you can use with your windows CD that does nothing more than restore thier bootloader.  in fact, instead of googling it, you could search these forums for it, it is a somewhat common need.

if you want the very smallest amount of headache though, honestly, just install grub to the mbr, I have never seen it have any issues with windows--so long as it tells you before you add grub that it detected a windows installation.

---

