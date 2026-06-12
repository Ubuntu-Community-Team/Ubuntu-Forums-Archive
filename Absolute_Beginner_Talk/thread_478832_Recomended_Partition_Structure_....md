---
title: "Recomended Partition Structure ..."
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by sidimaiga on 2007-06-19
hi all,

Ok, I just bought a 250 GB hard drive just for Ubuntu. 
How should I partition it?
Dual Boot with XP. 
Ubuntu HD will be sda, XP sdb.

Thanks

---

### Post by Happy_Man on 2007-06-19
See [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning) for suggestions. Ultimately, though, the decision is up to you.

---

### Post by niteshifter on 2007-06-19
Hi sidimaiga,

As Happy_Man said, it's your decision ... Read the link he gave, note this part at the end:

“You may hear people recommending a separate /boot partition or /usr partition. You can make a separate partition for just about any folder in the Ubuntu filesystem. The only down side is running out of space. If you have a 200 GB hard drive, make as many partitions as you can.”

I second that! I'm “old-school” Unix, the notion of separate partitions for the various folders is sound advice. So what and how big is the question.

Between the modern kernel and the drive's own buffering agonizing of where to put what is rather pointless so I won't say where to put what :p Just some ideas on slicing up the filesystem.

Let's deal with the swap partition size first. Opinions vary – a lot – but a middle of the road rule of thumb is somewhere between 1x and 2x the amount of RAM memory you have. For most desktop / notebook systems 2GB for swap is more than sufficient.  

Now, as to the filesystem proper:

The Minimal (Ubuntu default install)

/ and swap on two partitions . It works and many folks do this, but I don't like it. Rather like Windows in the fact that all the eggs (files) are in one basket.


The Middle-Of-The-Road approach

Separate partition for: /, /home, /tmp, /var
In this scheme we are separating out the critical (/home) and the busy (many reads and writes), prone to get large sometimes folders (/tmp and /var). 

The Extreme

Separate partitions for: /, /bin, /boot, /etc, /home,  /lib, /opt, /root,  /sbin, /tmp, /usr, /var
A place for everything ;) A bit wearisome for my taste – allocating sizes is a pain.

The Not Quite So Extreme

Separate partitions for /, /boot, /home, /root, /tmp, /var, /usr
More to my liking. Mainly because this is similar to how I did mine – add three partitions (Dell diagnostics, XP and a shared VFAT) and it is mine on a single 120GB drive.

Notice this common trait in all but the minimal: We keep /home apart from everything else. This gives your documents / data protection from rogue processes. Same goes for /boot and /root – they're protected also. If some software goes south on you (possible) or some component failure occurs (that's a when, not an if) you can still boot and commence recovery as su. /tmp and /var are kept apart because they can grow to large sizes – think burning a DVD. Or running a tool like ddrescue on a damaged DVD, /var/log files will record each and every IO error message (it can easily generate millions)

As to how big to make what, you've 200GB. Be generous to yourself.

/boot doesn't need much, even if you wish to indulge in kernel madness and build and try a bunch – 200MB is plenty big, 512MB if you're genuine kernel-crazy. Many folks allacate 50MB and rock on with that.

A reasonable size for /root is 4GB. That will be enough room to do recovery work.

For /var 4GB is plenty. Enough to handle big logs and spools.

10GB for tmp. Big enough to hold a dual-layer DVD ISO plus some.

6 to 10GB for /usr. Enough room to add applications and system documentation for a long time to come.

That leaves / and /home. After the above splits, / won't need much. I currently show 341MB used on mine. It's been larger, /opt lives there, and that's where I install applications I'm not sure I want to keep. I gave my / 8GB.

For /home ... that truly is up to you. Any other users? Going keep a bunch of music and / or videos? Then think in terms of 10's of GB.

However you may want to consider another partition with a VFAT filesystem to share with XP. I personally can't speak to the safety of the ntfs-3G suite – it's probably just fine, I just figure it's safer to render unto M$ that which is M$'s (which is what I did, a 15GB shared space).

Another thought is leave a portion of the 200GB space unallocated. You may get curious about another version of Linux and want to give it a try.

Enjoy!

---

### Post by st33med on 2007-06-19
250GBs... Man, you must a programmer or something because I rarely find myself the need for something bigger.

---

### Post by godog on 2007-07-07
Hello, I have a 250gb hard drive with ubuntu and no windows, and i want to virtualize windows just for those things i can't do with ubuntu. (I created a virtual machine from my old windows system)

Is it recommendable to create my virtual machine of windows in a separated partition? 

Shoud i give more space for swap? 

what do you recommend me?


Thanks

goDog

---

### Post by Vajra Vrtti on 2007-07-07
IMHO many partition schemes recommendations are more appropriate to servers running critical applications then for a simple desktop machine. I think you should keep it as simple as possible. Use a single partition (+swap) unless **_you_** have a reason not to do so, and not just because other people told you to do so.

I my own case, I choose to keep only my personal data on a separate partition. My reason: I can reformat the Ubuntu partition when I reinstall the system, with my data safely isolated.

---

### Post by Brian96 on 2007-07-07
> **godog said:**
> Hello, I have a 250gb hard drive with ubuntu and no windows, and i want to virtualize windows just for those things i can't do with ubuntu. (I created a virtual machine from my old windows system)

Is it recommendable to create my virtual machine of windows in a separated partition? 

Shoud i give more space for swap? 

what do you recommend me?


Thanks

goDog

Sort of in keeping with Vajra's comments, in my view it depends on what other partitions you have. If you have a separate partition for data, then you could just keep the virtual machine and disks in that partition. If you were otherwise planning on using only one partition then you could always just keep a backup of the virtual machine on an external disk. This can be easily accomplished using grsync (or just rsync if you like the CLI). It may take a few minutes to navigate to the folder that vmware defaults the install to, but once you've created the folder pair you can save it and it only takes a few seconds to back it up the next time.

I personally keep my virtual machine stuff on my data partition (which is also shared by a native Windows install--I know that doesn't apply to you). I also keep frequent backups of all that data using grsync.

---

### Post by godog on 2007-07-07
> **Brian96 said:**
> Sort of in keeping with Vajra's comments, in my view it depends on what other partitions you have. If you have a separate partition for data, then you could just keep the virtual machine and disks in that partition. If you were otherwise planning on using only one partition then you could always just keep a backup of the virtual machine on an external disk. This can be easily accomplished using grsync (or just rsync if you like the CLI). It may take a few minutes to navigate to the folder that vmware defaults the install to, but once you've created the folder pair you can save it and it only takes a few seconds to back it up the next time.

I personally keep my virtual machine stuff on my data partition (which is also shared by a native Windows install--I know that doesn't apply to you). I also keep frequent backups of all that data using grsync.


Thanks a lot Brian, right now I have my virtual machine in a 100gb ext3 partition (WinXP VM size is 70gb :-?) , I'll keep looking form better options and will have your opinion in mind.   

Does swap partition helps VM to run better?

Thanks again.

---

### Post by godog on 2007-07-07
> **Vajra Vrtti said:**
> IMHO many partition schemes recommendations are more appropriate to servers running critical applications then for a simple desktop machine. I think you should keep it as simple as possible. Use a single partition (+swap) unless **_you_** have a reason not to do so, and not just because other people told you to do so.

I my own case, I choose to keep only my personal data on a separate partition. My reason: I can reformat the Ubuntu partition when I reinstall the system, with my data safely isolated.


You'r right Vajra Vrtti, I would like to keep it as simple as possible, but may be there are some partition configurations to help Virtual Machines run better, I don't know much about virtualizations, but it must be a hard pounch for memory and cpu, isn't it? Thanks.

---

### Post by Brian96 on 2007-07-07
> **godog said:**
> Thanks a lot Brian, right now I have my virtual machine in a 100gb ext3 partition (WinXP VM size is 70gb :-?) , I'll keep looking form better options and will have your opinion in mind.   

Does swap partition helps VM to run better?

Thanks again.

70 GB? Did you manually set that? I think the default maxes out at 8 GB. Windows XP alone only took up 2-3 GB in my VM, but I stuck with 8 GB to have room for apps (though I don't plan to add very much).

I'm not sure about swap. All I know is that I got a warning when setting up my VM that if I set the RAM too high then it might use swap space (though my system seems to almost never use swap--with or without a VM running). I set mine at 512 MB and it runs about as well as my native install (which has access to a full gig). But I don't do much besides Quickbooks on it.

The only thing that I have found that makes a huge and noticeable difference is VMWare Tools. This app absolutely must be installed (from within the WinXP on the VM).

---

### Post by Omnios on 2007-07-07
As for sizes that is up to you. As for partitions I have been using a Ubuntu partition and also a documents partition working along with my XP partition. I don't care for a home partition as a lot of home stuff is not needed with a reinstall upgrade though I have just started using a Library file for stuff like pictures etc.

 Anyways I found having a documents partition works really well as I can use it in Ubuntu and also as the XP My Documents mount. Originally I used fat but it is probably better to using ext and using the windows ext program to access it. Word of advice though do not mount your / in windows as it does not enforce permissions in windows.

---

### Post by Vajra Vrtti on 2007-07-07
> may be there are some partition configurations to help Virtual Machines run better
I can't imagine why the host partition scheme could possibly affect the VM performance.
> t must be a hard pounch for memory and cpu, isn't it?
I think the host will need at lest 1GB RAM in order to run Windows properly in a 512MB VM.

---

