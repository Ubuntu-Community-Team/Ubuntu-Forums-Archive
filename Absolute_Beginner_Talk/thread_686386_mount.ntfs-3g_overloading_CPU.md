---
title: "mount.ntfs-3g overloading CPU"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Herbivore on 2008-02-03
Assistance needed! Recently the CPU usage has  been maxing out. Ran top and problem is mount.ntfs-3g. After searching here i found the link to [http://ntfs-3g.org/support.html#cpu100](http://ntfs-3g.org/support.html#cpu100) but I am probably too new to follow the instructions. I have rsync backing up to an internal ntfs drive and also to an external usb ntfs drive. It has been working fine for months. Could the drives be fragmented? Tried to use ntfsprogs but again, it is above my level of experience. Attempts to access the volumes was met with errors  I don't understand (what is an inode?) or that I have not been able to respond to. System is Linux Mint only, not a dual boot. All packages are up to date. Happy to supply logs, etc if instructions are given how to get them. Thank you for any suggestions.

---

### Post by bumanie on 2008-02-03
I have little idea about your specific question, but as no-one else had given you an answer, I propose the following (based upon very basic trouble shooting)
Go to synaptic and in search type ntfs-3g and uninstall it and then reinstal itl, just in case you initially got a corrupted file.
It may not help, but's worth a try.

---

### Post by 3rdalbum on 2008-02-03
> **bumanie said:**
> I have little idea about your specific question, but as no-one else had given you an answer, I propose the following (based upon very basic trouble shooting)
Go to synaptic and in search type ntfs-3g and uninstall it and then reinstal itl, just in case you initially got a corrupted file.
It may not help, but's worth a try.

It's not likely to do anything - the packages are checked using MD5 checksums, so it's impossible to install a corrupted package. But I appreciate you trying to give the OP some help :-)

It could be a fragmentation problem, but on my old dual-boot computer I always noticed that mount.ntfs-3g always used up a lot of CPU when writing a lot of files (or large files).

There probably isn't a lot you can do, but I hear that the NTFS-3G team are now working on optimising the driver. If there's a later release, you could try upgrading to it manually.

---

### Post by bumanie on 2008-02-03
> It's not likely to do anything - the packages are checked using MD5 checksums, so it's impossible to install a corrupted package. But I appreciate you trying to give the OP some help 
Agreed, it just that I did that once with something (can't remember what) and then it worked - ???why - some glitch????
Did read  [http://ntfs-3g.org/support.html#cpu100](http://ntfs-3g.org/support.html#cpu100), at the bottom of the page there is a new, stable release from Jan 29th, download that and try to install it. It is a .tar file - follow this to help install it [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
If that doesn't work, post any errors you are getting and someone will help.

---

### Post by szaka on 2008-02-03
From the FAQ you quoted:
[i]
Some softwares indeed do intensive file operations sometimes (Beagle, Amarok collectionscanner, updatedb, etc). The CPU usage is not directly visible in case of kernel file system drivers but obviously this is not true for user space drivers. That is, they are in the process list unlike the kernel drivers.
[/i]
Rsync is also a software which intensively uses the file system. When something uses a file system intensively then the file system intesively uses the CPU because it must check, calculate, analyze file system information where to put files and their data, etc. A file system driver is also a software and uses the CPU the same way as any other software.  So, what you see is exactly what one should expect when the driver is intensively used.

And yes, when the disk is close to full or very fragmented then the driver must do more work, so it must use more CPU, hence you will also see higher CPU usage.

---

### Post by Herbivore on 2008-02-03
> **bumanie said:**
> I have little idea about your specific question, but as no-one else had given you an answer, I propose the following (based upon very basic trouble shooting)
Go to synaptic and in search type ntfs-3g and uninstall it and then reinstal itl, just in case you initially got a corrupted file.
It may not help, but's worth a try.

Thanks. Tried that, and after uninstalling, ran top... mount.ntfs-3g still hogging! Reinstalled ntfs-3g.

---

### Post by Herbivore on 2008-02-03
> **szaka said:**
> From the FAQ you quoted:
[i]
Some softwares indeed do intensive file operations sometimes (Beagle, Amarok collectionscanner, updatedb, etc). The CPU usage is not directly visible in case of kernel file system drivers but obviously this is not true for user space drivers. That is, they are in the process list unlike the kernel drivers.
[/i]
Rsync is also a software which intensively uses the file system. When something uses a file system intensively then the file system intesively uses the CPU because it must check, calculate, analyze file system information where to put files and their data, etc. A file system driver is also a software and uses the CPU the same way as any other software.  So, what you see is exactly what one should expect when the driver is intensively used.

And yes, when the disk is close to full or very fragmented then the driver must do more work, so it must use more CPU, hence you will also see higher CPU usage.

Szaka, What do you think of Bumanie's idea: [from] [http://ntfs-3g.org/support.html#cpu100](http://ntfs-3g.org/support.html#cpu100), at the bottom of the page there is a new, stable release from Jan 29th...

---

### Post by bumanie on 2008-02-03
Refer to post #2 and my next #3. When I first wrote that, with reference to post #2, I realised what I had said would not work for something which is integrated in the kernel. Post #4 indicates high cpu usage not unusual (and he is a ntfs-3g developer, so he should know). The only thing you have left to try is to download the most recent stable release of ntfs-3g from the site you linked to. Follow the link I gave you. If you have problems and get errors, cut and paste the errors to the forum and someone will be able to point you in the right direction. Of course there is no guarantee that the latest release will be any better. out of interest, what are your computer specs?

---

### Post by Herbivore on 2008-02-03
> **bumanie said:**
> Refer to post #2 and my next #3. When I first wrote that, with reference to post #2, I realised what I had said would not work for something which is integrated in the kernel. Post #4 indicates high cpu usage not unusual (and he is a ntfs-3g developer, so he should know). The only thing you have left to try is to download the most recent stable release of ntfs-3g from the site you linked to. Follow the link I gave you. If you have problems and get errors, cut and paste the errors to the forum and someone will be able to point you in the right direction. Of course there is no guarantee that the latest release will be any better. out of interest, what are your computer specs?

Thanks for your help. 

First, computer info: 
AMD 64 3200+
nVidia GeForce 6600
2 GB RAM
Linux Mint 3.0 Cassandra (Main Edition with Gnome desktop)
ntfs-3g version installed is 1:1.328-1 (feisty)

And attached are screenshots of partitions (didn't know how to get this in a report.)

Next, I tried unsuccessfully to install from source the most stable release of ntfs-3g as you suggested. My experience and knowledge are insufficient to do this without more assistance. The tar file was downloaded to the Desktop. The help page containing Section 4, "Installing from source" was appreciated, but i was unsuccessful. I ran the following terminal commands:

sudo apt-get update
sudo aptitude update
sudo aptitude install build-essential
tar -xvzf ntfs-3g-1.2129

Result: 

tar: ntfs-3g-1.2129/[B: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
pampa1@pampa1:~$ tar -xvzf ntfs-3g-1.2129
tar: ntfs-3g-1.2129: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: Error exit delayed from previous errors

So, I never was able to sudo make install (or sudo checkinstall -D to make a .deb file -- I downloaded Checkinstall).

Since the volumes do not appear to be too full, and the CPU overload is a relatively recent phenomon,  the problem may be fragmentation from the constant rsync backups. Backups are going to both volumes sda1 and hdd1. hda1 is for data storage only. Not using home directory for work data. 

Suggestions on how to defrag an NTFS volume without Windows would be helpful.

I should mention that this is a work computer and although I have most data backed up, I would be at a loss to reconstruct the system. Such an effort would require tutoring probably beyond the scope of a forum not to mention your (plural) free time!

---

### Post by bumanie on 2008-02-03
I have only extracted .tar.bz2 and .tar.gz files, not just .tar files, but I hope this will work. Iin terminal type > sudo tar xvf ntfs-3g-1.2129.tar

---

### Post by Herbivore on 2008-02-04
Well, thanks for all your help on this. I've come to a workable conclusion which may not be correct that the problem with the CPU overloading is caused by fragmented drives. Since there appears to be no way to defrag them within Linux, i have no choice but to reformat a drive and install Windows in an 8 GB partition and go for Mint Daryna in another partition as a clean install. Since the data is on a different drive which will be unplugged during this operation to keep the data safe, i may only be looking at the pains of re-installing desired apps and getting configurations such as for DOSbox (used for Alpha4 DOS database - #-o retro, i know). Hopefully, whatever ntfs-3g - like app is included in the distro will do the job of recognizing my 3 internal drives and one external USB drive. Anyone who wants to suggest that a long walk off a short piere would be more fun, feel free to input! Thanks again and, Sayonara.

---

### Post by bumanie on 2008-02-04
I am glad you have got a workable, if not perfect, conclusion.

---

