---
title: "[SOLVED] Help! Want to Install Ubuntu to USB Ext HD with Linux OS"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by aonegodman on 2007-12-10
Everybody has talked about it, but I can't seem to narrow it down to my problem. I used the LiveCD of "Gutsy" to install Ubuntu to my External USB WD 250 MyBook HD. My goal was to create a stand-alone bootable Linux OS with Ubuntu destro so when I started my computer I would use the CMOS setup Boot Menu to decide when I wanted to go to WIN XP or directly to Ubuntu 7.10. I followed the install prompts choosing to use my USB ext HD with single partition. It allowed me to make all the choices except where and if to use GRUB. It automatically placed it on my INT HD0 MBR. Luckily I always boot to WIN XP from a write protected Floppy and not the HD since GRUB overwrites MS MBR. I know this after trying to boot and run Ubuntu first time on my EXT USB HD and getting "No operating system found". Next, after realizing that GRUB was installed on my INT hd0 I removed my Floppy Boot Disk and let it boot there. Yep, GRUB was there giving me the "Error 21" since it no longer sees my EXT USB HD device. So now I have a corrupted MS MBR that must be fixed in order to Boot to WIN XP on my INT HD and a EXT USB HD with no OS that won't boot either. Can you feel the frustration? I know someone has the answer and I appreciate your help. I was very impressed with Ubuntu and look forward to making it my primary OS but I can't totally abandon WIN XP yet. My goal is to place it on the EXT USB HD and use it like a portable bootable OS Flash Drive, is this possible?

AMD Athlon XP +1800 CPU, 1024mb, hd0 40G, hd1 40G, Ext USB 250G.

---

### Post by Xbehave on 2007-12-11
IIRC under advanced options on the installer you can change where grub installs. 
Im no grun expert but i think the command you want to run
grub-install <hd name grub style>
but you might want too have a google about  grub-install 

fixing windows should be fairly easy just have a look around these forums

---

### Post by skymera on 2007-12-11
im also thinking of installing it to a usb hard drive

as im fed up with my mum's suck-ish Vista >_<

---

### Post by aonegodman on 2007-12-11
Thanks for reply Xbehave. I just learned how to use sudo about 5 minutes ago and checked my dev's. Here's what I got back:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x763e763e

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4997    40138371    7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f1e8f1e

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4866    39086113+   7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30213   242685891   83  Linux
/dev/sda2           30214       30401     1510110    5  Extended
/dev/sda5           30214       30401     1510078+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

as you can see there appears to be a boot sector on my USB Ext drive that is listed as /dev/sda1. I want to boot and run Linux on this /dev from either my BIOS boot menu(my comp can boot USB) or by a floppy startup disk. Now WIN XP no longer sees this drive in Windows. It used to be listed as H:\. But I used the LiveCD to boot and then found that my EXT USB drive was recognized. I looked on the drive and find that GRUB is there, the 1.5 and 2 is there, linux system is there. Why won't it boot?

You know I'd be happy just using the LiveCD all the time if it wasn't so slow on startup and if I could keep the changes and tweaks I make each time. Thanks to all for help and comments.
:)

---

### Post by aonegodman on 2007-12-12
*BUMP*

Thinking about trying the suggestion of opening the box and discon the two INT HD's, restaring, go to BIOS, change Boot Seq to 1. Cd_ROM, 2. USB HD WD 2500. Save BIOS. Restart again, boot up the LiveCD, run the install Ubuntu. Will install on my USB Ext HD. Right?

Shut down, open box, replug 2 Int HD back on controller interface, restart computer, go in to BIOS reconfig as needed to boot sequence, save. Should work. Will let you know.

---

### Post by GeorgiaBoot on 2007-12-12
I suggest you reformat your external Drive and start all over again. Here is an outlined tutorial I made that will get it installed without problems. 

Also when you write skip lines ever so often cause it is hard to read your post. Follow exactly and you will get what you want.





Things you will need:

    * Ubuntu Linux (Free) [http://www.ubuntu.com/](http://www.ubuntu.com/)
    * A External Hard Drive
    * A Windows Machine, should work on Vista as well
    * A Little Time and Patience

Prep work:

    * 1. Download the LiveCD iso and burn to CD. Or have Ubuntu Ship you one for (Free).
    * 2. Prep your USB drive by deleting all partitions, no matter what kind they are.
    * 3. Disconnect your internal hard drive(s). This is Key
    * 4. Change your system BIOS boot priority by whatever procedure required for your specific hardware, to:
    * 1. CD
    * 2. USB
    * 3. Hard drive. 

If you cannot set the USB, because your motherboard is too old, this entire method will not work for you.

    * 5. Connect the USB drive
    * 6. Insert the LiveCD and boot your system
    * 7. When the Gnome desktop is visible and the Boot is complete select the following pull-downs from the menu:

System > Preferences > Removable drives & media.

    * 8. In the Removable drives & media window deselect:
    * * Mount removable drives when hot-plugged
    * * Mount Removable Media When Inserted
    * * Browse Removable Media When Inserted

    * 9. Close this window.
    * 10. Select the Install Ubuntu Icon and run through the install routine steps. When you get to the step regarding the hard drive, the easiest method is to select Use Entire Disk. You can partition out any space you require later.

    * 11. Run the installation. Even though the system says it will install GRUB to (hd0) the only drive connected is the USB drive, and it will place it in the right spot. Choosing sda or anything of that nature is not required by the new install cd.
    * 12. Restart the system when it is done.

Enjoy

---

### Post by jken146 on 2007-12-12
If you want to restore the original Windows bootloader you need to do the following (assuming it's XP):

1. Insert your XP install CD.

2. Boot from that CD and press R at the appropriate point to recover an XP installation.

3. At the command prompt type ```
fixmbr
```

---

### Post by aonegodman on 2007-12-13
Thank you "Georgia Boot", this is my project for today.

Thank you "jken146", been there and done that already. GRUB messed up my MBR on my first attempt.

My goal is 2 seperate OS systems(non interfaced) on same computer. Thanks to all for your reply and help.

---

### Post by aonegodman on 2007-12-13
Looks like I did it. Ubuntu booted up from USB Ext Drive without the LiveCD. :)

Started a little slower, but what the hey! Now I can save changes and modify . . .

But that brings me to next immediate problem - system default password?

I need to make some "administrative" changes and I don't know the password. 

It's not the one install let me choose when I did it. I'll go search the forum.

But thanks to all that I've gotten this far.

Oh - I'd place a [Solved] on the header of this thread, but I don't know how.

---

### Post by jken146 on 2007-12-13
The password for sudo is the one you chose when you installed.  If for some reason it doesn't work you can reset it.  Boot into recovery mode and type ```
passwd <your-user-name>
```  Then enter your new password.

[Solved] is in Thread Tools in the top right corner of the page.

---

### Post by Huss on 2007-12-13
Ah, I'm amazed to find a group of people working on this at the same time as me. 

I have been trying to install Ubuntu on a USB HD for a while now - and have fixed my MBRecord a few times along the way. I like the idea of booting without the internal HD connected - I would've never thought of it. I had a problem, though, when I followed your installation steps. I found that the live CD would not fully load without my internal HD attached. I can choose from the Ubuntu boot options, and the loading bar makes a showing - but it collapses to propt after that.

So far, I have:
- Double checked that the steps were followed
- Booted with the internal HD attached until the live CD was working and then removed it. When I did this I was able to deselect all the removable media options but it froze after clicking the "install icon" - tried to scan harddrives and then ...

Now I am going to remove the internal HD just after the install wizard has scanned my HDs and will report back.

... ...

---

### Post by Huss on 2007-12-13
Tried all combinations of HD removal that I can think of and it's no there yet.

Will post back if any positive results

---

### Post by Huss on 2007-12-21
Ubuntu installed on my USB HD with no worries. ;)

---

