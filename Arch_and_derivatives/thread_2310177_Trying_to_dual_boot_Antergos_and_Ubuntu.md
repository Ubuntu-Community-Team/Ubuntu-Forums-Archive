---
title: "Trying to dual boot Antergos and Ubuntu"
date: 2016-01-16
forum: Arch and derivatives
---

### Post by WinterMadness on 2016-01-16
I'm at the partition manager.

Heres what I have:

/dev/sda
-/dev/sda1 type: fat 32 label efi
-/dev/sda2 type: ext4 label: Ubuntu
free space
/dev/sda3 type: swap

how do I properly allocate the free space so that I can choose Ubuntu or Antergos? 

Do I need to do boot partitions and stuff here? I dunno, can someone give me a list of steps?

---

### Post by Cavsfan on 2016-11-25
> **WinterMadness said:**
> I'm at the partition manager.

Heres what I have:

/dev/sda
-/dev/sda1 type: fat 32 label efi
-/dev/sda2 type: ext4 label: Ubuntu
free space
/dev/sda3 type: swap

how do I properly allocate the free space so that I can choose Ubuntu or Antergos? 

Do I need to do boot partitions and stuff here? I dunno, can someone give me a list of steps?

There are only 4 possible physical partitions on hard disks. 
So, you would need to move that free space to the end and have sda4 as your extended partition.

Then you can create logical partitions or else if you only need 4 use the free space as your Antergos partition.
All you need is one partition for your system - mount point / unless you want to have separate home, system, etc. partitions.

I've got Arch Linux installed along with Windows 10, a few Ubuntu partitions and a 1MB swap file.
The swap file isn't used for anything that I know of other than allowing you to hibernate your system instead of putting it in suspend or sleep mode.
Since I use only sleep mode I just have to have a swap file, so the 1MB is OK for me.

I'm not real sure about efi though or if it makes a difference.

---

### Post by oldfred on 2016-11-25
If you have an ESP - efi system partition and drive is gpt partitioned, then Ubuntu is installed in UEFI boot mode. And you do not have a 4 partition limit but a soft 128 partition limit with gpt partitioning.

Do not know about Arch but most installers, have to be booted in UEFI mode to install in UEFI mode.
And some other systems use LVM or other formats as defaults. If dual booting often better to stay with ext4. And if using both a lot, a shared partition may make sense but other distributions do not always use user 1000 as default and if not 1000 mounting & using a shared partition can be difficult.

---

### Post by Cavsfan on 2016-11-26
> **oldfred said:**
> If you have an ESP - efi system partition and drive is gpt partitioned, then Ubuntu is installed in UEFI boot mode. And you do not have a 4 partition limit but a soft 128 partition limit with gpt partitioning.

Do not know about Arch but most installers, have to be booted in UEFI mode to install in UEFI mode.
And some other systems use LVM or other formats as defaults. If dual booting often better to stay with ext4. And if using both a lot, a shared partition may make sense but other distributions do not always use user 1000 as default and if not 1000 mounting & using a shared partition can be difficult.

Good info! I guess I was out of my league talking about my 6 year old computer that is limited to 4 partitions. Maybe some day I'll get a new one that uses UEFI and SSDs.

---

### Post by Cavsfan on 2016-12-05
I do know that Arch Linux has no GUI. I had to install the ArchWiki Viewer on my Android phone and go by those instructions.

[https://play.google.com/store/apps/details?id=com.gsc.archwikimanual](https://play.google.com/store/apps/details?id=com.gsc.archwikimanual)

You literally have to look at the phone while you are building the system from scratch; piece by piece until you have something you can boot into. 
Then you reboot and add the DE you want to use.
I just have [Xfce]("https://wiki.archlinux.org/index.php/Xfce") and nothing else. 

Then once you have a DE and a browser you can get further instructions here: [Arch Linux Installation Guide]("https://wiki.archlinux.org/index.php/installation_guide"). It can sense you have an UEFI system.
Which is basically what's on the wiki viewer.

Nothing is automatically installed without you doing it. So, you have only what you want to have.

I also do not have any display manager. I just boot into TTY1, login which starts X and the startxfce4 command and it's up and ready to go.

The beautiful thing about Arch Linux is that there is no version or cycle, it just keeps updating; manually of course to the most cutting edge things available.
Here is the current kernel:
```
[cavsfan@Le-Beast ~]$ uname -r
4.8.11-1-ARCH
```

There is a LTS kernel that you can choose to install and use plus there is a fallback to the main kernel and also the LTS kernel.

---

### Post by Cavsfan on 2016-12-05
Oops my bad! I thought the OP was asking about installing Arch Linux or Antergos.

---

