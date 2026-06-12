---
title: "Question about dual booting"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by Il_Tuo_Nome on 2006-01-15
Currently,

I am dual booting XP on my 120 gig C: drive and Ubuntu on my 20 gig D: drive. Now that I have familiarized myself much better with Ubuntu/Linux, I would like to put my Ubuntu on the bigger drive. I don't feel I need to resort to Windows nearly as much. My question is, is there anykind of problem with having Ubuntu as my main OS on the C: drive, since right now the MBR is located on the Windows partition.

Thank you in advance

---

### Post by npmeyer on 2006-01-15
So, if I understand you correctly, you want to swap the two drives, so you have Windows on the smaller drive and Ubuntu on the larger one?

I don't think there's anything to worry about.  How do you intend to do this?  Were you going to reinstall both operating systems, or were you going to use some sort of partition imaging software?  Your method might make a difference.

---

### Post by Il_Tuo_Nome on 2006-01-15
Correct, I do want to swap them. I was planning fresh installs for both. In the past I had asked about doing this, and was told it would effect the MBR, since that normally runs from the windows partition.


many thanks

---

### Post by npmeyer on 2006-01-15
If you're planning fresh installs, this shouldn't make a difference. When you install Windows, it should write a new MBR to the primary hard drive (the 120 gig one) and then after that, you can install Ubuntu, and have it write a new MBR to that same drive, overwriting the Windows-created MBR. Then you should be able to use GRUB to get into both Ubuntu and Windows.

So, I guess it does "affect" the MBR, technically speaking, but in the end you should still end up with a usable configuration.

Anyone who knows more about this can feel free to contradict me on this.

---

### Post by Il_Tuo_Nome on 2006-01-15
I'm nt sure if I read you correctly. Are you saying when I install windows on my D: drive (20 gig) it will create a new MBR on the C: drive (120 gig) or on the D: drive?

---

### Post by mustang on 2006-01-15
[QUOTE=npmeyer]If you're planning fresh installs, this shouldn't make a difference. When you install Windows, it should write a new MBR to the primary hard drive (the 120 gig one) and then after that, you can install Ubuntu, and have it write a new MBR to that same drive, overwriting the Windows-created MBR. Then you should be able to use GRUB to get into both Ubuntu and Windows.

So, I guess it does "affect" the MBR, technically speaking, but in the end you should still end up with a usable configuration.

Anyone who knows more about this can feel free to contradict me on this.[/QUOTE]

Correct. Just remember to install windows first.

---

### Post by jimrz on 2006-01-15
Unless you really want to do fresh installs, why not leave as is...use qparted (live cd), partion magic or whatever to re-do your primary drive with a large FAT32 partition (accessible from both ubuntu and win) and keep the bulk of your stuff on it.

---

### Post by Il_Tuo_Nome on 2006-01-15
[QUOTE=jimrz]Unless you really want to do fresh installs, why not leave as is...use qparted (live cd), partion magic or whatever to re-do your primary drive with a large FAT32 partition (accessible from both ubuntu and win) and keep the bulk of your stuff on it.[/QUOTE]

I thought about that, until I remembered all the problems xp was giving me with corrupt files. So I would rather install Ubuntu on a clean install.

---

### Post by Il_Tuo_Nome on 2006-01-17
well, I took the plung. Re-installed windows first on the 20 gig drive, but before that it prompted me to partition a section on the 120 gig so it could load the MBR. So both OSs installed fine. Now the problem is GRUB doesn't recognize the XP partition. And when I look in Systems>>Administration>>Disks, it tells me the 20 gig is inaccessible. Does anyone know why that would be? Before I installed Ubuntu I could get to XP, now I can't. Someone please help me solve this.

Thank you

---

### Post by npmeyer on 2006-01-17
It may be that you cannot access that partition because it is being mounted with root as the owner (since windows filesystems don't support Unix-style ownership and permissions) and therefore you can't browse that drive as a normal user.  You can check the starter guide at [http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions](http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions) to see how to mount windows partitions so they are readable by Linux.

It does surprise me though that GRUB can't access that disk either.  Did the Ubuntu Installer provide you with the option of specifying a mount point for that drive?  Usually, it does this during the partitioning process.  Since you had Ubuntu there before, I'd be very surprised if the installer stopped recognizing it completely.

---

### Post by shania98 on 2006-01-17
[QUOTE=npmeyer]If you're planning fresh installs, this shouldn't make a difference. When you install Windows, it should write a new MBR to the primary hard drive (the 120 gig one) and then after that, you can install Ubuntu, and have it write a new MBR to that same drive, overwriting the Windows-created MBR. Then you should be able to use GRUB to get into both Ubuntu and Windows.

So, I guess it does "affect" the MBR, technically speaking, but in the end you should still end up with a usable configuration.

Anyone who knows more about this can feel free to contradict me on this.[/QUOTE]
i have question, how would your bios be set up for this config?

---

### Post by mustang on 2006-01-17
Your primary master must be which ever hard drive has the MBR on it. In the case of the thread starter, it'd be the one with windows on it. You can set the other hard drive to whatever you please.

---

### Post by otetiani on 2006-01-17
I've been working on this for over a week now.  I did excactly the same thing.

XP was installed on my 120G Primary.

I installed Ubuntu on my 250G SATA drive.

I could only boot Ubuntu and couldn't access the Primary HD at all and Grub installed wrong and wouldn't let me select XP.

After waiting several days and trying the limited info suggested or googled:

So I decided to reinstall Ubuntu, clean install.  This was stupid, I lost all access to both HD's and The Ubuntu install wouldn't format either drive so I lost both.

Currently I am just trying to format either drive to get XP back (I use Skype with my family, and the Linux Skype doesn't allow me to see my contacts that use Windows?)

Next step if the XP install works is to partition the small drive to dual boot XP and Ubuntu and wipe the 250G drive.

Did I read correctly that if I format my 2nd drive as FAT32 I can store both XP and Ubuntu files on it to share?

---

### Post by mdsmedia on 2006-01-17
[QUOTE=otetiani]
Did I read correctly that if I format my 2nd drive as FAT32 I can store both XP and Ubuntu files on it to share?[/QUOTE]
The short answer is that Linux and Windows can read and write FAT32 partitions. 

Linux can't WRITE to NTFS and Windows can't READ/WRITE Ext2/3 partitions.

If you format one drive as FAT32 and install both OSs on the other (XP on NTFS partition and Ubuntu on Ext2/3 partition), you will be able to read/write from both OSs, the FAT32 formatted drive.

---

### Post by Il_Tuo_Nome on 2006-01-18
[QUOTE=shania98]i have question, how would your bios be set up for this config?[/QUOTE]



I'm sorry, but I'm not sure exactly what you mean by that. If you mean it shows my 120 gig as my primary and 20 gig as secondary, then yes.


thank you

---

### Post by Il_Tuo_Nome on 2006-01-18
[QUOTE=mustang]Your primary master must be which ever hard drive has the MBR on it. In the case of the thread starter, it'd be the one with windows on it. You can set the other hard drive to whatever you please.[/QUOTE]


I did notice, both drives having MBR on then. Can that be changed?


thank you

---

### Post by Il_Tuo_Nome on 2006-01-18
A friend of mine was telling me, since I XP successfully installed, I should add Ubuntu. And assuming it doesn't detect me running another OS (it hasn't during this whole process), he feels I should add it to GRUBs menu. Does that seems that it could work? And if so, could someone please tell or show me how I can do that?

Thanks again very much

---

### Post by shania98 on 2006-01-18
[QUOTE=Il_Tuo_Nome]A friend of mine was telling me, since I XP successfully installed, I should add Ubuntu. And assuming it doesn't detect me running another OS (it hasn't during this whole process), he feels I should add it to GRUBs menu. Does that seems that it could work? And if so, could someone please tell or show me how I can do that?

Thanks again very much[/QUOTE]
bump, keep thread alive

---

### Post by Il_Tuo_Nome on 2006-01-19
I figured out the problem, at least for my situation. I will explain how I did it in a couple of hours. I just got everything done and now I need to leave for a bit.




Talk to you soon

Thanks

---

### Post by Il_Tuo_Nome on 2006-01-19
Well, after many many formats and installs, I finally accomplished through trial and error. I needed to install XP first, so after deleting the partitions on both drives, in order for me to be able to install XP on the 20 gig, I had to create a partiton on the 120 gig. Well, like a pinsnap, I kept deleting that, when I would manually partition during the Ubuntu install. After all that my partitions look like the following:

> IDE1 master (hda) – 120.0 GB
						#1 primary 2.2 GB FAT32 /media/hda1
						pri/log 117.9 GB FREE SPACE
IDE1 slave (hdb) 20.5 GB
						#1primary 20.5 GB FAT32 /media/hdb1
						pri/log 8.2 MB FREE SPACE

The 117.9 GB of free space had to be formatted, and it automatically did it, creating a swap and extended partitions. So instead of messing with it more, I left it at that, since it accomplished what I needed. Of course this worked for me, that's not to say it couldn't of been done better.

Thank you everyone for the input.

---

