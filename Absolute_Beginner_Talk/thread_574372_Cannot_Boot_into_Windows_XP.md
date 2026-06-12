---
title: "Cannot Boot into Windows XP"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by KingdomKid on 2007-10-12
I just cloned my hard drive with Acronis true image...

All seemed to be a success. Linux is working fine, boots up as it should. 
When I select to boot into Windows XP, in Grub....the screen goes black with the message "Starting Up..." in the top left corner. Nothing happens.

Ctrl+Alt+Del takes me back to grub

Any suggestions???
Thanks

---

### Post by Sef on 2007-10-12
Applications > Accessories > Terminal

then type in this command:

```
sudo fdisk -l
```

copy and paste the results here.

---

### Post by KingdomKid on 2007-10-12
SEF...


```
???@#$%$#? :~$ sudo fdisk -l
Password:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
16 heads, 63 sectors/track, 77520 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       46681    23527192+   7  HPFS/NTFS
/dev/sda2           46682       76134    14844312   83  Linux
/dev/sda3           76135       77520      698544    5  Extended
/dev/sda5           76135       77520      698512+  82  Linux swap / Solaris
```

---

### Post by Tyke91 on 2007-10-12
i had this problem before, instert your windows install disk and run the command

CHKDSK from their terminal

---

### Post by KingdomKid on 2007-10-12
> **Tyke91 said:**
> i had this problem before, instert your windows install disk and run the command

CHKDSK from their terminal

Tyke91...
I bought this computer used and do not have the cd for the current copy of "XP Pro" I have installed on this computer.
I do have an older version of XP Home....I assume that would not work, right?

Thanks for any Help.

---

### Post by Imsati on 2007-10-12
It might, give it a shot!

---

### Post by KingdomKid on 2007-10-13
Sef...

I posted above...any ideas.
I am kinda new at this and could really use some input.

I tried the other xp cd (see above), just to see what would happen...I got to the admin password part in the repair mode...it kept kicking me out saying my password was incorrect. AHHHHH, I know my password. Go figure....

Any direction guys...Thanks

---

### Post by KingdomKid on 2008-04-10
DK...Thanks for taking the time. Here are the results when you get a chance.

```
mav@MavsEvo:~$ sudo fdisk -l
Password:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
16 heads, 63 sectors/track, 77520 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       46695    23534248+   7  HPFS/NTFS
/dev/sda2           46696       76140    14840280   83  Linux
/dev/sda3           76141       77520      695520    5  Extended
/dev/sda5           76141       77520      695488+  82  Linux swap / Solaris
mav@MavsEvo:~$
```

And...

```
sudo nano /boot/grub/menu.lst

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic 
root=UUID=aa42ec45-c75e-4dcc-891d-b79c63961af7 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic 
root=UUID=aa42ec45-c75e-4dcc-891d-b79c63961af7 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic 
root=UUID=aa42ec45-c75e-4dcc-891d-b79c63961af7 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic 
root=UUID=aa42ec45-c75e-4dcc-891d-b79c63961af7 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

---

### Post by Zralou on 2008-04-10
> **KingdomKid said:**
> Sef...


I tried the other xp cd (see above), just to see what would happen...I got to the admin password part in the repair mode...it kept kicking me out saying my password was incorrect. AHHHHH, I know my password. Go figure....

Any direction guys...Thanks

As long as you haven't changed the original administrator account in any way, the password in recovery mode should be blank.

Sara Lou

---

### Post by david_kt on 2008-04-10
Hi Mav,

The menu.lst looks ok for me, then you should try windows xp installation CD. I saw that you got into trouble of password. What you could do is to reset the windows xp password, see below for example:

[http://revver.com/video/319006/easily-reset-any-lost-windows-password-with-free-software/](http://revver.com/video/319006/easily-reset-any-lost-windows-password-with-free-software/)

You should make the password to blank to make it easier. After that, try again your windows xp installation cd. But please be carefull so as not to wipe out your harddisk.

DK

---

### Post by KingdomKid on 2008-04-10
> **david_kt said:**
> Hi Mav,

The menu.lst looks ok for me, then you should try windows xp installation CD. I saw that you got into trouble of password. What you could do is to reset the windows xp password, see below for example:

[http://revver.com/video/319006/easily-reset-any-lost-windows-password-with-free-software/](http://revver.com/video/319006/easily-reset-any-lost-windows-password-with-free-software/)

You should make the password to blank to make it easier. After that, try again your windows xp installation cd. But please be carefull so as not to wipe out your harddisk.

DK

DK...I did the above and got the password taken care of.
I ran the following:

```
C:\WINDOWS>chkdsk
Volume created 09/27/06  02:37p
The volume Serial Number is 3468-32c6

The volume appears to be in good condition and was not checked.
Use /p if you want to check the volume anyway.

  23534248 kilobytes total disk space.
    9944444 kilobytes are available.

         4096 bytes in each allocation unit.
    5883562 total allocation units on disk.
    2486111 allocation units available on disk.

C:\WINDOWS>
```

I am not sure what to do at this point???
Hey..we got in, thats a start...

---

### Post by david_kt on 2008-04-10
May be you should try below:

[http://www.webtree.ca/windowsxp/repair_xp.htm#How%20to%20Repair%20the%20Boot%20Sector:](http://www.webtree.ca/windowsxp/repair_xp.htm#How%20to%20Repair%20the%20Boot%20Sector:)

If still could not solve your problem, try below:

[http://www.webtree.ca/windowsxp/repair_xp.htm#How%20to%20Repair%20Windows%20XP%20by%20Installing%20Over%20top%20of%20Existing%20Setup:](http://www.webtree.ca/windowsxp/repair_xp.htm#How%20to%20Repair%20Windows%20XP%20by%20Installing%20Over%20top%20of%20Existing%20Setup:)

But the later step might require you to repair the MBR again in order to boot to linux. Anyway, let's do it one at a time as I am not an expert in this area as well.

DK

---

### Post by KingdomKid on 2008-04-11
Hey guys...going to attempt the suggestions above tonite..

I noticed tonite as I was boot into the computer...my 30'th reboot when it was checking the disk Isaw that mounting swap failed.

Would that have anything to do with this issue of not being able to boot into Windows side?

Thanks Again.

---

