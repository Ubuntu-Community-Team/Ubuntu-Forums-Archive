---
title: "Need Help Destroying Windows!!!"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by unoobu on 2006-05-14
I have been using Ubuntu for about a week now.  I have moved all of my files from my Windows partition to my Ubuntu partition...  I have decided that I have no more need for Windows, as the Linux community offers more than Microsoft, and I can sleep better at night...

Here is my next puzzle:

[IMG]http://www.organizingcollective.com/davedocs/gparted.jpg[/IMG]

My NTFS partition is flagged as the boot partition.  I am affraid that if I reformat this partition to an EXT3 partition, that GRUB will no longer work, and I will have no access to Ubuntu.

What I ultimately want to accomplish is this:  I want to safely delete the NTFS partition, and then take the free space and grow the pre-existing Ubuntu (EXT3) partition to take up that space.

NOTICE:  The EXT3 partition is locked.  Therefore, once I sucessfully delete the NTFS partition, how can I gain access to be able to grow the EXT3 partition?  If this will have to be done using SUDO in the terminal, can someone please give copy and paste commands, as I have not had time to learn them yet?!?

Peace,

uNOOBu

---

### Post by NeoRc on 2006-05-14
You can install the grub to the MBR manually in the linux.
grub> setup (hd0)

So you should first browser the documentation of GRUB to make sure that you can handle it. Then delete the NTFS partition IN the linux, and install the GRUB to the MBR. And then, ahh, everything goes well. You can do anything you wanna do.

---

### Post by adam.tropics on 2006-05-14
If you can backup your personal files to a cd or dvd or network, it may be worth considering a fresh install, with perhaps a seperate /home partition. It makes restoring further down the road a hell of a lot quicker, as it maintains most of your settings etc.

---

### Post by Kvark on 2006-05-14
If you would find that grub is gone so you can't start Ubuntu then you can use the Ubuntu install disk to resture grub by following [this howto]("http://ubuntuforums.org/showthread.php?t=76652").

You can't resize a partition while you are using it. And you can't use your installed Ubuntu without using it's partition. So you will need to use the live CD to resize it.

---

### Post by Sutekh on 2006-05-14
You might also want to check out the [Ubuntu Wiki - Recovering Ubuntu After Installing Windows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

I'm not sure if removing the bootable NTFS partition is the same as removing GRUB from the MBR, but I don't know for sure.  That link (and Kvark's) will set you straight.

I'd also recommend you check out the [GParted Live CD](http://gparted.sourceforge.net/livecd.php) to help you do the removal of the NTFS partition and the growth of the ext3 partition.  Its only 30MB and a useful CD to have lying around.

---

