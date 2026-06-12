---
title: "drives unreachable"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by poisonfro66 on 2008-03-25
Hello

Well, I have two problems, one of which must be solved (otherwise i think i'll just re-install everything from scratch).

Biggest one: I have made three partitions in my Int HDD. I have installed XP professional on one of them. No worries there. I then installed Ubuntu (v 7.10, 32-bit) on another partition. Ubuntu worked fine. however, when i tried to go back under XP, the whole boot sequence stopped (literally stopped, liked hitting "Pause" in a movie player) after the loading screen (the one which says "Windows XP Professional" with a loading bar, the windows logo, and the background=black). The screen just stays black (like the very short part where the screen restart, between the black loading screen and the blue screen saying "Windows is loading", before the "choose-your-session" screen, with the same blue background). Last time time i tried, the mouse pointer came back, the size it would be in safe mode, but the screen stayed black, and when i clicked, the computer went "Beep" each time i clicked.

I would like to try to start in safe mode but don't know how (If you know how...). I know, im a total n00b.

The second one: Ubuntu works fined when chosen in the "Choose-your-OS" screen after installation.The whole thing boots up perfectly, all my drives show and work, fine. Logout. And try to make XP work. However, after a few times restarting the computer to see if XP was going to boot or not, I loaded Ubuntu again, and my drives (partitions of the int HDD, and worse, the Ex HDD) icons can't be seen, and worst of all , can't be accessed (I know it because i chose a picture that was on my Ex HDD to be my background, and it doesn't appear when Ubuntu is booted. un-plugging, re-plugging the EX HDD, restarting the OS, nothing works.

I can do without Windows for a bit, but I need my Ex HDD (In Ubuntu)!

Please, Help!

---

### Post by Squish on 2008-03-25
I think I might have a solution to your ubuntu problem.

As to your windows, I am not quite sure I understand:
When you choose to boot up xp, does it have simply a black inactive screen, where you cannot see anything? Does it stay like that forever?
One thing that it might be is that if you have dual video cards, or more than one vga port, you might want to try switching screen ports for your monitor. Often I have booted up xp, and the os is actually sending the image through another vga port. 
Essentially try and see if you can plug your monitor's cable into any other ports behind your computer. 

As to your ubuntu, if you have these things on your external, you simply need to mount it first before you can access it.
This is an incredibly simple process
1> make sure the EXT HDD is on, and connected to your computer
2> goto places, and open up any folder (so that you open up nautaulius)
3> look on the left panel, where it lists shortcuts to the trash, pictures, videos, music, etc... you should see your external harddrive there. Mine is labled "Disk" or somethhing like that. 
4> Click on the icon pretaining to your external. the first time you click on it, it will cause it to mount. the second time you click on it, you will be able to access your files. Make sure you unmount it before unplugging it though, as that could cause some serious issues. If you shuttdown your computer with it, that is fine, ubuntu will unmount it for you

did that work?

---

### Post by poisonfro66 on 2008-03-25
Hello Squish

Well, no, my HDD doesn't show at all. I think it might be a hardware problem because i just plugged it into another computer with plug n' play and nothing happened. Something may have happened to it when it repeatedly re-booted the computer in frustration at XP not working? The HDD works, the lights are on, but it simply doesn't show. It's like less than a month old...

As for XP, when chosen as OS, the Loading Bar shows up (the screen with a black background, the windows logo, "Microsoft Windows XP", microsoft corporation copyright down in the corner). after it finishes loading...
Nothing. The screen is still on, but nothing at all shows up. it stays all black.

---

### Post by jan quark on 2008-03-25
do you have another machine with windows running? perhaps you must boot into windows and safely remove the external drive...

in linux can you please plug in the ext HDD and run these commands and post the output

```
sudo fdisk -l 
cat /etc/fstab
```

---

### Post by poisonfro66 on 2008-03-25
master@Cortana69:~$ sudo fdisk -l
[sudo] password for master:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd374d374

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6375    51207156    7  HPFS/NTFS
/dev/sda2            6376       30156   191020882+   f  W95 Ext'd (LBA)
/dev/sda3           30157       30401     1967962+  82  Linux swap / Solaris
/dev/sda5            6376       11474    40957686   83  Linux
/dev/sda6           11475       30156   150063133+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69e49990

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       58855   472752756    7  HPFS/NTFS
master@Cortana69:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=11396c24-0632-4547-8285-8a3abf97da40 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=1ADCEA3CDCEA11B5 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=FE300362300320EF /media/sda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=DE98AA5D98AA3445 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=a003511a-e4bb-4e3c-bf52-cbe50b67fc17 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by jan quark on 2008-03-25
I suppose this is your external hard drive
> 
Disk /dev/sdb: 500.1 GB, 500107862016 bytes

and when you go to 
```

/media/sdb1
```

it is not mounted there?

---

### Post by poisonfro66 on 2008-03-25
No, there is nothing there.
/media/sdb1

---

### Post by jan quark on 2008-03-25
try to mount all drives mentioned in fstab once again with

```
sudo mount -a
```

---

### Post by poisonfro66 on 2008-03-25
master@Cortana69:~$ sudo mount -a
[sudo] password for master:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda6': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda6 /media/sda6 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda6 /media/sda6 ntfs-3g defaults,force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/sdb1 ntfs-3g defaults,force 0 0

---

### Post by Squish on 2008-03-25
> Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
clicking on the 'Safely Remove Hardware' icon in the Windows
taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
your own responsibility. For example type on the command line:

mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

Or add the option to the relevant row in the /etc/fstab file:

/dev/sdb1 /media/sdb1 ntfs-3g defaults,force 0 0
It looks like this is what we want.

"Mount is denied because NTFS is marked to be in use" is the diagnosis. NTFS is the filesystem used to partition this drive, and it is stated to be in use by another process. Thus is it attached or being used by another operating system at the moment? Do you have any inclination to what might be keeping it busy?

---

### Post by jan quark on 2008-03-25
this issue I have seen quite often here in the forums

usually it helped to boot into windows again 
and safely remove the device

but I do not know if this is applicable to our situation because poisonfro66 told us that nothing happens in windows when the external drive is plugged in...

or?

---

### Post by poisonfro66 on 2008-03-25
I have restarted the computer a few times after each windows boot failed and the HDD was connected all the time. However that was yesterday and the whole thing's been shut down until i restarted it. Is it possible that the drive is still in use by windows?

---

### Post by jan quark on 2008-03-25
if you boot into windows 

do you have the possibility to remove the external drive safely?
does it show up somewhere ? ( not very specific, but I have forgotten how windows gui looks like :) )

if yes remove it safely and boot into linux again
sometimes the drive "thinks" it is in use when not removed safely

---

### Post by Squish on 2008-03-25
oh that actually makes allot of sense ~ brilliant
I learned something new:lolflag:

---

### Post by poisonfro66 on 2008-03-25
Yep, i' ve got it.

You were right all along; Windows needed to be booted up properly and shut down properly. Now all my drives are back online. I don't know how you made me make windows work, but I think you're really really good.

Ok, that could part of the explanation (because that's the only thing I've done in the meantime);

I've involuntarily made linux go into safe mode, while trying to configure my graphics card. Maybe that could be it, even though i don't see any freakin' connection between the two?!  :)

Anyway, thanks to everyone who helped me make my day (and my computer's).

You guys are great!

P.S. I'll probably be back soon, about that graphics card, and my efforts to enable the effects...

---

### Post by Squish on 2008-03-25
We appreciate your grattitude ^^ good luck!

---

