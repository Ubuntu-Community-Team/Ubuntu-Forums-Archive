---
title: "B&amp;W G3 Installer fails at 99%"
date: 2007-03-16
forum: Apple PPC Users
---

### Post by cellseven on 2007-03-16
I tried 6.10 first, then tried 6.06.1 next for my old G3.  The installer gets to yaboot and goes downhill from there.  And yes, I know your reading this going "SEARCH THE FORUMS", but I have and didn't find any posts that relate totally, just sort of.

Would it be better not going the route to boot to live cd and just go command line?  Or go in via live cd, open terminal and starting there?

Being honest I am a n00b as I haven't really touched *nix, beyond some minor server maintenance and system commands on my Tiger box, in almost a decade.

---

### Post by grazie on 2007-03-16
If the installation failed at 99%, you're almost done. B&W Powermacs are well known for the weird IDE config, but Ubuntu usually copes without problems. Do you know whether you have IDE or SCSI disks or maybe both? You could set up yaboot manually using the live cd. Details are give [here]("http://www.ubuntuforums.org/showthread.php?t=380424") and in other threads, If you need further assistance, boot the live cd and in a terminal
```
$ sudo mac-fdisk -l
```
Post the output to this thread. If you know how to get to /etc/fstab and /etc/yaboot.conf post those as well.

---

### Post by cellseven on 2007-03-16
I rebooted and couldn't log in, the kernal wasn't kosher so to speak.  I instead downloaded Xubuntu's alternate install image last night, do you think that may work better or should I sit through another install attempt with Ubuntu and try these alternates?

Oh and this is an IDE machine, Yosemite 400MHz G3.  It's a first rev motherboard that will not run 10.3 or up, I plan to set it up as a testing server as I like to keep my production box free of unnecessary tasks.

---

### Post by odelay on 2007-05-09
I tried installing Feisty Server on a 400 Mhz B&W Powermac G3.  Everything went fine until the yaboot step.

I have two SCSI drives installed.  I tried installing Feisty on the one *not* containing the OS X install.  Will having OS X on a separate drive (the main drive) screw up yaboot?

Thanks.

---

### Post by stmiller on 2007-05-09
Yeah there seems to be a possibly bug with the installer with yaboot and choosing manual partitioning.

After installing, (BUT before rebooting!)  press Ctrl+Alt+F1 (or F2, F3, etc.) to get to a terminal. And then run

$ sudo yabootconf

see if that will create the /etc/yaboot.conf file. Make sure it is then written to the boot partition by running

$ sudo ybin -v

---

### Post by odelay on 2007-05-09
OK...well know that I got a better understanding of my situation I was able to get my foot in the door.

I mispoke when I said SCIS drives (which is how ubuntu identified them).  I forgot since it's been so long, but I actually have 2 ATA drives connected via a PCI card.  Due to some hardware bug, you weren't able to add new, larger drives to the B&W Powermac G3 without using this PCI card.  Unfortunately, I couldn't get yaboot to work with the PCI card.

So I dug up the original 6 GB drive that works without the PCI card and I was able to instal Feisty Server without a hitch.  I might try later going back and adding the 2 ATA's as Ubuntu seemed to detect them fine, I just couldn't use them as the main install drive.

A point to note: I didn't see **stmiller's** advice until after installing the old drive...so it very well could work too.  I'm a little hesitant to start over now that everything is up and running, but I might if I get the time.  No sense is using 3 drives instead of 2.

Thanks.

---

