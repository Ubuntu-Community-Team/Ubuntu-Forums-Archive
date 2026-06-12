---
title: "NTLDR MIssing, CTRL ALT DEL to Restart"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by laxatives on 2007-08-28
So I thought I could try and install XP on a separate partition, but it turned out my disc was a little faulty.  I figured I could just restart and go back to Feisty Fawn, but NTLDR missing came up after the bios.  Some research showed me that NTLDR was from the XP installation, so I completely erased that partition that had the failed installation, but the error still comes up.  Right now I'm booting from my ubuntu cd to write this.  Any ideas on what I can do to fix this problem without starting from scratch?

Also, I noticed that I could create a new partitio nusing the freespace in an existing partition when I install ubuntu.  Is it possible to do the same to create an XP partition?  All the guides I've read so far on dual booting require XP to be installed first, but I really don't want to wipe the drive

Thanks in advance

---

### Post by undertherift on 2007-08-28
If you get even a little through the XP installation, windows goes ahead and wipes over your MBR.

This essentially means that GRUB (your boot loader, the thing that let you select Ubuntu before boot), is gone.  You don't have to wipe the disk, no.  I googled "Howto Reinstall grub ubuntu"  and this is what came up.

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

See if/how that works. That'll get you back into ubuntu. If the first method doesn't work, keep looking.  Almost everyone who has ever tried to dual-boot has run into this problem, so there's alot of info out there on it.

---

### Post by Marat Galiev on 2007-08-28
Use the fixboot command from the Windows CD,to rewrite the Windows XP boot code.
press R then you boot from you win cd.
and enter fixboot or fixmbr commands.
or copy NTLDR.exe from this CD to you system drive.

---

### Post by laxatives on 2007-08-28
Sorry, I'm quite new to linux and stil lhave alot of reading ahead. I'm a little lost in some of the instructions and need some further explanation

I tried a few of the possible fixes on the link, as wel as fixboot/fixmbr commands.  Fixboot didnt resolve the problem and fixmbr commands didnt seem to do anything.

The first solution on the site:
1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
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

I get lost at step 4.  Just to be sure, I've been loading from the Ubuntu 7.04 for a 64-bit CD (the same cd I originally installed from), and then hitting install.  I've been going through all the pages until the page that deals with partitioning(titled "Prepare Disk Space).  I go to manual section and find /dev/sda1 which is where ubuntu is installed.  From there, I'm lost.  Mount the partition?  I'm not sure what to do with the following commands (/boot, swap, .....) or how to run them in terminal if thats required.

The next possible solution: 
1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

I open terminal type "sudo grub"(just grub leads to the computer not finding root hd(0,0), type root hd(0,0) [I found this through "sudo grub" followed by "find /boot/grub/stage1"] Typing "root (hd0)", terminal responds with "root (hd0)", then setup (hd0)  results in 
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

I also ran "setup hd(0,0)" and got this back:
setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu.lst "... succeeded
Done.


But after a reboot, this doesn't solve the ntldr missing, ctrl alt del to restart problem.  Any ideas?

---

### Post by splintercellguy on 2007-08-28
Try Super GRUB CD? Seems to save the cmd-line trouble for me.

---

### Post by laxatives on 2007-08-29
Ah I lied.  It seems somewhere between my previous failures and my last post, the problem was fixed.  I redid all my previous moves as I was typing so I woud have something to copy and paste, and after rebooting, everything wsa in working order.  Thanks a lot to the previous posters for helping me through my troubles

---

