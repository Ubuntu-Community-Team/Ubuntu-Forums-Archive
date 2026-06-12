---
title: "Installing 8.04 on my MacBook - No bootable device error"
date: 2008-05-01
forum: Apple Hardware Users
---

### Post by Moses 410 on 2008-05-01
Hey, I'm trying to install ubuntu 8.04 on my MacBook2,1. I have the live CD and here is what I've done so far.

-Used Boot Camp to partition my harddrive. Gave 'windows' 10 gigs.
-put the live CD in, restarted holding down 'C' went to the ubuntu menu thing. Selected 'Install Ubuntu.'
-Went through the first few steps, language, keyboard, etc.
-At my partition menu I:
-Deleted /dev/sda3 (My 10GB windows partition)
-Created new swap partition: /dev/sda3  swap 936MB
-Created new ext3 partition: /dev/sda4  ext3 9500MB mounted at '/'

-So my partition table looks like this:
              type | mount | size
/dev/sda
   /dev/sda1   fat32         209MB
   /dev/sda2   hfs+          109387MB
   /dev/sda3   swap          936MB
   /dev/sda4   ext3   /      9500MB

-The installation proceeds as normal and it tells me to restart
-I click the restart button, it restarts, ubuntu loads.
- my live CD pops out and it tells me to 'remove the disk, close the tray (if any) and press enter.'
-I press enter and it restarts again.  It loads up to my EFI (rEFIt) I can choose Mac OSX or Linux, I choose Linux and press enter.
-A black screen comes up with white text across the top that says: 'No bootable device --
   insert boot disk and press any key.'
-Pressing keys doesn't do anything. I put the live CD in and still nothing.

If anyone could help me out here I'd really appreciate it.
Maybe I'm just missing something but I've read and reread the guide and cant figure it out, it seems as though I've done everything it told me to.

Thanks alot guys

---

### Post by jnev on 2008-05-01
I'm getting the same problem with mymacbook pro. the only way I can get it to boot is my booting off the ubuntu cd and then telling it to boot off the hd.

---

### Post by avtolle on 2008-05-01
Would this be of any help to either of you?
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by SiduSahib on 2008-06-04
well first install the reFit program
then partition with boot camp and then install from live cd.
after installing reboot, hold down the option key and go to ur mac.
install refit into ur computer and then run the partition tool from refit while booting after restart.
it works for me. thanks ubuntu users.

---

### Post by MichaelSwengel on 2008-06-10
Hey guys. I've been struggling all day to fix this dang error. AT LAST I found the solution. All I had to do was tell rEFIt to update the MBR. It's the (I think) second icon on the bottom row of the loader.

Ubuntu now loads perfectly on my Macbook Pro.:guitar:

Let me know if this works for you.

---

### Post by cyberdork33 on 2008-06-10
> **MichaelSwengel said:**
> Hey guys. I've been struggling all day to fix this dang error. AT LAST I found the solution. All I had to do was tell rEFIt to update the MBR. It's the (I think) second icon on the bottom row of the loader.

Ubuntu now loads perfectly on my Macbook Pro.:guitar:

Let me know if this works for you.
This is all detailed in the third post.

---

### Post by MichaelSwengel on 2008-06-10
> **cyberdork33 said:**
> This is all detailed in the third post.

Oh. haha.](*,)

---

