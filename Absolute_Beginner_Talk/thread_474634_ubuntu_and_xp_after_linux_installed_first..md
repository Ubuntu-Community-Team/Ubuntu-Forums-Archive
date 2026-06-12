---
title: "ubuntu and xp after linux installed first."
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-06-15
ok i know i should have setup xp first but i didn't ok!
so how do i now install xp and dual boot it?
i can make a partition for it yeah and install it then what.
i need to reinstall grub through a live cd like ubuntu?
clear instructions please!
cheers i know this is asked alot but its hard to find with keywords.

---

### Post by elvinatom on 2007-06-15
Boot up DOS (from 98-CD or whatever other media you got) then type 'fdisk /mbr' to rewrite the master boot record.  Then do you XP install.
Once its up and running boot the live cd of ubuntu and reinstall grub.  (you might have to set igrub up manually if xp is not in the list)

---

### Post by ZennouRyuu on 2007-06-15
It sounds like you have the general idea, once you have created your additional partiton and installed windows XP there, the windows installer will kindly replace your MBR without asking you. So you will need to boot with some linux live CD, just about any recent distros live CD will work as long as it has the hardware drivers for your system and grub.

Once you have booted into the live CD, go to a terminal as root and run grub

```
# grub
```


You will see something like this:

```
 
    GNU GRUB  version 0.95  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename.]

grub>
 
```

at the grub prompt type the following where (hd0,0) is your boot partition 

```
grub> root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83

```

then type the following

```
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/grub/stage2 /grub/grub.conf"... succeeded
Done.

```


Reboot, remove the live CD and that should be that, good luck

---

### Post by ikonia on 2007-06-15
as  I've told you about 30 times - search the wiki

First result for search "grub" on the ubuntu community help wiki

[https://help.ubuntu.com/community/GrubHowto?highlight=%28grub%29](https://help.ubuntu.com/community/GrubHowto?highlight=%28grub%29)

---

### Post by zeeR on 2007-06-16
> **ikonia said:**
> as  I've told you about 30 times - search the wiki

First result for search "grub" on the ubuntu community help wiki

[https://help.ubuntu.com/community/GrubHowto?highlight=%28grub%29](https://help.ubuntu.com/community/GrubHowto?highlight=%28grub%29)

On that article, there is no topic explaining how to reinstall Grub AFTER installing Windows...

---

### Post by meborc on 2007-06-16
maybe try article titled - [RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

