---
title: "Running an app from another HDA"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Dilbert59 on 2007-10-26
I made the mistake of installing 7.10 the other day.  I reinstalled 7.4 from the LiveCD into a partition that used to be Suse10.0, which I blew up when I tried to install Suse10.2....anyhow...My old Evolution email program and a lot of old mail, is still on the partition with the hosed 7.10.  My machine shows HDA1, which contains the dual boot WinXP, HDA3, the working Ubuntu 7.4, and HDA4, the non-working Ubuntu 7.10.

I suspect I hosed the 7.10 when I selected the restricted mode Nvidia driver option.  If I could unset that option I'd know for sure.  Haven't figured out how to do that from the recovery mode console.  

I see three alternatives (in order of increasing pain): 1) recover the existing 7.10 install by unsetting the Nvidia driver if this doesn't involve some arcane and extensive use of the command line; 

2) download a liveCD of 7.10 and install over the blown 7.10 if this won't erase all other contents in the partition (I've done this any number of times with Windows); 

and 3) suck it up, accept the loss of the emails, and don't ever use Linux for anything important again, since, at least being an MCSE, I can fix the screw ups in Windows.

Personally, I'd like to avoid option 3.  Any ideas on executing 1 or 2 successfully?

---

### Post by JKyleOKC on 2007-10-26
When you boot into the 7.04 on HDA3, open a terminal window and issue these commands:
    sudo md ~/mnt/710
    sudo mount -t ext3 /dev/hda4 ~/mnt/710

This should create a directory in your home directory named "mnt" and within it a subdirectory named "710" which, after the second command, should contain the file system of the 7.10 partition. You can verify this by closing the terminal window and opening your home directory, then navigating down to the 710 directory. If all is well so far, navigate on into the "etc" directory of the 710 filesystem, and from there to its "X11" subdirectory. Within that directory you should find a file named "xorg.conf" which you should open with your favorite text editor. Find the line "Section "Device"" and a couple of lines later the line that starts "Driver". The driver name, in quotes, may be nvidia or nv; change it to "vesa" for the generic driver, or make it the same as you have in the same file on your 7.04 partition. Then save the file, unmount the ~/mnt/710 device, and reboot to the 7.10 partition.

I don't know that this will solve the problem because I don't know if it's the driver causing your troubles, but this is how to access data in a different partition. Hope it helps!

---

