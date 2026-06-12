---
title: "Ubuntu triple-boot no longer booting :("
date: 2008-07-18
forum: Apple Hardware Users
---

### Post by randysparks on 2008-07-18
Yesterday I made my Intel MacBook (CD 1.83GHz) triple-boot OS X, Vista and Ubuntu. I used boot camp to resize the partition, then installed Vista, and finally installed Ubuntu by shrinking the Vista partition. I used a standard Ubuntu hardy install, except I opted at the end to install the boot loader to /dev/sda. 

It worked fine. If I selected the Windows boot option after holding down Alt during the chime, and chose Windows, I saw the GRUB menu from where I could choose either Vista or Ubuntu. 

Today I decided to resize the partitions using Gparted on the Hardy live CD. And now things won't boot. OS X boots fine, but if I select the Windows option I see the word GRUB and a flashing cursor.

I tried installing Refit and that gives menu options for OS X, Windows and Linux, but the WIndows and Linux entries bring up the word GRUB and a flashing cursor. OS X works fine. 

I've booted into live distro mode on the Hardy CD and mounted both the Vista and Ubuntu partitions, so they're there, and they're fine (i checked both using fsck.ext3 and ntfsprogs). It's just that the boot menu is screwed up. I tried reinstalling grub and it seems to work, but again all I get when I boot is GRUB and a flashing cursor. 

Here's the output from the refit partition inspector:


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    105498854  Mac OS X HFS+
 3      105498855    137436074  Basic Data
 4      137436075    154047284  Basic Data
 5      154047285    156296384  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    105498854  af  Mac OS X HFS+
 3 *    105498855    137436074  07  NTFS/HPFS
 4      137436075    154047284  83  Linux

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 105498855:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 07  NTFS/HPFS, active

Partition at LBA 137436075:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

Partition at LBA 154047285:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap

---

### Post by randysparks on 2008-07-18
OK, I fixed it, but not in a way that's 100% fuss-free.

I had to reinstall Ubuntu. In the installer I chose not to repartition or reformat the ext3 partition. This caused the installer to wipe the existing system files but leave my /home/randy directory in place. I created a new user during installation (randy2).

Then I did the following once Ubuntu had booted:

1) Logged in as randy2 and created a new user with my OLD username ("randy" -- the pre re-installation user)
2) I was told there was an existing /home/randy directory that I couldn't use (which is correct), so I entered a new one -- /home/dummy (it doesn't matter what I type, because it's only to allow a new user called "randy" to be created)
3) I then logged out and switched to a virtual console and logged in as "randy"
4) I chown'd /home/randy back to user and group "randy" because, during installation, its ownership had been changed to the new user (randy2) - the command I used was sudo chown -R randy:randy /home/randy/
5) Edited /etc/passwd so that user "randy" used the /home/randy directory, which now had the right ownerships, rather than /home/dummy, as we had set earlier
6) Switched back to the graphical login and logged in as "randy". It worked perfectly -- all my old data and settings were in-tact. In fact, I'm posting from there now. 

The only thing I've lost is the system updates, which need to be downloaded again.

Windows now boots again too, having been detected during installation and given its own GRUB boot entry. 

I'm not sure what GRUB magic the installer does but prior to reinstallation I tried every which way of reinstalling GRUB. But it didn't work. It would be nice if the Ubuntu installer had a "reinstall GRUB" rescue option.

---

### Post by unutbu on 2008-07-18
When you resize partitions (or modify them in any way), their UUIDs change. If you look in /boot/grub/menu.lst you'll probably see a line like 

```
kernel		/boot/vmlinuz-2.6.22-14-generic root=**UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed** ro 

```
This UUID would need to be updated if the partition were resized.

GParted sees its business as dealing only with the manipulation of partitions, and GRUB sees its business as only the booting of OSs. Unfortunately, that compartmentalization leads to GParted making no attempt at anticipating the needs of GRUB users.

---

### Post by cyberdork33 on 2008-07-18
you probably just needed to reinstall grub.

PS the default install location for grub would be /dev/sda

---

### Post by randysparks on 2008-07-19
> **unutbu said:**
> When you resize partitions (or modify them in any way), their UUIDs change. If you look in /boot/grub/menu.lst you'll probably see a line like 

```
kernel		/boot/vmlinuz-2.6.22-14-generic root=**UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed** ro 

```
This UUID would need to be updated if the partition were resized.

GParted sees its business as dealing only with the manipulation of partitions, and GRUB sees its business as only the booting of OSs. Unfortunately, that compartmentalization leads to GParted making no attempt at anticipating the needs of GRUB users.

I'm not sure this is the problem in my case. I didn't even get a GRUB menu. All I got was the word GRUB and a flashing cursor. If what you say is true, I would expect to at least get a boot menu. 

If what you say is true, though, I have real problems understanding why UUIDs are used in GRUB, rather than the old simple device labels. 

> you probably just needed to reinstall grub.

PS the default install location for grub would be /dev/sda 

As mentioned in the original posting, I tried this every which way -- reinstalling grub to /dev/sda0, /dev/sda3 (where the Ubuntu partition was) -- no dice. There's some magic the Ubuntu installer did when reinstalling that I'm not aware of. As mentioned, it may be linked to UUIDs but, if so, the use of UUIDs in the boot menu one of the crappiest ideas ever. The idea of Linux is that it's flexible. The use of UUIDs ties it down to one particular state, or configuration -- just like WIndows.

---

### Post by unutbu on 2008-07-19
This is just a guess:

The "setup (hd0)" command almost-copies /boot/grub/stage1 and /boot/grub/e2fs_stage1_5 to the first sectors of /dev/sda. stage1 occupies the MBR. The bootloader in these first few sectors includes the distance to the root partition containing stage2 and menu.lst, i.e. the distance from the MBR to sda3 in your case. Since the beginning of the partition moved, the number built into the bootloader would be wrong.

I say "almost-copies" because a few bits get modified when "setup (hd0)" copies stage1 and e2fs_stage1_5 to the boot sectors. If these few bits include the distance from the MBR to sda3, then I'm back to square one -- I don't know why reinstalling GRUB with setup (hd0) did not work. If, however, the distance is built into either stage1 or e2fs_stage1_5, and this distance gets copied into the bootsector, then clearly this will cause GRUB to fail on boot, because the true distance between the MBR and sda3 had not been updated. (GParted does not modify stage1, or e2fs_stage1_5.)

In that case, the fix, according to caljohnsmith: [http://ubuntuforums.org/showpost.php?p=5247838&postcount=15](http://ubuntuforums.org/showpost.php?p=5247838&postcount=15)
is to use 

```
sudo grub-install /dev/sda
```

because this regenerates the stage* files.

---

### Post by cyberdork33 on 2008-07-19
> **randysparks said:**
> As mentioned in the original posting, I tried this every which way -- reinstalling grub to /dev/sda0, /dev/sda3 (where the Ubuntu partition was) -- no dice.
I was referring to one statement:
> **randysparks said:**
> I used a standard Ubuntu hardy install, except I opted at the end to install the boot loader to /dev/sda.
Since that is already the default location, that is still a standard install.

---

