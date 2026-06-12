---
title: "How safe is my data?"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by l|s on 2006-10-05
I’ve been thinking recently about setting up Ubuntu for my server for some time now but there’s one thing that keeps bothering me is how safe is my data on there?

I’m a bit of a Linux newb, I’ve had experience with a lot of distros over the years but ive never gotten in depth with them. I currently have 1.7TB worth of data under windows and just want to know how safe my data would be under linux from file system failures and OS failures but most importantly from myself? How badly could I screw up all the data on the other hard drives if I kept the OS on a separate drive? 

Also if I need to reinstall Ubuntu or maybe down the line if I find another distribution more suited to my needs would they pick up my logical volume groups and volumes?

Thanks in advance for any help or advice you can provide on this matter.

---

### Post by sbergman27 on 2006-10-05
Are you asking if Linux is so new and unstable that it might eat your data?

No.

Might some of your hard drives die a natural death, taking your data with them?

Absolutely.

You do regular backups, though.  Right?

If you quarantined the data-eating Linux on a separate drive, you could still destroy your data with:

sudo dd if=/dev/zero of=/dev/the_harddrive_device_name

You'd have to enter your password after that.

Linux's ext2/3 filesystem has been rock solid since the Windows 3.1/fat16 days.  Would you trust your 1.7 terabytes of data to Windows 3.1 and fat16?

---

### Post by l|s on 2006-10-05
No i never thought linux was new or unstable.

I’m just asking what things i could do which would really fubar things up and corrupt the file system and lose data . I don’t think i have a chance off accidentally typing out a big command like that though.

Yeah i regularly backup my important personal data.

No i dont trust windows xp and ntfs with my data (after two sever crashes resulting in a lot of data loss) let alone 3.1

What about the logical volume groups and volumes? Would they still exist and work after reinstallation or installing of a new distro?

---

### Post by jaboua on 2006-10-05
I would have to add that some of your data might get corrupted if there for example is a power loss while you are writing something to disk - especially if it's writing the metadata... However in many situations the data will be just fine after power loss, with my reiserfs /home partition I must have had at least 30 unclean poweroffs, and it's still working. An other box I have however had parts of the filesystem (JFS) borked after something similar though...

---

### Post by sbergman27 on 2006-10-05
> **jaboua said:**
> I would have to add that some of your data might get corrupted if there for example is a power loss while you are writing something to disk - especially if it's writing the metadata...

No.  The default ext3 filesystem makes greater data integrity guarantees than most other journalled filesystems.  It always journals metadata, but has 3 data journalling policies one can select.  Here is a rundown of them:

data=journal: After an unclean shutdown, Fileysystem and
metadata are guaranteed to be consistent. If the application was told that a data write occurred, it did. (Slowest writes.)

data=ordered: The default. After a power outage, the filesystem and metadata are guaranteed to be consistent. The file contents are guaranteed not to be garbage. BUT, the data might not be the latest written. (Medium speed writes.)

data=writeback: This is the level that most journaled filesystems
give you.  In particluar, NTFS uses this level.  After an unclean shutdown, filesystem and metadata are
guaranteed to be consistent. Files can contain garbage. (Fastest
writes.)

BTW, modern distros are going to recognize volume groups and logical volumes created by other distros.

In the case of Ubuntu, you do need to install from the "alternate cd" to do a custom LVM setup.

---

### Post by slightcrazed on 2006-10-05
Data integrity is very relative, and I would say actually has less to do with the OS then it does with filesystem (as others have said) and hardware solutions (UPS, RAID, SCSI etc...). The one place where the application layer (including the OS) plays a role is with security issues. 

In the end I don't think that your data is any less safe on Linux than on any other OS, but I do think that there are advantages to be had using the filesystems and inherent security and stability benefits of linux (or BSD, or AIX or just about any of the *nix family OSes). 

Is there stuff that you, as an admin, could do to muck up the files or cause yourself headaches? Yes, of course there is, but this is true of any OS. In the end, that is the wrong question to ask.

Is linux good for file storage? Absolutely! 
Is it better than windows at that same task? 

Wrong forum to ask that question at. :-)

slight

---

### Post by sbergman27 on 2006-10-05
> **slightcrazed said:**
> 
Is linux good for file storage? Absolutely! 
Is it better than windows at that same task? 

Wrong forum to ask that question at. :-)

From a filesystem design standpoint, Linux is better.  This is not simply a matter of opinion.  As per my previous post, ext3 in either its default data=ordered mode, or in the more conservative data=journal mode, Linux provides integrity guarrantees that NTFS simply cannot.  data=journal gives you the same level of protection as mounting the filesystem synchronously while still achieving a good level of performance.

---

