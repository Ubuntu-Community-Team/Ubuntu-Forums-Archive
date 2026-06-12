---
title: "Dual Booting"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by xamfer on 2006-08-08
Hi everyone!

Ok, this is me:

80GB (approx.)
- partition 1 = 16GB Winxp
- partition 2 = 43GB NTFS (data)
- partiton 3 = 20GB Ubuntu 6.06
- partition 4 = 1GB swap

Installed winxp first, then installed Ubuntu 6.06.
Thing is it appears my PC is running like "first-option" Ubuntu when booting. Ok, I get to press ESC and I get a list of all the OS availabe, but my winxp is not there in the list. So, as for now, I just don't know hot to get the option or access to boot using winxp (I know by experience that if I now install winxp, then I won't be able to boot using Ubuntu)

By the way, yeah, I'm a neewbe! But I'm making my way into Linunx through Ubunut little by little (if it wasn't for printing set ups, winxp could kiss my ...)

Please help!!
Thanks.

---

### Post by orb9220 on 2006-08-08
esc is for the linux options. you need to boot and when you get to grub menu you use the down arrow key until you reach the other operating system where xp should be listed.

Don't hit esc hit the down arrow key

---

### Post by Mtnear on 2006-08-08
If you got through the install correctly you shouldn't have to hit ESC.  Like orb said, you should see the grub menu boot up and Windows XP should be the last thing listed to choose.

---

### Post by xamfer on 2006-08-08
Well, that menu option appeard when I installed the previous version of Ubuntu (before 6.06). My Pc would boot, the menu appeard like for 10 seconds or something, and the winxp was in the last place. No problem there.

But now that I installed Ubuntu 6.06, if I let my Pc boot normally, the menu never appears. I press ESC and a list appears but is verything about ubuntu kernel or boot in safe mode or whatever.

It there some way around to configure the booting???? So the winxp option appears?

Thanks a lot.

---

### Post by Tomosaur on 2006-08-08
Does Windows appear in the menu.lst file? You can find it in /boot/grub

If not, try running 'sudo update-grub' from the terminal. It should rescan your hard disks for installed operating systems and fix the menu accordingly.

---

### Post by confused57 on 2006-08-08
Boot into Ubuntu, then open a terminal(Applications---Accessories---Terminal):
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

The first command changes directory, the 2nd command creates a backup of your menu.lst, then the 3rd command opens your menu.lst in the text editor "gedit".
Put a # in front of the line **Hiddenmenu**, this will display your grub menu at startup.  You might want to make the timeout something like 10(seconds).
Add your windows entry to the end of the menu.lst file, something like this(also see the example in your menu.lst):
```
 title         Windows XP
 root          (hd0,0)
 makeactive
 chainloader   +1
```

Then when you bootup the grub should display and have the option to boot Windows.
You probably should try the suggestion by Tomosaur first & if it doesn't work, you can try the above.

---

### Post by Tomosaur on 2006-08-08
You could also try my sexy script.

</hijack> :P

---

### Post by xamfer on 2006-08-08
Ok, thanks a lot everyone.

Confused57, very well explained. I did like you told me, but I'm missing something. When I press ESC then the hidden menu shows up. The Windows XP option appears, but I must'd write something wrong.
This is the error message I got:

Booting ' Windows XP 2 '
Root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
make active
chainloader +1

Error 13: invalid or unsupported excecutable format.

---

### Post by Tomosaur on 2006-08-08
Erm. That's somewhat odd. Try setting it to (hd0,1) and see if that works, but judging from your first post this partition is just data.

---

### Post by xamfer on 2006-08-08
Ok. This is what it is on my PC. I think the Windows XP is not detected or something. This what I got from the Terminal after scaning & updating the list:

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.15-26-386
Found kernel: /boot/vmlinuz-2.6.15-23-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

So, I think I'm pretty f...d up?

Questions:

1. Any way to solve thi and make my system detect my windows xp? 

2. If "I'm f....d up" situtation, then how can i install windows xp again, and keep the GRUB list to appear. I know - because I've done it - that if I re-install winxp having already a version of Ubuntu installed, then when I boot, I got now GRUB listing of the Os installed in my PC.

---

### Post by confused57 on 2006-08-08
In Ubuntu, see what the output of this command is:
```
sudo fdisk -l
```
The -l is a small "L"

This will show your partition table.

Make sure you enter the Windows entry exactly the way I showed it, Linux is case-sensitive and I noticed you had Root instead of root...may make a difference.  

May want to add the line savedefault:
```
 title         Windows XP
 root          (hd0,0)
 savedefault
 makeactive
 chainloader   +1
```

You don't need to reinstall Windows, you can repair the Windows mbr using the Windows install CD(not the recovery CD), boot up with the CD, press "r" for recovery, then enter **fixmbr**.  This will restore the Windows mbr to make Windows bootable again, but you wouldn't be able to boot Ubuntu. Here's a tutorial:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm) 
You might be able to reinstall grub using the Live CD:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Hopefully, the earlier suggestion will work(case-sensitivity).

---

