---
title: "ARG! Huge root user system malfunction"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by johntkucz on 2007-06-20
Okay, I'm running Fiesty Fawn 7.04, on a gateweay mx3701 . I had it intalled, but no sound, so I went to install alsa drivers.  whenver I got to ./configure command I got "permission denied" so I logged in with root, tried to change the permissions  (temporarily) of all directories to rwx (using the GUI permissions box), then I just tried to change the "usr" director to rwx for everyone (the one that contained the drivers), then a system crash, and the next thing I know I restart and only see this:

BusyBox v.1.1.3 (Debian 1:1.1.3 -3ubuntu3) Built-in sh (ash)
/bin/sh: can't access tty; job control turned off
(initramfs)

I cd to my home directory and all my files are still there so it doesn't look like things were erased ,but I'm writing this from the boot disk.  
HELP Please!!

---

### Post by wormser on 2007-06-20
First off, there is no reason to ever log in as root.  Use sudo and gksudo (for gui apps) for root privileges.  Try changing the permissions back to what they were then reboot.

---

### Post by johntkucz on 2007-06-20
thanks for the response.  I did try using sudo, and it still have the permissions denied error (before this problem).  

But the current problem..I'm still on the boot disk

What were the default permissions before?  How do I change all of them for the entire filesystem?

When I go to access the boot hardrive, all the folders show up as files with unknown size, date-modified, and type and all the permissions of these (previous folders) now files say "permissions for  'filename' could not be determined". It says there's 60gb out of 80 available, so I know my files are still there; just can't access them.

---

### Post by johntkucz on 2007-06-20
in terminal, all the commands refer to the "uneditable" boot disk. How do  I even begin to change directories to the actual hard drive? and then how do I change the permissions back?

---

### Post by johntkucz on 2007-06-20
all of these return permission denied!

cd /media/disk/ 
cd /media/disk
sudo cd /media/disk

/media/disk is my hard drive location.

---

### Post by johntkucz on 2007-06-20
actually, I don't know where my hard drive is.  /media/disk seems to be the boot cd, but under the GUI window it has the 60gb free, so it's definitely hard drive and "File System" is the boot cd, but that's in the gui.

---

### Post by johntkucz on 2007-06-20
Am I going to have to reinstall everything from scratch????? Please tell me I don't have to do that!

---

### Post by CrispyFried on 2007-06-20
permissions vary on a file by file basis. you would have to find out what each file/directory should be and change them all back one by one.

a reinstall is your only option at this point I think.

---

### Post by johntkucz on 2007-06-21
bloody hell.  how would I get the "defaults of permissions" for commonly used folders?  this is revoltingly unpleasant.  that's ridiculous -- you can't change permissions without snafuing the system?  if you change the /usr/src/ permissions to anythign but default,and I mean, adding more permissions, the system won't recognize the directory or somethign?  I can't even acess those folders to alter the permissions.  

Could I atleast learn what that BusyBoxy tty thing was?

---

### Post by johntkucz on 2007-06-21
how do you access the "computer" directory -- the highest directory, holding all drives, cd-drive and external hds?

---

### Post by DrPppr242 on 2007-06-21
the highest dir is / so cd / gets you there

---

### Post by juantao on 2007-06-21
Doing a global permissions change will certainly snafu a system. When you "tried to change the permissions (temporarily) of all directories" things probably became irretrievably messed up. You probably will reinstall, and don't be like me, and be so heavy handed next time. I've done a very similar thing and the trouble was too big to fix without starting over.

Can you mount another drive and backup some of your important stuff? Good luck - maybe some others will have a better suggestion for you.

---

### Post by DrPppr242 on 2007-06-21
not sure what to do if something can be done but the first thing I'd try would be to remove busybox
sudo apt-get remove busybox
just to see if it will at least boot properly.

---

### Post by HermanAB on 2007-06-21
Hmm, the only practical way to fix this kind of mess is to re-install.  I have also made a mistake like that about 10 years ago, so you are not alone and neither of uss will ever do that again :)

If your data is in a separate /home partition, then ensure that you don't format that one.  If not, then you have to backup your data first and then re-install.  

Anyhoo, now you know why you must always create a separate /home partition, since then you can re-install or upgrade in a jiffy without worrying about losing your data.

Cheers,

Herman

---

### Post by johntkucz on 2007-06-21
wow, drppr and juanto.  I'm still in the bind, but thanks a ton for the massive inputs. New plan of action: accept the reinstall, but salvage my home folder on the original harddrive.

I have an external hard drive, and if I can back up my main hd, then I'm in the clear and can reinstall worry free.  Any suggestiosn on how to do that?
 I think my hard drive (the internal 80 gb Fujitsu one that had ubuntu installed on it) is vmlinuz

But got this when I tried to open it:
ubuntu@ubuntu:/$ cd boot/vmlinuz-2.6.20-1
bash: cd: boot/vmlinuz-2.6.20-1: No such file or directory
ubuntu@ubuntu:/$ ls
bin   cdrom  etc   initrd      lib    mnt  proc  root  srv  tmp  var
boot  dev    home  initrd.img  media  opt  rofs  sbin  sys  usr  vmlinuz
ubuntu@ubuntu:/$ cd boot
ubuntu@ubuntu:/boot$ ls
abi-2.6.20-15-generic     initrd.img-2.6.20-15-generic.bak  System.map-2.6.20-15-generic
config-2.6.20-15-generic  memtest86+.bin                    vmlinuz-2.6.20-15-generic
ubuntu@ubuntu:/boot$ mount vmlinuz-2.6.20-1
mount: can't find vmlinuz-2.6.20-1 in /etc/fstab or /etc/mtab

In the GUI (This is where support would be seriously appreciated)
I've got a half-terabyte MyBook (sweet) that mounts and the target hard drive, the one I want to salvage the "home" from is called "71.8 GB Volume".  It's owner is "unkonwn" and permissions are "read-only" across the board.  When I double click on it, it turns into "disk", which has owner: "root" with permissions, list, create/delete, no access, and then for group and other access, it's "list files only". when I open it, it's all the folder "names' I'd normally see -- bin, boot, cdrom, etc.  but they're "ghosted out" as just files (when they are really folders) that have no size, no date-modified, and no known type.  WTF WTF!!!! is going on!!!!

Illd efinitely learn my lesson after this, and be sure to not login as root and to change permissions, at most, one at a time! Change ALL permissions of every file and folder of the computer, I realize who noobily idiotic that was!

THANKS!

---

### Post by johntkucz on 2007-06-21
One more thing.  When I check the permissions of those "files" (that are really folders) in the mounted volume "disk" (Which was "71.8 GB Volume" before), they all say "permissions of mnt [folder-file name] could not be determined."

---

### Post by arvevans on 2007-06-21
Have you considered looking at the RAM-based file and directory permissions while booted from the Live/Install CD?  That could give you some clues if you really would rather fix things manually.

I might suggest that you take the earlier tendered advice and re-install from scratch.  If you have stuff in /home that you don't want to lose, you could copy that to a USB pen-drive or to a CD and then restore it after re-installing the OS.

Part of the advantage of Ubuntu is it's not allowing uncontrolled use of the root ID and permissions.

If you do re-install everything, may I suggest that you set up partitions for "/", "/boot", "/home", and "swap".  Then the only thing you should ever have to touch in the /boot partition might be the grub list if you are doing dual-boot.  You should never have to manually change permissions on anything in "/", and of course you own your own" /home/user_ID" and can do anything you want in that area.

The root system didn't malfunction...it did exactly what you set it to do.  If it is any consolation, you are not the first to do this, and will probably not be the last (I've been there too).
_._

---

### Post by johntkucz on 2007-06-21
well, thanks a ton, this is somewhat of a consolation, but I have a new plan of action JUST save my home folder! I can't seem to do that though! When I try to copy just the home file or the entire "disk" hd volume, to my external HD, it transfer overs "ghost files" that are all 0bytes with the folders name so I get the home, boot, mnt, etc. folders but all are 0bytes.

I don't even know what grub is, I'm realizing how much more and more of a newbie I am, and the / /home /boot partitions sounds pretty complicated.  I've done multiple partitions on a mac before, but don't understand the ext2, ext3, swap terminology of linux.  So then all my home stuff would be "preserved" in it's own partition, which would be designated the most hd space?  Sounds good, but I need to SAVE MY HOME FOLDER, first.  How can I do that with all these 0bytes ghost folders?  how can I access my home folder to save?  I know i'll reinstall.

I still don't get that, thoug.  You change key system files around and put them in different folders, that could prevent them from being found, snaufing the the system, but adding permissions -- allowing more access to files?  That seems innocuous (obviously, I'm seeing that it's not).  Adding more permissions is just "opening more doors", not closing anything, it seems ridic. how adding permissiosn could mess up a system so severely.

I don't know what the ram-based file is and I just wrote three responses about the results of permissions.  this entire thread has been posted from the boot cd.

---

### Post by johntkucz on 2007-06-21
Noob realization, I jsut realized

lrwxrwxrwx   1 root root    30 2007-04-15 11:56 vmlinuz -> boot/vmlinuz-2.6.20-1

means that vmlinuz is an alias for the actual volume in the boot folder! Sweet, I'm getting some of the this.  But is vmlinuz my hard drive that holds the HOME folder?  How can I access that?  When I try to open it it says "no application suitable for automatic installation is available for handling this kind of file".

---

### Post by johntkucz on 2007-06-21
your thread seemed to have very similar problems as I was having, but I don't get the boot disk after blkid; here's the code:

Device Boot Start End Blocks Id System
/dev/hda1 * 1 9376 75312688+ 83 Linux
/dev/hda2 9377 9729 2835472+ 5 Extended
/dev/hda5 9377 9729 2835441 82 Linux swap / Solaris

Disk /dev/sda: 1021 MB, 1021312512 bytes
129 heads, 16 sectors/track, 966 cylinders
Units = cylinders of 2064 * 512 = 1056768 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 967 997367+ e W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
phys=(972, 128, 16) logical=(966, 57, 15)

Disk /dev/sdc: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 7872 2015216 e W95 FAT16 (LBA)

Disk /dev/sdd: 517 MB, 517341184 bytes
218 heads, 45 sectors/track, 103 cylinders
Units = cylinders of 9810 * 512 = 5022720 bytes

Device Boot Start End Blocks Id System
/dev/sdd1 * 1 103 505192+ b W95 FAT32

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdf1 1 60801 488384001 c W95 FAT32 (LBA)

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
ubuntu@ubuntu:/boot$ blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="TravelDrive" UUID="392C-62FA" TYPE="vfat"
/dev/sdc1: SEC_TYPE="msdos" LABEL="TRAVEL2GB" UUID="D4BB-92EF" TYPE="vfat"
/dev/sdd1: LABEL="JTK_IPOD" UUID="0000-0000" TYPE="vfat"
/dev/sdf1: LABEL="My Book" UUID="92A8-ABE1" TYPE="vfat"
ubuntu@ubuntu:/boot$


Please help! I need to get files off of dev/hda1
from
/dev/hda1 * 1 9376 75312688+ 83 Linux
/dev/hda2 9377 9729 2835472+ 5 Extended
/dev/hda5

How can I do that?

---

