---
title: "MBP &amp; Gutsy: Couple of problems"
date: 2007-10-20
forum: Apple Intel Users
---

### Post by chipt4 on 2007-10-20
Ok, finally got around to installing Gutsy on my 1st gen macbook pro (1.83 core duo, 1.5gb ram, 80gb hd).  Installation went completely smooth and it booted up just fine.  I am triple booting, using rEFIt, and my partitions look like so:

1 ->  EFI
2 ->  OSX
3 ->  Gutsy
4 ->  Win XP

Problem #1:  GRUB still fails to load for me.  If, after selecting Linux from the rEFIt menu, I don't press anything, the tux icon comes up, then the screen goes black and the computer hangs.  If I press ESC while the tux icon is up, it says something like 'GRUB Loading Stage 2', then comes up to GRUB's menu where I can select what kernel to load, select the top most one (Ubuntu 7.10)  and Ubuntu boots just fine.  I had this problem before, with Feisty, and the solution was to run LILO instead of GRUB.

Sooo, I install LILO (apt-get install lilo lilo-doc) and create /etc/lilo.conf with the following:

```

boot=/dev/sda3
default=Ubuntu
map=/boot/map
delay=20
image=/vmlinuz initrd=/initrd.img
root=/dev/sda3
label=Ubuntu
read-only

```
and then try to run lilo -P ignore -b /dev/sda3  (after doing a 'sudo sh') but it gives 3 warnings:

```

Warning: Ignoring entry 'boot'
Warning: LBA32 addressing assumed
Warning: Partition 3 on /dev/sda is not marked Active

```
and when I try syncing the MBR in rEFIt & booting, it still uses GRUB.  Any clue as to what I'm doing wrong?

Oh, and I also did:  "parted ->  set 3 boot on -> quit" if that makes a difference.

Problem #2:   I didn't create a swap file.  In the tutorials I read, it said to create the swap file before installing (I installed from the LiveCD) but the commands that were given in the tutorial produced an error for me.  So I installed without one and everything seems to be going fine.  Will I run into problems without one?  Less performance?  I'm guessing suspend won't work correctly, since, IIRC, it writes the contents of your RAM to the swap file before turning off the computer.  Any thoughts?

Problem #3:  rEFIt shows 4 choices of OSes:  Boot Mac OS X from OSX, Boot Linux from HD, Boot Linux from <blank> and Boot Windows from <blank>.  It doesn't matter which Linux I pick, it still boots into GRUB (I was hoping maybe one was for lilo & the other grub, but no luck) and Ubuntu boots fine.  But it's just a bit aesthetically unpleasing to have two Linux icons, when I only have one distro installed.  Not sure why Windows' HD name is blank.  I don't believe it was like that before I installed Ubuntu.  Also, now if I select Windows from rEFIt, it just loads GRUB (albeit without me having to press ESC to get to GRUB's menu) where Windows is an option.  This works fine, but I'd like to skip the GRUB menu and just have rEFIt boot directly to Linux if I select it & directly to Windows if I select it (from within rEFIt).

Problem #4: Having issues getting Compiz Fusion working.  I installed the ATI Restricted drivers, XGL, dbus-x11, etc but still nothing.  However I've found a thread or two talking about these issues, so I'm going to try them.  EDIT:  Followed the instructions at [http://ubuntuforums.org/showthread.php?t=579892]("http://ubuntuforums.org/showthread.php?t=579892") and got it working. 1 down, 3 to go!

Sorry for the confusing explanations, I'm getting tired and a bit frustrated.  I managed to get LILO working fine with Feisty, however it was just a dual boot.

Thanks in advance :D

---

### Post by cyberdork33 on 2007-10-20
> **chipt4 said:**
>  Problem #1:  GRUB still fails to load for me.  If, after selecting Linux from the rEFIt menu, I don't press anything, the tux icon comes up, then the screen goes black and the computer hangs.  If I press ESC while the tux icon is up, it says something like 'GRUB Loading Stage 2', then comes up to GRUB's menu where I can select what kernel to load, select the top most one (Ubuntu 7.10)  and Ubuntu boots just fine.  I had this problem before, with Feisty, and the solution was to run LILO instead of GRUB.

Sooo, I install LILO (apt-get install lilo lilo-doc) and create /etc/lilo.conf with the following:

```

boot=/dev/sda3
default=Ubuntu
map=/boot/map
delay=20
image=/vmlinuz initrd=/initrd.img
root=/dev/sda3
label=Ubuntu
read-only

```and then try to run lilo -P ignore -b /dev/sda3  (after doing a 'sudo sh') but it gives 3 warnings:

```

Warning: Ignoring entry 'boot'
Warning: LBA32 addressing assumed
Warning: Partition 3 on /dev/sda is not marked Active

```and when I try syncing the MBR in rEFIt & booting, it still uses GRUB.  Any clue as to what I'm doing wrong?

Oh, and I also did:  "parted ->  set 3 boot on -> quit" if that makes a difference.

can't help you there. Grub works just fine for most.

> Problem #2:   I didn't create a swap file.  In the tutorials I read, it said to create the swap file before installing (I installed from the LiveCD) but the commands that were given in the tutorial produced an error for me.  So I installed without one and everything seems to be going fine.  Will I run into problems without one?  Less performance?  I'm guessing suspend won't work correctly, since, IIRC, it writes the contents of your RAM to the swap file before turning off the computer.  Any thoughts?You can run without, but it better to have one for disk caching. suspend should not be limited by swap (as suspend just keeps everything in powered RAM). Hibernate, however, operates as you described and will not work without swap. If you really want it, you can resize one of your partitions (with gparted perhaps) and add swap. You will then have to add the correct lines to your fstab to use it.

> Problem #3:  rEFIt shows 4 choices of OSes:  Boot Mac OS X from OSX, Boot Linux from HD, Boot Linux from <blank> and Boot Windows from <blank>.  It doesn't matter which Linux I pick, it still boots into GRUB (I was hoping maybe one was for lilo & the other grub, but no luck) and Ubuntu boots fine.  But it's just a bit aesthetically unpleasing to have two Linux icons, when I only have one distro installed.  Not sure why Windows' HD name is blank.  I don't believe it was like that before I installed Ubuntu.  Also, now if I select Windows from rEFIt, it just loads GRUB (albeit without me having to press ESC to get to GRUB's menu) where Windows is an option.  This works fine, but I'd like to skip the GRUB menu and just have rEFIt boot directly to Linux if I select it & directly to Windows if I select it (from within rEFIt).
You have installed Grub to the MBR (the normal location), thus it is the default legacy bootloader (and has replaced the windows bootloader). You can use the windows recovery cd and the fixmbr command to replace grub with the windows bootloader again, then install your bootloader to the Ubuntu partition instead of the MBR. See this thread for instructions on doing that from inside your booted system.
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively)
This may have something to do with your multiple icons in rEFIt too.

---

### Post by chipt4 on 2007-10-20
> If you really want it, you can resize one of your partitions (with gparted perhaps) and add swap. You will then have to add the correct lines to your fstab to use it.


There's an issue on intel macs that keeps them from using more than 4 partitions (something about hybrid MBRs?) so I'm stuck using a swapfile.  I want to use a 2gb swapfile, on /dev/sda3.. Could you walk me through setting it up?

You mentioned that hibernate will require it.  It seems that suspend still isn't working correctly in Gutsy.  If hibernate works, is there a way to have it hibernate when I close the laptop, instead of suspend?

I also have another question:  I've tried mounting my OSX partition using mount -t hfsplus /dev/sda2 /mnt/osx and it lets me browse my OSX partition up to a certain point, but if I try to access my user files it says I don't have permission.  Any ideas?  I have all my music, video and images on my OSX partition and would like to access them from ubuntu.

EDIT:  Ok, after poking around I've found out that my OSX & linux UIDs need to be the same for me to be able to access my OSX's user directories.  My OSX UID is 501, should I try to change it to match my linux UID (haven't looked it up yet) or vice versa (change my linux UID to match my OSX)?  I'd much rather hose my linux install than my osx, if this is dangerous.

---

### Post by cyberdork33 on 2007-10-20
> **chipt4 said:**
> There's an issue on intel macs that keeps them from using more than 4 partitions (something about hybrid MBRs?) so I'm stuck using a swapfile.  I want to use a 2gb swapfile, on /dev/sda3.. Could you walk me through setting it up?you are misinformed... You can only have 4 bootable primary partitions available in your legacy BIOS emulation... Ubuntu does not require the hybrid stuff it can read GPT disks just fine.

> You mentioned that hibernate will require it.  It seems that suspend still isn't working correctly in Gutsy.  If hibernate works, is there a way to have it hibernate when I close the laptop, instead of suspend? I don't know that either work at the moment.

> I also have another question:  I've tried mounting my OSX partition using mount -t hfsplus /dev/sda2 /mnt/osx and it lets me browse my OSX partition up to a certain point, but if I try to access my user files it says I don't have permission.  Any ideas?  I have all my music, video and images on my OSX partition and would like to access them from ubuntu.
linux can read the permissions on files in your OSX partition. Those files are "owned" by another user (from another system) and therefore you cannot access them. If you boot OSX and alter the permissions for the items you want, you can access them in linux.

---

### Post by rickwood on 2007-10-20
> **chipt4 said:**
> Ok, finally got around to installing Gutsy on my 1st gen macbook pro (1.83 core duo, 1.5gb ram, 80gb hd).  Installation went completely smooth and it booted up just fine.  I am triple booting, using rEFIt, and my partitions look like so:

1 ->  EFI
2 ->  OSX
3 ->  Gutsy
4 ->  Win XP

Problem #1:  GRUB still fails to load for me.  If, after selecting Linux from the rEFIt menu, I don't press anything, the tux icon comes up, then the screen goes black and the computer hangs.  If I press ESC while the tux icon is up, it says something like 'GRUB Loading Stage 2', then comes up to GRUB's menu where I can select what kernel to load, select the top most one (Ubuntu 7.10)  and Ubuntu boots just fine.  I had this problem before, with Feisty, and the solution was to run LILO instead of GRUB.

:D

I've got the 2nd gen macbook, so maybe things are a little different.  But with previous versions of Ubuntu I've also had to use lilo.  Not so with Gutsy.  It works just fine with Grub.  But I used the alternate install disk so I would have the option of where to install Grub.  My partitions are identical to yours, I also use rEFIt, and I wanted to make sure Grub was installed to partition 3 (Gutsy) rather than the master boot record.  In previous versions of Ubuntu I haven't been able to find an option with the normal install disk to put Grub anywhere other than on the MBR.  Maybe this is different now, but I didn't take the chance and used the alternate install disk.  I believe the master boot record is how WinXP is booting, and I didn't want to mess with that.  With Grub installed to partition 3 only, rEFIt has no problems booting all three OS's, and I don't have to rely on Grub to boot WinXP.

---

### Post by cyberdork33 on 2007-10-20
> **rickwood said:**
> I wanted to make sure Grub was installed to partition 3 (Gutsy) rather than the master boot record.  In previous versions of Ubuntu I haven't been able to find an option with the normal install disk to put Grub anywhere other than on the MBR.
After the installer asks all the 'questions' it will give a summary of what you are about to do and there is an advanced button where you can change the location that grub is installed to.

---

### Post by rickwood on 2007-10-20
> **cyberdork33 said:**
> After the installer asks all the 'questions' it will give a summary of what you are about to do and there is an advanced button where you can change the location that grub is installed to.

Thanks!  Next time I'll go back to trying the normal install disc.

---

