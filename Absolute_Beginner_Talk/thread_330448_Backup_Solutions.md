---
title: "Backup Solutions?"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by rockin_goliath on 2007-01-03
I am new to Ubuntu and Linux, and I am looking for a good backup solution. I am trying to avoid proprietary software, but I liked the simplicity of Norton Ghost on my windows machine. Is there a software backup solution out there with a nice GUI and good integration with the Ubuntu desktop (gnome) where I can just tell it to backup my whole harddisk to an external harddrive, and then boot to the backup to restore my computer if I need to? Thanks!

---

### Post by xyz on 2007-01-03
Here's a couple of ways:
[Howto: Backup and restore your system!]("http://ubuntuforums.org/showthread.php?t=81311&highlight=backup+windows+drive")
[Partimage]("http://www.psychocats.net/ubuntu/partimage")
Good luck and let us know...

---

### Post by indytim on 2007-01-03
I'll second the motion on partimage.  I've been using it for a couple of months to back up my ops partitons (Win2k, Ubuntu-Dapper, Kubuntu-Edgy) on a weekly basis.  Must admit, haven't had the opportunity (or need) to reverse install yet.

Good Luck,

IndyTim

---

### Post by squrl on 2007-01-03
I've also been using part image. It is as good as I can find.

It has a drawback that you need to use the rescue CD to make it do a complete restore and mounting an external drive got a little confusing. My wife and I on a lan now back up with part image to a newtork drive with part image.

---

### Post by wieman01 on 2007-01-03
There is a full guide for Partimage in my signature.

---

### Post by indytim on 2007-01-03
Wieman01,

Nice tutorial.  I wasn't aware of the problems with saving the partition image as a .tar.gz.  In my case I'm tri-booting.  The backups that I'm running are the partitions containing the ops system.  I think I would not have to be concerned with the Rescue CD as I can boot to the op system that is still intact and restore the partition of the failed ops.  Or, am I missing something?

IndyTim

---

### Post by wieman01 on 2007-01-04
> **indytim said:**
> Nice tutorial.  I wasn't aware of the problems with saving the partition image as a .tar.gz.  In my case I'm tri-booting.  The backups that I'm running are the partitions containing the ops system.  I think I would not have to be concerned with the Rescue CD as I can boot to the op system that is still intact and restore the partition of the failed ops.  Or, am I missing something?
Yes, that's the case. You could restore your various partitions anytime you want. However, I have never tested it with a Windows system.

---

### Post by indytim on 2007-01-04
On my last backup, I did, in fact backup the Windows partition.  I think partimage provided some warnings about NTFS restores as being un-tested.  So I guess I've been forwarned.

IndyTim

---

### Post by wieman01 on 2007-01-04
NTFS could be a problem indeed. FAT32 may be ok though. Let us know how it goes later on... Just for the record.

---

### Post by kebes on 2007-01-04
This LinuxJournal article:
[http://www.linuxjournal.com/article/8931](http://www.linuxjournal.com/article/8931)

Describes a few different backup solutions that are GUI-based and quite user-friendly. They are designed for backing-up user files in an easy way. For doing a full disk backup I agree partimage is a good choice.

---

### Post by dannyboy79 on 2007-01-04
i believe he is asking for a gui, part image is far from a gui and it also isn't a realistic option for users whole aren't dual booting with 2 linux distros as you can't use part image on a mounted filesystem! so this basically takes away unattended backups then doesn't it. so that leaves this guy booting to a part image cd or kanopix or whatever distro and then backing up his partitions etc etc etc. I don't see this as a valuable backup solution for immediate failure recovery. I see part image being a good backup solution only for times where say you have your machine in a prestine setup and you want to capture that so you can use it for easy reinstallation to the same setup or for ghosting. anyway, I myself use sbackup. also known as simple backup. it's really configurable and allows it to be run from cron, it allows incremental backups, it also allows acking up to an ssh server or ftp server which obviously is optimal since a backup is in case your main computer's hard drive dies so it's no good to back it up to itself, sure you can put it on another partition but again, thats not optimal. So, my vote is for sbackup.

---

### Post by carlosfocker on 2007-01-05
Personal Backup (VMware) Appliance is a good imaging tool.  

[http://sourceforge.net/projects/pba-vm](http://sourceforge.net/projects/pba-vm)

---

### Post by TonioRoffo on 2007-01-16
Does PartImage work for mounted filesystems, in a secure way?  Like Acronis TrueImage would do?

Or ghost 9, livestate, drive snapshot, ... on Windows?

Seems there's no tool that can do live sector based snapshots while a system is in use (using a filter driver to catch drive changes during backup)

Thanks

---

### Post by dannyboy79 on 2007-01-16
> **TonioRoffo said:**
> Does PartImage work for mounted filesystems, in a secure way?  Like Acronis TrueImage would do?

Or ghost 9, livestate, drive snapshot, ... on Windows?

Seems there's no tool that can do live sector based snapshots while a system is in use (using a filter driver to catch drive changes during backup)

Thanks


I know for a fact that Part image can't be used on  a mounted filesystem! I just use sbackup which does run and work with the filesystem mounted! you could also use dar which is way more configurable than simply using tar a  backup command. you can even split the images so you can then burn them onto dvd's for safe keeping.

---

