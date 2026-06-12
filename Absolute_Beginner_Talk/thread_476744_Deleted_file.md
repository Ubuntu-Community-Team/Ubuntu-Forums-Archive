---
title: "Deleted file"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Jimmy McKellar on 2007-06-17
Hi

I am new to Ubuntu but have managed to load it to a hard disk which is partitioned for XP and Ubuntu (it defaults to Ubuntu).  All was going well, I had managed to load a Samsung driver for an MFD (Multi Functional Device - that is a scanner, copier, printer) then I turned my attention to a spinning desktop like Beryl.  Though I used the Nvidia driver.  It gradually dawned on me the Nvidia driver was not all that stable and the screen a but shaky so I decided to delete the driver to get back to the original.  In retrospect this was not the best decision I have ever made as the Ubuntu will boot but gives a white screen with nowhere to navigate to.

I was wondering if anyone could advise me on one of two strategies - 1 how could I get the file back, undelete?  Or even restore the Ubuntu graphics drivers from the bootable CD?  Or 2, how could I reload everything without deleting the XP (my wife uses that!)  The problem being there are two partitions, one for the system and one for the Swap thing?

I am not very familiar with the way this system works so if you respond I may have to ask some really simple questions like "How do I log on with all rights from a boot disk.  Oh and how do I know which partition it is I am overwriting?  Swap or flle system or even XP?

Please note I may be slow to respond as I will have to try everything out first and I procede slowly when I am not sure.

Regards
Jimmy

---

### Post by moffa on 2007-06-17
Firstly, welcome.

To restore your original driver, go to System > Administration > Restricted Drivers Manager.  You can then uncheck the nvdia driver and go back to the default driver.

To modify your partitions, I recommend using gparted (Gnome Partition Manager).  You can install it from the Applications > Add/Remove meu.  You might need to install the NTFS Configuration Tool program as well to work with the NTFS partition.

(Edit: If you don't see the programs, go to preferences and enable all the categories)

Working with Gparted is pretty intuitive if you've used partioning programs before.

I highly recommend you backup your critical data to a cd before you start fooling around just in case.

---

### Post by Happy_Man on 2007-06-17
'tis quite easy, no reinstalling required. Go into recovery mode upon boot (from GRUB), and wait for it to ask you to login. Do so, and then enter the following command:
```
sudo dpkg-reconfigure xserver-xorg
```

Choose all the defaults until you get to the screen with a long list of drivers. Scroll to select "vesa", spacebar to select, keep going until it finishes. Then enter ```
/etc/init.d/gdm start
```. Hopefully, everything will be alright!

---

### Post by Jimmy McKellar on 2007-06-17
> **moffa said:**
> Firstly, welcome.

To restore your original driver, go to System > Administration > Restricted Drivers Manager.  You can then uncheck the nvdia driver and go back to the default driver.

   Jimmy - This may sound easy but I do not know how to get there from the CD booted system.  IE after I boot from the CD where do I go?

To modify your partitions, I recommend using gparted (Gnome Partition Manager).  You can install it from the Applications > Add/Remove meu.  You might need to install the NTFS Configuration Tool program as well to work with the NTFS partition.

  Jimmy - This bit I understant - partitions I am more familiar with but not Linux.

(Edit: If you don't see the programs, go to preferences and enable all the categories)

Working with Gparted is pretty intuitive if you've used partioning programs before.

I highly recommend you backup your critical data to a cd before you start fooling around just in case.  

  Jimmy - I really do not want to upset the XP installation but nor do I want to try to back it up. My Data is stored on a separate disk and backed up to yet another partition on the disk with the operating systems.

I suppose what I am asking is once booted from the CD how do I get to System > Administration > Restricted Drivers Manager on the hard disk?

Regards
Jimmy

---

### Post by Jimmy McKellar on 2007-06-17
> **Happy_Man said:**
> 'tis quite easy, no reinstalling required. Go into recovery mode upon boot (from GRUB), and wait for it to ask you to login. Do so, and then enter the following command:
```
sudo dpkg-reconfigure xserver-xorg
```

Choose all the defaults until you get to the screen with a long list of drivers. Scroll to select "vesa", spacebar to select, keep going until it finishes. Then enter ```
/etc/init.d/gdm start
```. Hopefully, everything will be alright!


Jimmy - Ah, not quite so simple as the recovery mode has the same problem!  I tried that one.  Could I possibly use those codes after booting from the origina Ubuntu CD?  If so how would I go about it?

Regards
Jimmy

---

### Post by quinnten83 on 2007-06-17
> **moffa said:**
> Firstly, welcome.

To restore your original driver, go to System > Administration > Restricted Drivers Manager.  You can then uncheck the nvdia driver and go back to the default driver.

To modify your partitions, I recommend using gparted (Gnome Partition Manager).  You can install it from the Applications > Add/Remove meu.  You might need to install the NTFS Configuration Tool program as well to work with the NTFS partition.

(Edit: If you don't see the programs, go to preferences and enable all the categories)

Working with Gparted is pretty intuitive if you've used partioning programs before.

I highly recommend you backup your critical data to a cd before you start fooling around just in case.

Uhm, he doesn't get the graphical interface to start up. He broke his X.
I not sure if this will work, but i think you should be able to copy the xorg.conf from the live CD to the desktop. That should give you the default.

---

### Post by Jimmy McKellar on 2007-06-17
> **quinnten83 said:**
> Uhm, he doesn't get the graphical interface to start up. He broke his X.
I not sure if this will work, but i think you should be able to copy the xorg.conf from the live CD to the desktop. That should give you the default.

Jimmy - Ah, now you are talking, but from where to where?  Oh and do I need to be logged in as somethink like a supervisor.  You can tell I am new to this.

PS I am having difficulty finding all these responses is there a trick to following a thread?

Regards
Jimmy

---

### Post by moffa on 2007-06-17
Can you try pressing Ctrl-Alt-F2 when you see that white screen.  Hopefully you'll see: Ubuntu 7.04 computername tty2

try logging in and then run the "sudo dpkg-reconfigure xserver-xorg" command.

---

### Post by Jimmy McKellar on 2007-06-17
> **moffa said:**
> Can you try pressing Ctrl-Alt-F2 when you see that white screen.  Hopefully you'll see: Ubuntu 7.04 computername tty2

try logging in and then run the "sudo dpkg-reconfigure xserver-xorg" command.

Jimmy - Thank you I will give that a go.  In the meantime I have been thinking - would it be possible to copy from a working version of Ubuntu the whole directory/file and transport it on a pen drive to paste it into the appropriate place.  I will consider this more once I have tried what your suggest.

Regards
Jimmy

---

### Post by silverglade00 on 2007-06-17
removed because I re-read the thread and realized my answer would not work

---

### Post by moffa on 2007-06-17
> **Jimmy McKellar said:**
> Jimmy - Thank you I will give that a go.  In the meantime I have been thinking - would it be possible to copy from a working version of Ubuntu the whole directory/file and transport it on a pen drive to paste it into the appropriate place.  I will consider this more once I have tried what your suggest.

Regards
Jimmy

Yes, you can from a live cd.  You'd have to mount your partition though to get it working.  It would probably be easier to reinstall though at this point.  Just make sure you don't select "Use the entire disk"

---

### Post by Jimmy McKellar on 2007-06-18
> **moffa said:**
> Yes, you can from a live cd.  You'd have to mount your partition though to get it working.  It would probably be easier to reinstall though at this point.  Just make sure you don't select "Use the entire disk"

Jimmy - Right, I tried what you suggested with the Ctl Alt and F2 and that did indeed get me to where you said it would.  However my knowledge is poor so I probably answered all the questions wrongly so that I think it is, now, never going to work.  So I am resigned to reloading Ubuntu in its entirity.

One slight concern is that if I use the entire disk it will overwrite my XP - I have already done that once so I do not really want to do it again.  It took me a week to get it all up and running to my satisfaction and my confidence took a knock!!!

I think what I will try is to delete the partitions which have Ubuntu and then use the free space to load it afresh.  On the other hand I do not feel quite confident enough nor convinced this will work.  If all else fails I do have the spare PC with Ubuntu on it for playing around with.

Thank you for all your help and I will post an update if I ever resolve it.

I think I learned quite a lot during this short exercise but there is still a lot to know.

Regards
Jimmy

---

### Post by Jimmy McKellar on 2007-06-19
> **Jimmy McKellar said:**
> Jimmy - Right, I tried what you suggested with the Ctl Alt and F2 and that did indeed get me to where you said it would.  However my knowledge is poor so I probably answered all the questions wrongly so that I think it is, now, never going to work.  So I am resigned to reloading Ubuntu in its entirity.

One slight concern is that if I use the entire disk it will overwrite my XP - I have already done that once so I do not really want to do it again.  It took me a week to get it all up and running to my satisfaction and my confidence took a knock!!!

I think what I will try is to delete the partitions which have Ubuntu and then use the free space to load it afresh.  On the other hand I do not feel quite confident enough nor convinced this will work.  If all else fails I do have the spare PC with Ubuntu on it for playing around with.

Thank you for all your help and I will post an update if I ever resolve it.

I think I learned quite a lot during this short exercise but there is still a lot to know.

Regards
Jimmy

Jimmy - Well I tried to reload Ubuntu but it overwrote the XP for the second time.  Woe!  I have now reloaded it on my spare PC and cannot remember how I managed to load the Samsung Driver for my MFP.  No doubt I will get it in the end but it is not easy.

Once again thank to everyone for all their assistance lets hope I get it all sorted.

Regards
Jimmy

---

