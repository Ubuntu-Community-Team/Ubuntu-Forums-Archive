---
title: "Dual booting Lion and Oneiric"
date: 2011-09-24
forum: Apple Hardware Users
---

### Post by Lars Noodén on 2011-09-24
Something has changed in Lion that it does not like to dual boot with Linux any more.  rEFIt seems to work but after that, the OS won't load.  

Are their instructions on how to dual boot with the latest in Lion?

---

### Post by dfacto on 2011-09-25
I've already addressed [this issue]("http://ubuntuforums.org/showpost.php?p=11215214&postcount=185") in the Macbook Air 4 thread.  The long and short of it is that libparted does something to the hybrid MBR that gptsync doesn't know how to fix.  Therefore you have to use gdisk and correct the hybrid MBR manually.  The [linked post]("http://ubuntuforums.org/showpost.php?p=11215214&postcount=185") gives detailed instructions how to do this.  The [subsequent post]("http://ubuntuforums.org/showpost.php?p=11215380&postcount=186") lists all of my tables for reference purposes.

---

### Post by Lars Noodén on 2011-09-25
Thanks.  I tried the instructions linked there but had no visible effect on the booting: I get a blank screen with a blinking underscore cursor in the upper left corner when I choose the Linux option.  

I will try reinstalling an older version of Ubuntu later this week.

---

### Post by dfacto on 2011-09-25
Do you get an error for gptsync?  I don't think reinstalling is the quickest way to resolve this.  Either the hMBR is bad, you need to bless the partition, you need to gptsync, or grub needs to be reinstalled.  Try these first--each is an easy thing to try. And if you've already resigned yourself to re-install, you have nothing to lose.

---

### Post by Lars Noodén on 2011-09-25
In rEFIt when I try to sync the tables, it says:

Status: Tables are synchronized, no need to sync.

There is otherwise no error message, even when trying to boot.  As for re-installing grub, how can that be done from OS X or the rescue CD?  I have followed the steps in the link above even including the bless.

---

### Post by dfacto on 2011-09-25
There are two popular ways to reinstall grub. I personally use method 1 but method 2 is arguably more appropriate. I like method 1 because it is also the first step for fixing almost every imaginable problem in Linux (not just Ubuntu).  If one method doesn't work, try the other.

First, determine the partition which contains /boot (ie the partition that contains grub).  You can try "sudo fdisk -l" or "df" or "sudo gdisk /dev/sda" or other things.  I can always get by with "sudo fdisk -l".

I will assume that your /boot is on /dev/sda4 (yours may be different; be sure!).

Method 1:

```

# boot from LiveCD, open terminal, enter:
sudo mount /dev/sda4    /mnt
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt

# do the fixing:
sudo grub-install /dev/sda4

# clean-up:
exit
sudo umount /mnt/{sys,proc,dev,}
# last comma is not a typo

```

-OR-

Method 2:
```

# boot from LiveCD, open terminal, enter:
sudo mount /dev/sda4 /mnt

# do the fixing:
sudo grub-install --root-directory=/mnt/ /dev/sda4
# if you get errors, try:
#sudo grub-install --recheck --root-directory=/mnt/ /dev/sda4
# then try the grub-install again

# clean-up
sudo umount /mnt

```

Note that in both methods, I set the install location as /dev/sda4 (which is a file-system).  Normally you would install grub to /dev/sda (the whole partition) but since this is Mactel, you typically want the MBR to be on a file-system not the whole device.

---

### Post by dfacto on 2011-09-25
Also, even if gptsync doesn't complain, you may STILL want to try the gdisk rebuild hybrid MBR steps I linked you.  Sometimes gptsync puts the wrong partitions in the hMBR.  I believe I had this too, and as I said, gdisk fixed it for me.  In order I would try:

1) gptsync
2) gdisk
3) grub-install

And you could probably do a bless after each step.

---

### Post by Lars Noodén on 2011-09-26
I get the following error when trying either method 1 or method 2:

```

# mount /dev/sda4 /mnt
# grub-install --root-directory=/mnt /dev/sda4
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.

```

And this following the second option in method 2:

```

# sudo grub-install --recheck --root-directory=/mnt/ /dev/sda4
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.

```

---

### Post by dfacto on 2011-09-26
Yes, I now remember seeing this too. As far as the scary warnings, we can ignore these.  We know this is what we want.

I think at this point what I did was:
```

# in the chroot of above
sudo aptitude purge grub-pc
sudo aptitude install grub-pc

```
Then make sure to install to sda4.  I think you can ALSO install to sda if it makes you feel more comfortable (I'll bet that's already selected).  But I unselected sda and selected only sda4.

You see, the reason grub is giving warnings is because its very weird to install the boot info to a file-system and its even weirder that the disk "doesn't have partition info".  We're basically doing weird things because apple's "legacy mode" booting *IS WEIRD*.

It works like this.  Apple uses UEFI to boot and GPT to organize the paritition information.  Grub expects to see BIOS and BIOS doesn't support GPT (so neither does grub).  Apple fakes BIOS, in part by creating the "Hybrid MBR" (hMBR). The hMBR is only ever relevant immediately following your choice at refit--its used by BIOS-expecting-OS's so they know where the boot data is located. (Note: BIOS can only have four fs per partition--that's why you used to have to use logical partitions and why hMBR limits you to four.)  This is why grub thinks there is "no parititon"--it can't understand the GPT info.  Basically we can put the grub image anywhere we want--we'll be telling the hMBR to look in sda4 for the boot image.  And sda4 makes the most sense since its a dual-boot and we'd like linux and macos each self-contained.

Finally I should say that the simple fix is just tack on the --force flag to the grub commands.  However, I purged then reinstalled and this did the trick (sorry I didn't remember sooner!).

---

### Post by Lars Noodén on 2011-09-26
> **dfacto said:**
> 
Finally I should say that the simple fix is just tack on the --force flag to the grub commands. 


That still gives the same errors with grub-install.  When trying to boot to linux, the error presented is just a blank screen with the text "Missing operating system"

---

### Post by dfacto on 2011-09-26
Tried the purge/install sequence? And after that you should gptsync (and make sure the sync'ed table makes sense!).  If there is a sync problem or the table doesn't look right (see my table linked from my first post) then you need to gdisk a new hMBR.

---

### Post by Lars Noodén on 2011-09-26
> **dfacto said:**
> Tried the purge/install sequence? And after that you should gptsync (and make sure the sync'ed table makes sense!).  If there is a sync problem or the table doesn't look right (see my table linked from my first post) then you need to gdisk a new hMBR.

I tried purging/installing grub but it still gives the "Missing operating system" error.  Running gptsync does not work, it gives the error "Error: Not Found returned from gptsync.efi"  What other options are there?

---

### Post by dfacto on 2011-09-26
Yes--this is expected. It means you're nearly there. Follow the gdisk steps from my first post.

---

### Post by Lars Noodén on 2011-09-26
> **dfacto said:**
>  Follow the gdisk steps from my first post.
Can you give some more detail there?  When I try it, the partition table scan shows MBR only -- but a blank one.  I'm not sure what to do with gdisk.

---

### Post by dfacto on 2011-09-26
Sorry I can't give much more detail without a more specific question--its already a complete walk-through. Just [follow the steps]("http://ubuntuforums.org/showpost.php?p=11215214&postcount=185").

o	print protective MBR data
p	print the partition table

It doesn't matter that your current MBR is empty--this is what we are rebuilding!  You only need information from the GPT (the 'p').

---

### Post by Lars Noodén on 2011-09-26
> **dfacto said:**
> Sorry I can't give much more detail without a more specific question--its already a complete walk-through. Just [follow the steps]("http://ubuntuforums.org/showpost.php?p=11215214&postcount=185").

o	print protective MBR data
p	print the partition table

It doesn't matter that your current MBR is empty--this is what we are rebuilding!  You only need information from the GPT (the 'p').

OK it boots now.  Thanks.  Now I have to figure out what I did so I can do it to my production machine.

---

### Post by dfacto on 2011-09-26
So it works because you followed my advice or because you did something different?  I'd like to know for future reference so please keep me updated.

---

### Post by Lars Noodén on 2011-09-26
I followed your advice but repeated some steps and did the gdisk thing twice, once at the start and once at the end.  AFAIK it was only at the end that it had effect.

Edit: I'm still trying to duplicate the results on my production system with no effect yet.  I'll keep trying a few more times.

---

### Post by dfacto on 2011-09-26
You mean to say you did gdisk after purge/install grub-pc? If everything works, mark this thread solved so others know that the solution exists.

---

### Post by Lars Noodén on 2011-09-26
> **dfacto said:**
> You mean to say you did gdisk after purge/install grub-pc? If everything works, mark this thread solved so others know that the solution exists.

Yes. I did gdisk after the purge/install of grub-pc.

I've not been able to duplicate the results yet on my production machine.

---

### Post by srs5694 on 2011-09-26
> **dfacto said:**
> It works like this.  Apple uses UEFI to boot and GPT to organize the paritition information.  Grub expects to see BIOS and BIOS doesn't support GPT (so neither does grub).

That's not quite completely correct. Apple uses EFI 1.x (not UEFI, which is EFI 2.x) to boot. Macs do use GPT, though. GRUB 2 (which Ubuntu uses) *does* support GPT, but it works best when a [BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition) is present, which most of the Ubuntu-on-Mac instructions I've seen don't create. I'm not positive that this is a source of problems, but it might be.

BIOS supports neither GPT nor the MBR partitioning system; it's too stupid for any of that. Under BIOS, it's boot loaders and OSes that provide the partition table support.

> Apple fakes BIOS, in part by creating the "Hybrid MBR" (hMBR). The hMBR is only ever relevant immediately following your choice at refit--its used by BIOS-expecting-OS's so they know where the boot data is located.

Correct.

> (Note: BIOS can only have four fs per partition--that's why you used to have to use logical partitions and why hMBR limits you to four.)

I think you mean "four partitions per disk," not "four fs per partition." Hybrid MBRs are actually limited to *three useful* partitions, since one of the four partitions *must* be a type-0xEE partition that's used to flag the disk as a GPT disk for GPT-capable OSes.

> This is why grub thinks there is "no parititon"--it can't understand the GPT info.

I don't know what causes a "no partition" error in GRUB, but it's certainly not the use of GPT. I use GPT, with no hybrid MBR, on several BIOS-based PCs with GRUB 2 and the combination works fine.

> Finally I should say that the simple fix is just tack on the --force flag to the grub commands.  However, I purged then reinstalled and this did the trick (sorry I didn't remember sooner!).

Personally, I prefer doing Linux/OS X dual boots using a conventional (non-hybrid) GPT and EFI mode. I've got [a Web page](http://www.rodsbooks.com/ubuntu-efi/index.html) that describes how I did this on my (somewhat elderly 32-bit) Mac Mini. Unfortunately, model-to-model differences mean that the approach I used might not work on all systems. Also, I originally wrote that page several months ago. I've learned a lot since then, and Ubuntu's changed since then, so I'd probably do it differently today. For instance, I've since discovered that Fedora's patched GRUB Legacy is more reliable on my Mac Mini than is GRUB 2.

If you're interested in learning more, I've recently put up [a Web page on EFI boot loaders.](http://www.rodsbooks.com/efi-bootloaders/index.html) You could use that information to install a Linux-capable boot loader in your Mac's ESP. I recommend Fedora's heavily-patched GRUB Legacy, but ELILO might work on some models. I don't recommend trying this on a system that boots and works well unless you're very curious and are willing to risk losing a working system when you experiment with it. Installing an EFI-capable boot loader to use in conjunction with rEFIt might be a better solution than mucking with a BIOS version of GRUB if your system isn't booting in Linux at all, though.

---

### Post by dfacto on 2011-09-26
Thanks for correcting me srs5694! :)

One source of confusion might be terminology--I was referring to the package grub-pc and (implicitly) the package grub-efi.  Of course both are grub but obviously facilitate different boot styles.

Still though, certainly I should be more careful in explaining things! ;)

It would be nice to determine what exactly happens during the oneiric install that causes the problem. Lars Noodén described the exact same problems I had.  What's particularly strange to me is that reinstalling grub-pc and rebuilding the hMBR fixes the problem.  This strange because I don't see any reason that the original grub-pc install should cause a problem.

Do you think that reinstalling grub-pc from the chroot forces the designated partition to become the BIOS boot partition?  Is there an easier way to do this, say immediately after installing Oneiric while still in the Live session?

Despite the benefits of EFI booting, its still important to have legacy mode working--particularly for people on the new Macbook Airs.  The current hacks to get video working only seem to work for legacy mode.

---

### Post by srs5694 on 2011-09-26
> **dfacto said:**
> Thanks for correcting me srs5694! :)

One source of confusion might be terminology--I was referring to the package grub-pc and (implicitly) the package grub-efi.  Of course both are grub but obviously facilitate different boot styles.

True, they use different boot styles. It's important to realize, though, that grub-pc supports GPT; GPT support is *not* limited to the grub-efi version of GRUB. I'm not sure if you could use a pure-GPT configuration and still BIOS boot with a Mac, though. My understanding is that a hybrid (or conventional) MBR is required to get the Mac's EFI to activate its BIOS compatibility module, but maybe there's some other way to do it with a pure-GPT setup. (Maybe rEFIt could do it in the absence of a hybrid MBR, for instance, but that's just speculation on my part.)

> Do you think that reinstalling grub-pc from the chroot forces the designated partition to become the BIOS boot partition?  Is there an easier way to do this, say immediately after installing Oneiric while still in the Live session?

Given that most of the install procedures I've seen don't set up a BIOS Boot Partition, I'd give a tentative "no" answer to the first question. Note that a BIOS Boot Partition has a very specific purpose, and you should *not* set a regular Linux or OS X partition as a BIOS Boot Partition. Doing so will cause damage when you next install GRUB! So if you're thinking of experimenting with BIOS Boot Partitions, *do not* do so on partitions that contain data; instead, create a new partition and flag it as a BIOS Boot Partition ("bios_grub flag" set in libparted-based tools, or type code of 0xEF02 in GPT fdisk tools).

My suggestion is to create a BIOS Boot Partition when installing Ubuntu and to install GRUB to the MBR. Perhaps that would bypass whatever the problem is. GRUB should install itself to the MBR, to the BIOS Boot Partition, and to its normal locations in /boot/grub when you do this. Without a BIOS Boot Partition, GRUB is likely to have to use block lists, which are unreliable.

> Despite the benefits of EFI booting, its still important to have legacy mode working--particularly for people on the new Macbook Airs.  The current hacks to get video working only seem to work for legacy mode.

I can't speak to the issue of video hacks on MacBook Airs, either.

---

### Post by Lars Noodén on 2011-09-27
Maybe this should be in a new thread, 
I've tried to duplicate the results on a second machine but no luck.

I've tried:

1. in the Linux partition while using the rescue CD:
sudo apt-get purge grub-pc
sudo apt-get install grub-pc

2. while in OS X:
sudo gdisk /dev/disk0
sudo bless --device /dev/disk0s4 --setBoot --legacy --verbose

Not able to boot into linux, choosing the linux image from rEFIt generates a blank screen with a blinking cursor (underscore) in the upper left corner.  That lasts indefinitely.

Trying grub-install while using the rescue CD gives the following error
```

# grub-install --recheck /dev/sda4
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.

```

What step am I missing?

---

### Post by dfacto on 2011-09-27
When purge/install did you do it after the mount/chroot steps?

---

### Post by Lars Noodén on 2011-09-27
> **dfacto said:**
> When purge/install did you do it after the mount/chroot steps?

Yes.  According to the installation, it installed grub in /dev/sda4

---

### Post by dfacto on 2011-09-27
The only other thing I can guess is that the partitions are laid out differently? Is linux truly on sda4?  Did you tailor the hybrid mbr you created in gdisk to the partition layout of this machine?  Also, you could try the --force flag as I indicated earlier.

---

### Post by Lars Noodén on 2011-09-27
> **dfacto said:**
> The only other thing I can guess is that the partitions are laid out differently? Is linux truly on sda4?  Did you tailor the hybrid mbr you created in gdisk to the partition layout of this machine?  Also, you could try the --force flag as I indicated earlier.

The partitions are laid out the same.  Linux is on sda4.  I did try the --force flag.  But this one behaves differently.  One clue is that rEFIt has been looking for the linux partition on partition #3 instead of #4.    I'll try a few changes.

---

### Post by dfacto on 2011-09-27
if refit's looking on the wrong partition, that would suggest to me that you have an incorrectly configured hMBR.

When I was fighting this problem some time ago, I also reinstalled refit.  Perhaps there is a more elegant way to make refit re-examine the partition tables, but its a 30sec try.

---

### Post by Lars Noodén on 2011-09-27
Re-running rEFIt got it looking at the right partition. But it still gives the blank screen with a blinking cursor, nothing else, no grub menu or anything.

---

### Post by dfacto on 2011-09-27
try the steps from before one more time.  Do the chroot grub reinstall and then rebuild the hMBR with gdisk.  I'll bet you it will work this time!

To recap, I think the best procedure is:
1) reinstall refit
2) reinstall grub
3) use gdisk to rebuild the hMBR
4) bless the linux partition if its slow to switch to grub

Obviously I'm trying to figure out a good recipe too, but I've done it once as have you, so we should be able to figure out the steps.

---

### Post by Lars Noodén on 2011-09-27
I've tried those in that order and still no dual booting.  :(

---

### Post by dfacto on 2011-09-27
> **Lars Noodén said:**
> I've tried those in that order and still no dual booting.  :(

Damn. Sorry Lars that was my last idea.  Hopefully someone more knowledgeable than me will chime in. :(

If you do happen to figure something out, please post-back detailed steps!  I am very curious what the fix will be.  (Don't forget to unmark this thread as solved!)

---

### Post by srs5694 on 2011-09-27
> **Lars Noodén said:**
> Maybe this should be in a new thread, 
I've tried to duplicate the results on a second machine but no luck.

I've tried:

1. in the Linux partition while using the rescue CD:
sudo apt-get purge grub-pc
sudo apt-get install grub-pc

2. while in OS X:
sudo gdisk /dev/disk0
sudo bless --device /dev/disk0s4 --setBoot --legacy --verbose

I want to be sure you understand that simply launching gdisk on a disk and then exiting will do nothing; you've got to type "r" followed by "h", answer a bunch of questions, and then type "w" to write your new hybrid MBR to the disk. If you were just using "sudo gdisk /dev/disk0" as shorthand for all of that, then of course you've already done this and this paragraph won't help you.

> Not able to boot into linux, choosing the linux image from rEFIt generates a blank screen with a blinking cursor (underscore) in the upper left corner.  That lasts indefinitely.

Trying grub-install while using the rescue CD gives the following error
```

# grub-install --recheck /dev/sda4
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.

```What step am I missing?

I recommend you try this:


[list=1]
[*]Launch gdisk and use it to create a [BIOS Boot Partition.](http://en.wikipedia.org/wiki/BIOS_Boot_partition) There's probably a gap of 32 KiB or more in your partition table that will serve for this purpose. If not, you might need to resize a partition by a tiny amount. In gdisk, a BIOS Boot Partition has a type code of EF02.
[*]Install GRUB *to the MBR,* as in "sudo grub-install /dev/sda", rather than to a Linux partition.
[*]Reboot and see if it works.
[/list]


If that fails, or if you prefer to try it another way, you could try installing an EFI boot loader for Linux to the MBR. I've had the best luck with [Fedora's patched GRUB Legacy](http://www.rodsbooks.com/efi-bootloaders/grub_legacy.html) on my 32-bit Mac Mini, but it's possible that ELILO or the EFI version of GRUB 2 will work better for you. If this method works, you can replace the hybrid MBR with a conventional protective MBR (unless you're also booting Windows), although you don't need to do this just to test it.

---

### Post by Lars Noodén on 2011-09-27
> **srs5694 said:**
> I want to be sure you understand that simply launching gdisk on a disk and then exiting will do nothing; you've got to type "r" followed by "h", answer a bunch of questions, and then type "w" to write your new hybrid MBR to the disk. If you were just using "sudo gdisk /dev/disk0" as shorthand for all of that, then of course you've already done this and this paragraph won't help you.


Understood.  I've done that and even set the linux partition to type 83.

I'll keep picking away at it this week.  It worked for the test machine so it should also work for the production machine, though they are different models.

---

### Post by dfacto on 2011-10-14
Did you ever get it working?

---

### Post by Lars Noodén on 2011-10-15
> **dfacto said:**
> Did you ever get it working?

On the Mini, yes.  On the Macbook Pro, no, not yet.  I'll give it another try in a few days.

---

### Post by dfacto on 2011-10-15
[http://ubuntuforums.org/showpost.php?p=11346282&postcount=429](http://ubuntuforums.org/showpost.php?p=11346282&postcount=429)

---

### Post by Lars Noodén on 2011-10-22
> **dfacto said:**
> Did you ever get it working?

I've not gotten it working on the MacBook Pro yet.  Grub-install gives the following error:

```

$ sudo grub-install /dev/sda4
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.


```

---

### Post by Lars Noodén on 2011-10-22
Ok.  I set a side time to do a fresh install from CD and now it boots as it should.  This only reinforces my opinion that Grub is voodoo.  

Anyway, thanks for the info.

---

### Post by dfacto on 2011-10-22
Glad you got it working and sorry it required a reinstall.

---

