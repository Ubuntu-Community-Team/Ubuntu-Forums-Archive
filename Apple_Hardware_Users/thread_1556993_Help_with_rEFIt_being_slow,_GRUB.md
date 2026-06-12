---
title: "Help with rEFIt being slow, GRUB"
date: 2010-08-20
forum: Apple Hardware Users
---

### Post by kennethsime on 2010-08-20
Hi everyone,

I'm currently dual-booting snow leopard (10.6.4) and lucid lynx (10.04) on my macbook pro (5,5) and trying to figure out two things.

The first is that rEFIt is extremely slow when booting. It takes upwards of 10-20 seconds before the rEFIt menu comes up. I do not think this is right, and certainly puts a damper on my bootime (which is otherwise impeccably fast in both snow leopard and lucid lynx). I'm thinking of just removing rEFIt; is that ok? I just trie rebooting and holding down alt/option, and that worked to boot Ubuntu just fine (and a million times faster than waiting for rEFIt to load). Is it okay then to just get rid of rEFIt? How can I uninstall it properly so that my Mac partition boots normally (and quickly again!) unless I hold down my option key?

My second question is on my Ubuntu partition, I still have the GRUB bootloader. While I realize this is a good idea, I previously shortened the automatic boot time to 1-2 seconds so that I would sort of "skip GRUB." An unexpected consequence of this turned out to be that the Ubuntu logo splash screen appears skewed and pixelated (a shame!) for the brief moments it's on my screen. I would like to restore the splash screen to its former glory, and am willing to go back to the normal 10-seconds or whatever it is for automatic boot if that would help, but I can't recall even how to do that, or find the post that supplied the code before. Should I / could I just reinstall GRUB? Is there an easier way to do this?

**Edit:** After more googling, I stumbled across this: [http://www.howtogeek.com/howto/ubuntu/change-the-grub-menu-timeout-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/change-the-grub-menu-timeout-on-ubuntu/) which mentions that the GRUB boot menu was apparently at one point an option thing only viewed upon pressing escape from the login menu? Am I getting that right (I've only been using Ubuntu since 8.04)? Can I go back to that?

**Edit:** I loaded rEFIt's partition tool (gptsync) and it informed me I had an invalid MBR, and my partition tables were overlapping. This could be part of the problem as well, if the system is scrambling to figure out what to do. Interestingly, if I hold down the option key at startup, then select my mac partition (labelled rEFIt), rEFIt will load almost immediately. This could also seems to support this theory.

Thanks very much in advance to all of you, I really appreciate it.

---

### Post by dngfng on 2010-08-20
Hi,
I can only tell you where to change the grub timeout:

```

sudo gedit /boot/grub/grub.cfg

```

Further down in the file you will find the timeout parameter just change that to what ever you like.

timeout=10

---

### Post by kennethsime on 2010-08-20
Thank you! That helped. I also updated grub, as per the grub.cfg file's reccomendation. This definitely helped Grub not freak out, but the Ubuntu logo is still all distorted. Sad :(

---

### Post by kennethsime on 2010-08-20
Output of fdisk -l is as follows:

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000256e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   *          26       24341   195312500   af  HFS / HFS+
/dev/sda3               1       24341   195518463+  ee  GPT
/dev/sda4           24341       30258    47524864   83  Linux

Partition table entries are not in disk order
```

Can someone help me figure out what this means?

Also, I attached a screenshot of Disk Utility showing the 1.00 MiB partition, which fdisk -l doesn't seem to show...

---

### Post by kennethsime on 2010-08-22
Could the time delay possibly be solved by "blessing" the mac/rEFIt partition, so that it boots immediately? Do you need the OSX install dvds to "bless" a partition?

From OSX, this is what I get in terminal:

```

KennethMac:~ kenneth$ sudo bless --device /dev/sda2 --setBoot --verbose
Password:
EFI found at IODeviceTree:/efi
Could not get IOService for sda2

```

---

### Post by Taoye on 2010-08-22
You can bless from the install DVD, or from a running OS X.

Is rEFIt installed on the system EFI partition, or the OS X partition? Either way, if you know what file is the rEFIt efi image you can bless that specific file. For example, I'm single-booting into Linux, so I used this command to get grub-efi to boot directly:

bless --folder "/Volumes/EFI/grub" --file "/Volumes/EFI/grub/grub.efi" --setBoot

---

### Post by kennethsime on 2010-08-22
rEFIt is installed on the OSX partition. What is the benefit to installing it on the EFI partition? I could re-install to EFI if it would help.

So, what would be the address for my refit file be, if it's installed like this:

Macintosh HD > efi/refit/refit.efi

Would it be:
```

sda2/efi/refit/refit.efi

```

Making the command?:
```

bless --folder /efi/refit --file /efi/refit/refit.efi --setBoot

```

I tried this and while terminal didn't return any errors, it also did not noticeably enhance boot speed. Hmm...

Is that correct?

---

### Post by srs5694 on 2010-08-23
First, when cutting-and-pasting something from a text-mode console or other monospaced display, please enclose it in a [noparse]```

```[/noparse] block, not a [noparse]> [/noparse] block. The former will preserve columnar output and will be quotable; the latter will not. I had to manually cut-and-paste the critical stuff below, and clean up the columns for legibility.

> **kennethsime said:**
> Output of fdisk -l is as follows:

```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000256e

Device    Boot   Start    End      Blocks  Id System
/dev/sda1            1     26      204819+ ee GPT
/dev/sda2   *       26  24341   195312500  af HFS / HFS+
/dev/sda3            1  24341   195518463+ ee GPT
/dev/sda4        24341  30258    47524864  83 Linux

Partition table entries are not in disk order 

```

Can someone help me figure out what this means?

This means that your partition table is messed up. Before you do anything else, you should fix it. You've got a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) configuration there, and those are ugly and dangerous at the best of times. Worse, you've got a *broken* hybrid MBR: You've got two 0xEE ("GPT") partitions, one of which (/dev/sda3) overlaps other partitions. Both of these issues are bad.

At the very least, you should use Linux fdisk to delete /dev/sda3. Chances are the system will begin to work better at this point.

Note that Linux does *not* require a hybrid MBR to boot on a Mac, so use of a hybrid MBR is just asking for trouble for no reason. Thus, you'd probably be better off eliminating the hybrid MBR entirely and creating a conventional protective MBR. You can do this with my [GPT fdisk](http://www.rodsbooks.com/gdisk/) in either Linux or OS X. Launch the program on the disk (as in "sudo gdisk /dev/sda" in Linux or "sudo gdisk /dev/disk0" in OS X), enter the experts' menu by typing "x", use the "n" option to create a fresh protective MBR, and then type "w" to save the changes. Verify the changes by using Linux fdisk; you should see a single type-0xEE ("GPT") partition that spans the entire disk, with no other MBR partitions present. Your GPT partitions will be unaffected by this change.

---

### Post by kennethsime on 2010-08-23
Used GParted to delete /sda3, now fdisk -l reads:

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000256e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   *          26       24341   195312500   af  HFS / HFS+
/dev/sda4           24341       30258    47524864   83  Linux

```

Alright, so it no longer says that partition table entries are not in disk order, does that mean that they do not overlap anymore? Startup time is unaffected at 22 seconds until rEFIt will show up.

In setting up the dual-boot, I mostly just followed the rEFIt tutorial, which mentioned using apple's boot camp to set up a "windows partition" which was then wiped and formatted as ext4 for Ubuntu. I'm not very experienced in partitioning, this is the first time I've dual-booted and that it's on an EFI disk is complicating it for me. Could I just get rid of MBR and have linux run on a GPT partition? My ideal would be to have the whole system use EFI & GPT natively like the mac originally did. Ubuntu will run on on a GPT partition, yes? I'm looking at your article here: [http://www.rodsbooks.com/gdisk/mbr2gpt.html]("http://www.rodsbooks.com/gdisk/mbr2gpt.html") If I'm reading it right, it would be possible to use gdisk to convert the mbr partitions back to gpt?

---

### Post by srs5694 on 2010-08-23
The message about the partition entries not being in disk order is harmless in and of itself, and it has nothing to do with overlapping partitions. The overlap in your original layout could be seen by the start and end positions of the partitions -- /dev/sda3 ran from cylinder 1 to cylinder 24341, but at least two other partitions (1 and 3) also occupied the same space. That's like two cars trying to occupy the same parking space: Trouble.

Incidentally, using GParted to fix this problem was risky. GParted can handle both MBR disks and GPT disks, but the last I checked, it wasn't very aware of hybrid MBR disks. Thus, there's no telling whether it would change the GPT or the MBR data. It appears you lucked out, but if anybody else reads this, I must emphasize: Use *Linux fdisk* to delete extra 0xEE partitions! Because Linux fdisk doesn't understand GPT, you can be sure it will operate on the MBR data, not the GPT data.

---

### Post by kennethsime on 2010-08-24
> **srs5694 said:**
> 
Note that Linux does *not* require a hybrid MBR to boot on a Mac, so use of a hybrid MBR is just asking for trouble for no reason. Thus, you'd probably be better off eliminating the hybrid MBR entirely and creating a conventional protective MBR. You can do this with my [GPT fdisk]("http://www.rodsbooks.com/gdisk/") in either Linux or OS X. Launch the program on the disk (as in "sudo gdisk /dev/sda" in Linux or "sudo gdisk /dev/disk0" in OS X), enter the experts' menu by typing "x", use the "n" option to create a fresh protective MBR, and then type "w" to save the changes. Verify the changes by using Linux fdisk; you should see a single type-0xEE ("GPT") partition that spans the entire disk, with no other MBR partitions present. Your GPT partitions will be unaffected by this change.

Ok, so this solved the problem as far as rEFIt not coming up. It now shows up within three seconds of startup. Interestingly, if I hold down alt-option, only the rEFIt drive shows up. If I select Ubuntu from rEFIt, I get a no bootable deviice message. I suspect I will be re-installing Ubuntu, but I don't think that this is the problem... What do I now have to do to make Ubuntu bootable again?

---

### Post by srs5694 on 2010-08-24
I'm afraid I can't help you much from this point, since I'm not familiar with rEFIt. With any luck somebody else will respond.

---

### Post by kennethsime on 2010-08-24
> **srs5694 said:**
> I'm afraid I can't help you much from this point, since I'm not familiar with rEFIt. With any luck somebody else will respond.

I believe the problem is not rEFIt-based. rEFIt I believe hands off the computer to the linux partition and then runs GRUB, normally. Now, I get a "No bootable device found, insert bootable device," or something very close to this, and it's definitely linux displaying the message. I tried reinstalling and updating GRUB on the linux partition, but this did not help.

So I guess I go about troubleshooting now...

---

### Post by kennethsime on 2010-08-24
Problem solved! The problem as that Ubuntu was reading the "protective" MBR partition table, which says that there are no linux devices present, since it says there's just one "GPT" partition. I simply started rEFIt, used the partitioning tool (GPTSYNC) to sync the partition tables. Now Ubuntu reads the MBR table, which is synced properly with the MBR table. rEFIt now shows up within seconds, and Ubuntu boots right up.

Now, to get to work on the nvidia drivers, which are being quite annoying right now...

---

### Post by srs5694 on 2010-08-25
Ubuntu normally is happy with GPT. I suspect it was GRUB that was reading the MBR table, and chances are force-loading the part_gpt.mod module would fix the problem in a cleaner way. If it works for you now, though, you might as well leave it. At worst, it'll break later; but if you try to change the configuration, it might break again now.

I curse Microsoft for not supporting GPT better, and I curse Apple for using the hybrid MBR abomination to get around Microsoft's lack of GPT support. Combined, these two decisions have cause *a lot* of problems!

---

### Post by kennethsime on 2010-08-25
> **srs5694 said:**
> Ubuntu normally is happy with GPT. I suspect it was GRUB that was reading the MBR table, and chances are force-loading the part_gpt.mod module would fix the problem in a cleaner way. If it works for you now, though, you might as well leave it. At worst, it'll break later; but if you try to change the configuration, it might break again now.

I curse Microsoft for not supporting GPT better, and I curse Apple for using the hybrid MBR abomination to get around Microsoft's lack of GPT support. Combined, these two decisions have cause *a lot* of problems!

Could you explain the benefits of doing that and how?

Currently, the MBR basically exists to communicate the GPT partition to GRUB, and any OS that can't read GPT, correct? force-loading part_gpt.mod (I don't know what this is) would in theory make GRUB be able to read the GPT table and use that instead?

---

### Post by srs5694 on 2010-08-25
Yes, GRUB 2 is GPT-aware. (I've used it on GPT-only installations, albeit on BIOS-based systems, not EFI-based Macs.) For whatever reason, it's not working that way on your system -- I'm speculating this is because the necessary GPT module isn't being loaded. Actually, it now also occurs to me that you might need a [BIOS Boot Partition,](http://grub.enbug.org/BIOS_Boot_Partition) although I'm not sure if this is really necessary on an EFI-based Mac. I can't provide more explicit instructions on inserting this module in GRUB since I've never had to do it. I suggest you try Googling "grub insmod gpt" or something similar to find relevant information.

---

### Post by chillyperson23 on 2010-09-06
I used gptsync and an alternate install CD to fix that on mine. 

**backup whatever you need just in case. **


install gparted and delete the small bios_grub partition. 

then run
"sudo gptsync /dev/sda" or whatever your drive is. 

Then go into OS X and run in terminal,
"sudo gptsync /dev/disk0"
then reboot into the alternate CD and choose "rescue broken system"
Go through all the stuff and choose your root filesystem. (mine was /dev/sda4)
then run

"grub-install /dev/sda --force"  and
"update-grub"


It should be fixed and rEFIt should work much faster. If it isnt, try reblessing rEFIt.

Hope this helps you. =]

---

### Post by kennethsime on 2010-09-08
> **chillyperson23 said:**
> I used gptsync and an alternate install CD to fix that on mine. 

**backup whatever you need just in case. **


install gparted and delete the small bios_grub partition. 

then run
"sudo gptsync /dev/sda" or whatever your drive is. 

Then go into OS X and run in terminal,
"sudo gptsync /dev/disk0"
then reboot into the alternate CD and choose "rescue broken system"
Go through all the stuff and choose your root filesystem. (mine was /dev/sda4)
then run

"grub-install /dev/sda --force"  and
"update-grub"


It should be fixed and rEFIt should work much faster. If it isnt, try reblessing rEFIt.

Hope this helps you. =]

I'm sorry, but this thread has gotten very complicated. Which problem did you fix by doing this?

---

### Post by ipina on 2011-03-12
In fact, it seems this is becoming a complicated thread. I got the problem of booting slow with Mac OS X and Ubuntu server 10.04 on an iMac 21" with Intel processor. I had an overlapping issue as well, which I solved following directions as indicated at the beggining of this thread. And I solved the rEFIt slow problem simply by repairing permissions on the MacInthosh volume. Hope this helps someone.

---

### Post by joopbraak on 2011-04-18
[https://bugs.launchpad.net/ubuntu/+source/parted/+bug/757201](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/757201)

---

