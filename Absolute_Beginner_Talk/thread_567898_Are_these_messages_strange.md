---
title: "Are these messages strange?"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by persofi on 2007-10-05
Hey folks,
I do not know too much about Ubuntu so sorry if this is trivial stuff. There are some things I cant really understand and I would like to know if they are nothing to worry about. I keep alot of important data on my computer...

So:
I'm running Ubuntu Feisty Fawn with all updates on a Acer Aspire 5612 WLMi laptop. I also still have Windows XP installed.

1) In the boot menu, where I choose between loading up Ubuntu or Windows XP it says:

"Ubuntu, Kernel 2.6.20-16-generic"
"Ubuntu, Kernel 2.6.20-16-generic (recovery mode)"
"Ubuntu, Kernel 2.6.20-16-generic"
"Ubuntu, Kernel 2.6.20-16-generic (revocery mode)"
"Ubuntu, memtest 86+"

Why are the Ubuntu entries duplicates? Is this something to be concerned about? (I'm not sure if I maybe made some errors installing Ubuntu...)

2) While startup I always get some long lines with strange numbers... Unfortunately I do not know how to view the logs of the bootup procedure, otherwise I could post it here. Anyways the last entry is always something like

506: bf/59, 507: cc/53
Not automatically fixing this

I also get the message:
"There are differences between boot sector and its backup.
Not automatically fixing this"

---

### Post by aquavitae on 2007-10-05
1)  You may have two systems installed, or it might just be duplicate entries.  Can you post the contents of the file /boot/grub/menu.lst?

2)  Sounds like a problem on your hard drive.  You can find the logs under /var/log.  The system log is /var/log/messages, and IIRC its is the one that will show this.  See if you can work out which partition has the problem - if its a windows one try running scandisk in win.  If its a linux one, boot off the live cd, open a terminal and run 'sudo fsck /dev/hda1'.  Replace /dev/hda1 with the correct device.

Does this help - or do you need more detail?

---

### Post by justinmiller87 on 2007-10-05
Mine when I initially started only had XP, the Memtest, Ubuntu, and Ubuntu Recovery mode. After my system did a security update it then had two in there, so that's probably what happened. I just pick the most recent version. But I see yours is slightly different because you have two of the same version. Mine are two different, the original off the 7.04 DVD, and the new.

---

### Post by philinux on 2007-10-05
Good idea to back up your home folder and move it to a separate partition too.

---

### Post by aquavitae on 2007-10-05
> **justinmiller87 said:**
> Mine when I initially started only had XP, the Memtest, Ubuntu, and Ubuntu Recovery mode. After my system did a security update it then had two in there, so that's probably what happened. I just pick the most recent version. But I see yours is slightly different because you have two of the same version. Mine are two different, the original off the 7.04 DVD, and the new.Yes, this happens when you update the kernel (the 2.6.20-16 refers to the kernel version)  It puts them there is case there's a problem with the new kernel - you can easily go and boot off the last one that worked.  I occasionally go in and delete the old ones to keep it tidy.  But two with the same version number looks like something different - unless something weird happened with the updates...

---

### Post by persofi on 2007-10-05
Thx for your responses!

1) I opened the /boot/grub/menu.lst file. Here are the parts I think are relevant

"## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0788140d-5b10-4f92-a2e7-a6952d3f70ef ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0788140d-5b10-4f92-a2e7-a6952d3f70ef ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0788140d-5b10-4f92-a2e7-a6952d3f70ef ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0788140d-5b10-4f92-a2e7-a6952d3f70ef ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST"

I have no real idea what it means, but my intuitive feeling is that this shows they are just duplicate entries and not two seperate systems, correct?

2) Strangely I do not find my messages in these logs. Is there a function under Ubuntu which searches every document file on the hard drive for certain phrases or crazy stuff like "^[[6~^[[6" ?

---

### Post by persofi on 2007-10-05
I actually noticed that I misread and I have two different entries -16-generic and -15-generic... So problem 1 seems fixed already :)

---

### Post by Lord Illidan on 2007-10-05
>  title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0788140d-5b10-4f92-a2e7-a6952d3f70ef ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0788140d-5b10-4f92-a2e7-a6952d3f70ef ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0788140d-5b10-4f92-a2e7-a6952d3f70ef ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0788140d-5b10-4f92-a2e7-a6952d3f70ef ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

As far as I can see, they're not the same, just different kernel entries. You can try and remove them from synaptic. However, it's not that important, although you can free a good 80 mbs.

---

### Post by aquavitae on 2007-10-05
It might not be logging all the detail - I think you can specify how much it should log but if you can I don't know how.  I'd suggest you just boot off the livecd and fsck all your partitions.  You won't have that many...  You can also get a list of them by typing 'fdisk -l'.

---

### Post by sailor2001 on 2007-10-05
you can remove the past kernel through synaptics:  linux-image  however it has always been recommended to keep the immediate past kernel for a "fall back" in case something messes up with the newest kernel

---

### Post by persofi on 2007-10-05
OK so I found the partition with the errors and it's the Windows partition... Scandisk in Windows couldnt fix the error so I did the fsck thing with the live cd. It asked me:

"fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  67:0e/a8, 68:18/ef, 69:0d/0c, 70:32/54
1) Copy original to backup
2) Copy backup to original
3) No action"

There is nothing important on the windows partition so either choice doesnt really matter to me, as long as it doesnt affect Ubuntu. However I have no idea what boot sector/backup means in this context... I suppose action 1) makes more sense?

---

### Post by aquavitae on 2007-10-05
If won't affect ubuntu.  Option 1 is probably best, based on the assumption that the disk is working fine with the boot sector as it is now, so keep it and change the backup.  

As for an explanation - I think this is how it works:  The boot sector is the section right at the start of the disk or partition.  For fat partition, it most notably contains the File Allocation Tables, of which there are usually 2 copies - an original and a backup.  What the error means is that the original and backup do not match, and that one of them contains inaccurate information about what is on the drive.  In order to recify this, you need to select which copy is correct.  As I said, if its all running fine now, its probably the backup thats corrupt.  I could be wrong!  Btw, is there any particular reason you have a FAT partition?  Its not a nice file system, and now that linux can write to ntfs there's no real need for it.

---

### Post by persofi on 2007-10-05
Why do I have a FAT partition? I dont really know. Maybe it autoconverted when I installed Potgre-SQL but I doubt it.

What I dont get: When I do fdisk -l I get:
"/dev/sda1               1         509     4088511   12  Compaq diagnostics
/dev/sda2   *         510        5087    36772785    c  W95 FAT32 (LBA)
/dev/sda3            5088        9585    36130185   83  Linux
/dev/sda4            9586        9729     1156680   82  Linux swap / Solaris"

sda1 is probably some Phoenix Recovery thing the Acer laptop has preinstalled... With fsck only sda2 is making problems. But if I do option 1 it says:

"fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  67:0e/a8, 68:18/ef, 69:0d/0c, 70:32/54
1) Copy original to backup
2) Copy backup to original
3) No action
? 1
Leaving file system unchanged.
/dev/sda2: 50541 files, 372958/1148868 clusters"

And when I restart my system I see that nothing seems to have changed, getting the same messages on startup...

---

### Post by aquavitae on 2007-10-05
Thats weird.  And scandisk doesn't fix it?  Did you remember sudo in front of fsck? The only other thing I can suggest is to upgrade the file system to ntfs in windows.  Can't remember how though - I think its ubder computer administration or something - so long since I did it!  If you don't need FAT it would probably be a good move anyway, and it might sort the problem out at the same time.

---

