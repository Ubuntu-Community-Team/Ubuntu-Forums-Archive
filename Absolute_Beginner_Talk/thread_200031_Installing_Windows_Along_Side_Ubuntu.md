---
title: "Installing Windows Along Side Ubuntu"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by Steggy on 2006-06-19
Hello all,

Okay, I've searched around quite a bit, and what I have found is a bunch of tutorials dealing with how to install Ubuntu/Linux on a computer that already has Windows on it, and getting it to dual boot. What I want to know is how to install Windows (specifically, Windows XP) on a computer with Ubuntu, and let them dual boot.

Right now, I can't figure out how to even get Windows to install at all. When I get the partitions set up in the Windows installer, it then goes to install Windows but gives me an error about the MBR, and not being able to write to it. I don't want Windows to mess up my Ubuntu installation, and I want GRUB to control the boot process, as Ubuntu is and will be my primary OS.

Has any one else had to deal with this? How did you get it to work? Or, is there a tutorial for this out there somewhere that I just can't find?

Thank you in advance :D

---

### Post by jason.b.c on 2006-06-19
> it then goes to install Windows but gives me an error about the MBR, and not being able to write to it. I don't want Windows to mess up my Ubuntu installation, and I want GRUB to control the boot process,

I think that you will have to reinstall grub..#-o

---

### Post by DarthMandeep on 2006-06-19
Dual-booting by installing Windows after Linux can be done easily, but it requires a couple more steps than the usual method of installing Windows first.

I'm sure the vast majority of Windows users aren't dual-booting, so Microsoft expects that Windows will be the only OS installed on a computer. Because of this, Windows expects to have the ability to overwrite your mbr, and as far as I know, requires it. So when you install Windows, it will wipe Grub from the mbr and you'll lose the ability to boot Linux for a short time.

Make sure your BIOS isn't set to write-protect the mbr, and try installing Windows again. If there's no write-protect option and Windows still won't install, you may need to format the mbr. To do that you'd use the recovery console in the Windows setup. That should allow you to install.

Once you're done installing Windows, you won't be able to boot into Linux. All you need to do to fix that is load up your liveCD, and mount your Linux partition. Then you can use chroot to get inside that partition and setup Grub to take over your mbr again, letting you boot whatever OS you want.

I don't recall the exact commands that you'd need to reinstall Grub in the mbr, as whenever I do this I just look through the manpage and try things till it works. I googled and the end of this page might help with that: [http://gentoo-wiki.com/HOWTO_Install_Windows_after_Gentoo](http://gentoo-wiki.com/HOWTO_Install_Windows_after_Gentoo)

---

### Post by Sasquatch2000 on 2006-06-19
Is there a quick step-by-step anywhere to tell how to set up a PC to boot from Windows or Linux and allow one to choose at boot time? This would be either a shared hard drive, or from two hard drives.  Either way, I would like to be able to have at least one shared directory (volume?) between both operating systems.

Thanks.

---

### Post by r4ik on 2006-06-19
Found this  [http://ubuntuforums.org/showthread.php?t=76652](http://ubuntuforums.org/showthread.php?t=76652)
Please give it a read and decide to go for it or not.
Best of luck !

1. Boot your computer up with Ubuntu CD
2. Go through all the process until you reach "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

Good luck!.

---

