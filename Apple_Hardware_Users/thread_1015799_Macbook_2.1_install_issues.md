---
title: "Macbook 2.1 install issues"
date: 2008-12-19
forum: Apple Hardware Users
---

### Post by Kingpatzer on 2008-12-19
Downloaded the latest x86 install disk and went to town.

I have one drive /sda which is partitioned with 300G for / and 20 Gig for swap. 

The install goes fine, I see all the pretty graphics and everything works (including my wireless Logitech MX mouse). 

Then it ends, reboots and asks me to remove my CD.

I do so, and I get a file icon in the middle of the screen with a '?' in the middle of it.

I've tried installing a boot loader on sda, sda1 and even hd0 (even though there's only the one drive in the system).

Always the same result.

Any ideas on how to fix this and move forward?

---

### Post by beauman on 2008-12-19
Please boot into Ubuntu (with the LiveCD) and post

```
sudo gparted /dev/sda
``` 


[COLOR="Red"](This is not a malicious command!! Normally you should never execute commands like sudo something or sudo gparted ..., but see the man page for gparted, see also [Announcement about malicious commands]("http://ubuntuforums.org/announcement.php?a=54"))[/COLOR]

For my MacBook it looks like:

  
/dev/sda1        200MB EFI 
/dev/sda2   hfs+ 65GB
/dev/sda3   Swap  1G
/dev/sda4   ext2 75gB

How large is your hard drive, that you have that much disk space? And you need only twice the RAM size for swap space.

You want a dual boot system, right?

You need to install grub into your root partition. You need to sync the GPT with the partition table, using for example rEFIt. And, if you don't want to press the Alt-Key every time you boot, you need a boot manager like rEFIt. See the [Mactel start page]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages"), it features a link to a generic install instructions. 

You tell during the last install step, to install grub to the MBR of the root partition. You can also install grub after the install, but that is also quite dangerous. come back here if you want to know how that works.

Unfortunately, there is no wiki for the MB2-1 for Intrepid. You might try the wiki for MB3-1/Intrepid. If you like to, note things that differ from the wiki for the MB3-1!

---

### Post by Kingpatzer on 2008-12-19
Nope, I am not going for dual boot at this time. I backed up my existing mac stuff to an external drive using carbon copy, and am just going to run Linux for a bit and see how I like it.

The disk drive is 320G. I have 8G ram, so 2x is 16. 

How do I install refit when I, atm, have no OSX?

---

### Post by beauman on 2008-12-19
no idea. sorry. did you look at the [rEFIt pages]("http://refit.sourceforge.net/")?

---

### Post by hyperboloid on 2008-12-19
> **Kingpatzer said:**
> Downloaded the latest x86 install disk and went to town.

I have one drive /sda which is partitioned with 300G for / and 20 Gig for swap. 

The install goes fine, I see all the pretty graphics and everything works (including my wireless Logitech MX mouse). 

Then it ends, reboots and asks me to remove my CD.

I do so, and I get a file icon in the middle of the screen with a '?' in the middle of it.

I've tried installing a boot loader on sda, sda1 and even hd0 (even though there's only the one drive in the system).

Always the same result.

Any ideas on how to fix this and move forward?

I had exactly the same experience when I installed Ubuntu 8.10 single boot on my 4th generation MBP. This is due to a bug in the Ubuntu installer that wipes out the MBR. The bug is well documented all over this forum; see [http://ubuntuforums.org/showthread.php?t=767677]("http://ubuntuforums.org/showthread.php?t=767677"). You need to burn a rEFIt rescue CD (google rEFIt) on another computer, then boot from the rEFIt CD (hold down "C" key while booting with the CD in the drive). Once in rEFIt you will need to re-sync your MBR and then all well be fine.

---

### Post by Kingpatzer on 2008-12-19
> **hyperboloid said:**
> I had exactly the same experience when I installed Ubuntu 8.10 single boot on my 4th generation MBP. This is due to a bug in the Ubuntu installer that wipes out the MBR. The bug is well documented all over this forum; see [http://ubuntuforums.org/showthread.php?t=767677]("http://ubuntuforums.org/showthread.php?t=767677"). You need to burn a rEFIt rescue CD (google rEFIt) on another computer, then boot from the rEFIt CD (hold down "C" key while booting with the CD in the drive). Once in rEFIt you will need to re-sync your MBR and then all well be fine.

Ok, that makes sense - so to followup: how do I get rEFIt onto a CD? There is no ISO that can be downloaded, only a .dmg and a .cdr -- both are mac specific filetypes and I don't have a working mac. I have a PC, but roxio doesn't handle those file types.

---

### Post by hyperboloid on 2008-12-19
> **Kingpatzer said:**
> Ok, that makes sense - so to followup: how do I get rEFIt onto a CD? There is no ISO that can be downloaded, only a .dmg and a .cdr -- both are mac specific filetypes and I don't have a working mac. I have a PC, but roxio doesn't handle those file types.

I used another Ubuntu box to download the CDR iso image, then burned a CD; that worked just fine. So I don't understand your assertion that .cdr is Mac specific.

If Windoze can't handle CDR then try the tar.gz download and unpack it once you get it.

---

### Post by Kingpatzer on 2008-12-19
let's put it his way .. My PC and it's associated software insist it is a mac image :)

All data is 1's and 0's, so in that sense nothing is machine specific, but PC's don't have the user developers that Linux does ;)

---

### Post by hyperboloid on 2008-12-19
> **Kingpatzer said:**
> let's put it his way .. My PC and it's associated software insist it is a mac image :)

All data is 1's and 0's, so in that sense nothing is machine specific, but PC's don't have the user developers that Linux does ;)

I can't help you - I haven't used Windows since 1999. Don't you know anybody with a Mac or a PC running Linux?

---

### Post by cyberdork33 on 2008-12-19
> **Kingpatzer said:**
> Ok, that makes sense - so to followup: how do I get rEFIt onto a CD? There is no ISO that can be downloaded, only a .dmg and a .cdr -- both are mac specific filetypes and I don't have a working mac. I have a PC, but roxio doesn't handle those file types.

roxio should handle it fine, it just thinks it can't. It is just an image file and you could probably rename it to *.img or *.iso and roxio would burn it like normal.

Since you posted this in two places, I answered here:
[http://ubuntuforums.org/showpost.php?p=6400029&postcount=54](http://ubuntuforums.org/showpost.php?p=6400029&postcount=54)

(You shouldn't double post. It makes support confusing and difficult).

Also, if you are going to single-boot, you should convert your hard drive from a GPT disk to a normal MBR (msdos) partition table. You can do this with gparted, but it will wipe out your partitions you currently have!

---

### Post by Rog-Mahal on 2008-12-19
I don't believe refit is totally necessary if you are going to single boot. It would probably speed up your bootup time, but you could just try cyberdork's instructions and not worry about refit at all. Just be prepared for your mac to wait at the grey screen for about 10-15 seconds before grub starts.

Just another option.

---

### Post by cyberdork33 on 2008-12-19
> **Rog-Mahal said:**
> I don't believe refit is totally necessary if you are going to single boot. It would probably speed up your bootup time, but you could just try cyberdork's instructions and not worry about refit at all. Just be prepared for your mac to wait at the grey screen for about 10-15 seconds before grub starts.

Just another option.
and that should be fixable by blessing

---

### Post by hyperboloid on 2008-12-19
> **Rog-Mahal said:**
> I don't believe refit is totally necessary if you are going to single boot. It would probably speed up your bootup time, but you could just try cyberdork's instructions and not worry about refit at all. Just be prepared for your mac to wait at the grey screen for about 10-15 seconds before grub starts.

Just another option.

I don't know - this confuses me. Isn't rEFIt *needed to re-sync the MBR* so the guy can boot? 

That was my experience. On Ubuntu install I blithely chose the option to wipe the HD and install Ubuntu on the entire disk, and got the blinking ? after the install finishes and tries to boot into Ubuntu. I needed a rEFIt rescue CD to re-sync my MBR, and then I was fine. I never installed rEFIt to my HD, because once I fixed the MBR it wasn't needed anymore: as you say, it isn't needed to boot. But I sure needed it to fix the MBR, and that's the guy's problem, if I understand correctly.

---

### Post by pxwpxw on 2008-12-19
> **Kingpatzer said:**
> Nope, I am not going for dual boot at this time. I backed up my existing mac stuff to an external drive using carbon copy, and am just going to run Linux for a bit and see how I like it.

The disk drive is 320G. I have 8G ram, so 2x is 16. 

How do I install refit when I, atm, have no OSX?

Use the ubuntu live cd
```

sudo apt-get install refit
sudo gptsync /dev/sda

```
You need gptsync because you are using a hybrid GPT/MBR disk if I read the thread correctly.
The flashing folder is because you have no alternative to booting ubuntu (no macosx).

---

### Post by anujseth on 2008-12-20
this is a bit out of context, sorry, but how did you get 8G ram on a macbook 2,1. i have the same machine and it does not go above 3GB, officially atleast. If you stick in 4G's then you get extra video memory but not 4G ram.

---

### Post by cyberdork33 on 2008-12-22
> **anujseth said:**
> this is a bit out of context, sorry, but how did you get 8G ram on a macbook 2,1. i have the same machine and it does not go above 3GB, officially atleast. If you stick in 4G's then you get extra video memory but not 4G ram.

Are you on a 64bit OS?

---

### Post by anujseth on 2008-12-22
@cyberdork33

yes Leopard.

---

### Post by cyberdork33 on 2008-12-22
> **anujseth said:**
> @cyberdork33

yes Leopard.

Well, then technically, no it's not a 64bit OS, but that is another topic. ;)

I see mixed reports for the mid-2007 macbooks and 3gb or 4gb of RAM, but nothing more than that.

---

### Post by anujseth on 2008-12-22
> Well, then technically, no it's not a 64bit OS, but that is another topic. 

yup the kernel is 32bit.

i haven't tried the extra ram on a 64bit linux install, but yes as you say mixed reports is what i've also found.

---

### Post by cyberdork33 on 2008-12-22
> **anujseth said:**
> yup the kernel is 32bit.

i haven't tried the extra ram on a 64bit linux install, but yes as you say mixed reports is what i've also found.

I don't think it will make a difference as I believe it is a limitation in the controller. I thought maybe there was a firmware update that fixed that as it seems to work fine on newer machines, but I didn't find anything.

---

### Post by anujseth on 2008-12-22
> I don't think it will make a difference as I believe it is a limitation in the controller. I thought maybe there was a firmware update that fixed that as it seems to work fine on newer machines, but I didn't find anything.

true, but op here says he uses 8GB on a 2,1 so was just curious.

---

