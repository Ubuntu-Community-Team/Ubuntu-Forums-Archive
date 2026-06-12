---
title: "How-To: Grub, Windows XP, and the MBR"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by Apple 101 on 2006-07-29
This short guide is designed to help users boot into Windows XP, Ubuntu and other operating systems from the NT boot loader without replacing their Master Boot Record.

For example, you may have two separate hard drives.  One has Windows XP installed, and the other will be used for Ubuntu or another operating system.

This guide focuses on Ubuntu and the use of the floppy disk, but it can be easily adapted for other distributions.

1. Go through the Ubuntu installation process, making sure to install GRUB to a floppy disk, not the MBR*.

2. Complete the installation and reboot into Windows.  Download [DD for Windows]("http://www.chrysocome.net/dd") and extract it to a folder.

3. In Windows: Start --> Run --> cmd.  Navigate to the folder you extracted the 'DD for Windows' programme.

4. Insert the floppy disk.  Copy and paste the following text directly into the command prompt: *dd bs=512 count=1 if=\\?\Device\Floppy0 of=C:\ubuntu.lnx*.  This will automatically place the boot file in C:\.  Close the command prompt window.

5. In Windows: Start --> Run --> *notepad C:\boot.ini*

6. Add in the following lines under the [operating systems] heading: *C:\ubuntu.lnx="Ubuntu Linux 6.06"*.  Save the file and close notepad.

Now Ubuntu (or another Linux distribution) will be available for bootup from the Windows XP NT boot loader.

*GRUB can actually be installed to the MBR.  This method takes slightly longer.  Instructions to follow.

---

### Post by rowanparker on 2006-07-29
Nice howto, but shouldn't it be in the How-To section?

---

### Post by Apple 101 on 2006-07-29
It should be... I'll put it there when I finish the final section.

---

### Post by rowanparker on 2006-07-29
OK.
Good luck with it.

Rowan.

---

### Post by LaoziSailor on 2008-04-11
After a grueling three days -- my Grub kept coming up with msg 17 -- I finally was able to boot Partition Magic and in DOS mode able to erase all traces (except MBR) from my **single** 100MB HD split into 50-50 for Ubuntu. I know have downgraded to Ubuntu 6.06 Desktop. This was after several unsuccessful attempts but no matter, I'm almost where I left off after partitioning my laptop and installing "Gutsy Gibbon" which was working fine for a while until I scr*wed it up somehow.
> **Apple 101 said:**
> [SIZE="1"]This short guide is designed to help users boot into Windows XP, Ubuntu and other operating systems from the NT boot loader without replacing their Master Boot Record.

For example, you may have two separate hard drives.  One has Windows XP installed, and the other will be used for Ubuntu or another operating system.

This guide focuses on Ubuntu and the use of the floppy disk, but it can be easily adapted for other distributions.

1. Go through the Ubuntu installation process, making sure to install GRUB to a floppy disk, not the MBR*.

2. Complete the installation and reboot into Windows.  Download [DD for Windows]("http://www.chrysocome.net/dd") and extract it to a folder.

3. In Windows: Start --> Run --> cmd.  Navigate to the folder you extracted the 'DD for Windows' programme.

4. Insert the floppy disk.  Copy and paste the following text directly into the command prompt: *dd bs=512 count=1 if=\\?\Device\Floppy0 of=C:\ubuntu.lnx*.  This will automatically place the boot file in C:\.  Close the command prompt window.

5. In Windows: Start --> Run --> *notepad C:\boot.ini*

6. Add in the following lines under the [operating systems] heading: *C:\ubuntu.lnx="Ubuntu Linux 6.06"*.  Save the file and close notepad.

Now Ubuntu (or another Linux distribution) will be available for bootup from the Windows XP NT boot loader.

*GRUB can actually be installed to the MBR.  This method takes slightly longer.  Instructions to follow.[/SIZE]
Now for my questions:
Point #1 - I don't have a floppy on my laptop, just a CD RW / DVD R, the installer must have discovered this because I never got a chance to reply where I wanted GRUB. It went straight to the MBR. Can I somehow transfer it to CD?

If I follow points #2-6 and I get that result I'd be happier than a pig in mud :) 
questions are, 
(a) step 4 talks about the floppy -- roadblock and academic at this stage, I have to take the MBR and somehow put it on CD or a USB memory stick to carry out that step
(b) how do I backup the working environment I currently have before going through those steps?

If I messed up this descriptions just yell at me and I'll try to clarify.

Thanks!

ETA: Although I originally was at Ubuntu 7.04 "Feisty Fawn: I did go to "Gutsy Gibbon", I'm now at a 6.04 and don't understand exactly how to get myself back to 7.10
       Still my main concern is how to get my WinXP safe -- as much as I hate it. How do I get my MBR to boot WinXP with Ubuntu as a secondary option. Not a primary as with GRUB.

Cheers!

---

