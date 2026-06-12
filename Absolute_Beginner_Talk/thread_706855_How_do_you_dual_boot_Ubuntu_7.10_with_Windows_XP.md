---
title: "How do you dual boot Ubuntu 7.10 with Windows XP?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Bigbob22 on 2008-02-24
I am new to Linux and I heard about dual booting. I want to keep the data of my Window XP computer and have Linux. How can I do this. I do have a Live CD of Ubuntu 7.10.

---

### Post by overdrank on 2008-02-24
> **Bigbob22 said:**
> I am new to Linux and I heard about dual booting. I want to keep the data of my Window XP computer and have Linux. How can I do this. I do have a Live CD of Ubuntu 7.10.

HI and this link has good info
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Oldsoldier2003 on 2008-02-24
Overdranks link is a good starting point.

 I've run a dual boot Ubuntu /XP for quite some time now with absolutely no problems.

something else to consider:
 If you have the space available and don't use windows a lot you can shrink the [partition that windows lives on and make it part of your linux sytem. Or turn it into a NTFS patition and mount it as a shared data drive available for to both linux and XP.

---

### Post by northern lights on 2008-02-24
> **Oldsoldier2003 said:**
>  If you have the space available and don't use windows a lot you can shrink the [partition that windows lives on and make it part of your linux sytem. Or turn it into a NTFS patition and mount it as a shared data drive available for to both linux and XP.

If he's running XP for a while already, regardless of whether he's got one or more partitions, something's gotta be shrunk no matter what - or do you suppose he's got 5 or more gigs of unallocated space lying around since he bought his comp?

So @ Bigbob:

Shrink some partition by a minimum 6 gigabytes. Create an X gig large (I'd recommend 10 if you wanna store personal data on your NTFS, otherwise more) ext3 partition and a 1 gig swap. Set the newly created ext3 as root (/) and install. Ubuntu installation will install GRUB (a bootloader) in the end and Windows and Ubuntu will both be selectable upon booting. This is not the case if you have Linux setup and thereupon (re)install Windows...

---

### Post by tuskenraider on 2008-02-24
what ive done on a couple o peoples computers... was ran partition magic and shrank the xp partition down to what ever size i felt it needed to be. and after partition magic was done.. i booted into the live cd...and intstalled ubuntu... i felt it was alot easier than using ubuntu's partition manager...  idk maybe it was just me...anyway.. just a thought on dual booting..  oh and btw... once you start dual booting... youll wonder why you ever used windoze in the first place!! :lolflag:  

tusken

---

### Post by Bigbob22 on 2008-02-24
It only has two options for me. I want to dual boot and i don't know how to do it manually. The first options uses the entire disk. What do I do?And if there is a way to share the files between Ubuntu and XP please tell me how to do it.

---

### Post by northern lights on 2008-02-24
No - do **not** use the entire disk! (Unless you want your windows to be overwritten...)

> **northern lights said:**
> Shrink some partition by a minimum 6 gigabytes. Create an X gig large (I'd recommend 10 if you wanna store personal data on your NTFS, otherwise more) ext3 partition and a 1 gig swap. Set the newly created ext3 as root (/) and install. Ubuntu installation will install GRUB (a bootloader) in the end and Windows and Ubuntu will both be selectable upon booting. This is not the case if you have Linux setup and thereupon (re)install Windows...

---

### Post by Bigbob22 on 2008-02-24
What does your quote mean? And I dont want to (re)install windows. I want to keep the data I have. I have already created a restore point. BTW i am currently running from the live CD.

---

### Post by northern lights on 2008-02-24
There are several filesystem a harddrive or partition can be formatted with. Your windows partition is formatted as "NTFS". Ubuntu can read and write on that partition, but it cannot be installed on it. You need to create an extra partition for ubuntu to run on. So resize your windows partition (or any other, if you have more than one), free up 11 gigabytes for now. Create a 10 gig partition for Ubuntu, choose "ext3" as the filesystem. The last gig you create as a swap partition - its function is that of the pagefile in Windows.

---

### Post by Bigbob22 on 2008-02-24
oh, okay.

---

### Post by torgrot on 2008-02-24
At the point where it says use the entire disk, there is a button near the bottom of the dialog that says manual or guided or something, I don't remember off the top of my head.  If you click that it will let you choose to shrink the windows partition and use the free space for ubuntu.

torgrot

---

### Post by Niketas on 2008-02-25
Well, there are options for using "**Entire Disk**" or "**Manual**" configuration. So the author should select "**Manual**" and go through the partitioning procedure. 

Actually, if the Windows partition has got enough free space, afaic in the "Entire Disk" dialog there is a slider that chooses how much space of the entire disk wil be used by Ubuntu. In my case I've luckily selected amount that is nearly less than free space on my Windows partition, so Ubunty gently took it, making no harm to Windows. So cute! ;) 

After installation, Ubuntu will dual boot with your Windows. The GRUB Loader will offer Ubuntu first, so you will have less chance to use Windoze :KS

---

### Post by Bigbob22 on 2008-02-25
Can some one give me a guide on how to do this. And if there is any possible way to share the files on both please tell me. Thanks in advance.

---

### Post by northern lights on 2008-02-25
Gutsy can read from and write to NTFS partitions, and all such partitions will be automatically mounted (they'll be there, on the desktop) and accessible from the first start of the system.

Windows cannot natively read ext3 (the filesystem you'll be installing Ubuntu on). In order to accomplish this, you could install [linux-reader]("http://www.diskinternals.com/linux-reader/") or [Ext2IFS]("http://www.fs-driver.org/")...

---

### Post by Bigbob22 on 2008-02-25
I just want to know how to do what you said about shrinking and stuff. How do you do that. And why is it only showing two options instead of three? I have 49GB free on that partition.

---

### Post by HoLLyw00dGT on 2008-02-27
I am doing the same thing as you know northern, i created partitions before installing this time. I made a new one and selected ext3 in the drop down menu...what do you mean set it as root (/) ? How and why?

---

### Post by northern lights on 2008-02-27
If you're installing from the Live CD with a GUI, then that's redundant. I think clicking something along the lines of "Install Ubuntu on this partition" is all you need to do. Anyhow, there's a graphical selection and all you gotta do is follow installation instructions, if you've done the manual partitioning like I've posted earlier.

> **northern lights said:**
> Erase the old ext2

| Windows/279 | unallocated space/16 | ext2/3.4 | unallocated/128 |

After deleting the ext2, it should be:

| Windows/279 | unallocated/148 |

and then you either make it

| Windows/279 | Ubuntu/ext3/147 | swap/1 |

or, for instance, anything along the lines of

| Windows/279 | Ubuntu/ext3/20 | swap/1 | ... | ... | or how many ever more partitions you feel like having for data storage (NTFS is read by both OSs) |

---

