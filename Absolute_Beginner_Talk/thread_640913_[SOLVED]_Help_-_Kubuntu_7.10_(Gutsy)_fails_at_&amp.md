---
title: "[SOLVED] Help - Kubuntu 7.10 (Gutsy) fails at &amp;quot;install GRUB&amp;quot;"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Lorin Ricker on 2007-12-14
Initial conditions:  1) I'm a Linux/Ubuntu newbie.  2) My intention is to, ultimately, abandon Windows completely on all my PCs, replacing with (K)Ubuntu -- please, no advice to "kill all Windows", I've just got to migrate efficiently but quickly, but I've still got legacy data & apps to deal with.  3) Working with a downloaded Kubuntu v7.10 Desktop distro -- live CD boots and runs fine on my first target PC.  However, installation runs into a snag that I cannot figure out.

Target PC: older Compaq box, AMD Athlon CPU, 654,832 Kb RAM
OS: Windows 2000 Pro 5.00.2195, SP4.
Phoenix - AwardBIOS v6.00PG (AK73 Series R1.17).

```

2 Hard drives:
IDE Primary Master -- Maxtor 96147H6 (approx 60Gb)
IDE Primary Slave   -- ST340016A         (approx 40Gb)

IDE Secondary Master -- Hewlett-Packard DVD
IDE Secondary Slave   -- Compaq DVD-ROM SD-6
Drive A -- 1.44M 3.5in (floppy)
Drive B -- (none)
Video -- EGA/VGA

Partition configuration:
Device        Type    Mount point   Size     Used
/dev/hda
  /dev/hda1   ntfs    /media/hda1   21002Mb  12700Mb   # C: - where W2K lives
  /dev/hda5   ntfs    /media/hda5   36082Mb  14800Mb   # E: - where my Windows data lives
  /dev/hda6   swap                           2933Mb    # swap for Linux
/dev/hdb
  /dev/hdb1   ext3    /                      40015Mb   # Linux root, where Ubuntu installs

```

Prior to getting started with (K)Ubuntu, I was fortunate to have partitioned disks as above, and taking over hda6 and hdb1 for Linux root and swap was just lucky.  So, now on to my problem...

As mentioned above, I've booted both the Kubuntu v7.10 (Gutsy) and an older Ubuntu v7.04 distro (from "The Official Ubuntu Book") on this PC and played around with both without any problems... enough to give me the courage to click on Install.

And Install seemed to go fine, up to a point.  My first attempt, using the "Manual Partitioning" choice, got through the reformatting of hdb1 (root) and hda6 (swap) just fine, and then Install proceeded to Copy files..., Installing hardware..., etc., a-okay.

However, when we got to about 94% done, at the point where the process got to:

```

Installing GRUB boot loader...
  Running "grub-install (hd0)"...
  Detecting operating systems...

```

after about 30 seconds, I get this error-box:

```

Unable to install GRUB in (hd0)
  Executing 'grub-install (hd0)' failed.
  This is a fatal error.
         <OK>

```

Clicking the <OK> button then terminates the installation.  Apparently (and having tried the Install twice more, to understand and document the failure point), what I'm left with is:

a) Correctly formatted hdb1 (root) and hda6 (swap) partitions.
b) Kubuntu files copied from distro to hdb1, but that drive is not (yet) bootable.
c) MBR on hda1 (hd0) is unchanged, still boots Windows 2000 just fine.

Here are my questions:

1. Why does the Install fail at the "installing GRUB" point?  There are no error messages or numbers which indicated anything for diagnosis... just the error-box as quoted in full above.

2. Is GRUB installable for dual-boot with W2K?  A brief read through the GRUB entry of the O'Reilly "Linux in a Nutshell" book warns me that there are issues with dual-booting NT and W2K, but I'm too new to this to make out what to do about it, if true.  It seems to indicate that I must leave the Windows boot code alone in hda1 MBR, but add something about "chaining" to GRUB code on hdb1(???) -- but if so, how does dual-booting then work to get Kubuntu up? :confused:

3. Can I manually finish the GRUB install, assuming y'all can give me complete guidance and advice here?

4. If "Yes" to #3 above, what's left undone by the fatal termination of the Install... that is, what's left to do after the GRUB install that hasn't yet been done?

5. Alternative to 1-4 above, should I just try to install Ubuntu v7.04, or would I encounter exactly the same problem? :confused:

TIA for any and all help and advice.  As a novice, I ask humbly that y'all be gentle and complete with any responses.  I'd hoped not to have to become a "GRUB guru" this soon in my learning curve, but apparently I must...  I am determined to join the ranks of Linux and Ubuntu, and eventually hope to give back to the community, once I actually learn something! :)

So, so far, I've done no damage to my PC -- it remains W2K bootable, and I've only accomplished a partial (unsuccessful) Kubuntu install.  I patiently, and gratefully, await any and all helpful guidance!

---

### Post by Pumalite on 2007-12-14
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by dstew on 2007-12-14
> 1. Why does the Install fail at the "installing GRUB" point? There are no error messages or numbers which indicated anything for diagnosis... just the error-box as quoted in full above.Good point. The installer does not report the errors, but see below.> 2. Is GRUB installable for dual-boot with W2K?Yes. I have a notebook at work which dual boots W2K fine.> 3. Can I manually finish the GRUB install, assuming y'all can give me complete guidance and advice here?Yes, and this is what you need to do.>  4. If "Yes" to #3 above, what's left undone by the fatal termination of the Install... that is, what's left to do after the GRUB install that hasn't yet been done?Installing grub is the last thing that the installer does. You probably have the Ubuntu system ready to go. You just need to install grub.> 5. Alternative to 1-4 above, should I just try to install Ubuntu v7.04, or would I encounter exactly the same problem?One goal of all this is to learn. Why don't we try to get grub set up on your installation? Then we might both learn something.

To install grub manually, see [this thread]("http://ubuntuforums.org/showthread.php?t=224351"). If grub doesn't install, at least you get to see the error messages!

---

### Post by mondy on 2007-12-14
**This post could be related to an Ubuntu bug filed at**: test your hd or ormat with win98 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **Lorin Ricker said:**
> Initial conditions:  1) I'm a Linux/Ubuntu newbie.  2) My intention is to, ultimately, abandon Windows completely on all my PCs, replacing with (K)Ubuntu -- please, no advice to "kill all Windows", I've just got to migrate efficiently but quickly, but I've still got legacy data & apps to deal with.  3) Working with a downloaded Kubuntu v7.10 Desktop distro -- live CD boots and runs fine on my first target PC.  However, installation runs into a snag that I cannot figure out.

Target PC: older Compaq box, AMD Athlon CPU, 654,832 Kb RAM
OS: Windows 2000 Pro 5.00.2195, SP4.
Phoenix - AwardBIOS v6.00PG (AK73 Series R1.17).

```

2 Hard drives:
IDE Primary Master -- Maxtor 96147H6 (approx 60Gb)
IDE Primary Slave   -- ST340016A         (approx 40Gb)

IDE Secondary Master -- Hewlett-Packard DVD
IDE Secondary Slave   -- Compaq DVD-ROM SD-6
Drive A -- 1.44M 3.5in (floppy)
Drive B -- (none)
Video -- EGA/VGA

Partition configuration:
Device        Type    Mount point   Size     Used
/dev/hda
  /dev/hda1   ntfs    /media/hda1   21002Mb  12700Mb   # C: - where W2K lives
  /dev/hda5   ntfs    /media/hda5   36082Mb  14800Mb   # E: - where my Windows data lives
  /dev/hda6   swap                           2933Mb    # swap for Linux
/dev/hdb
  /dev/hdb1   ext3    /                      40015Mb   # Linux root, where Ubuntu installs

```

Prior to getting started with (K)Ubuntu, I was fortunate to have partitioned disks as above, and taking over hda6 and hdb1 for Linux root and swap was just lucky.  So, now on to my problem...

As mentioned above, I've booted both the Kubuntu v7.10 (Gutsy) and an older Ubuntu v7.04 distro (from "The Official Ubuntu Book") on this PC and played around with both without any problems... enough to give me the courage to click on Install.

And Install seemed to go fine, up to a point.  My first attempt, using the "Manual Partitioning" choice, got through the reformatting of hdb1 (root) and hda6 (swap) just fine, and then Install proceeded to Copy files..., Installing hardware..., etc., a-okay.

However, when we got to about 94% done, at the point where the process got to:

```

Installing GRUB boot loader...
  Running "grub-install (hd0)"...
  Detecting operating systems...

```

after about 30 seconds, I get this error-box:

```

Unable to install GRUB in (hd0)
  Executing 'grub-install (hd0)' failed.
  This is a fatal error.
         <OK>

```

Clicking the <OK> button then terminates the installation.  Apparently (and having tried the Install twice more, to understand and document the failure point), what I'm left with is:

a) Correctly formatted hdb1 (root) and hda6 (swap) partitions.
b) Kubuntu files copied from distro to hdb1, but that drive is not (yet) bootable.
c) MBR on hda1 (hd0) is unchanged, still boots Windows 2000 just fine.

Here are my questions:

1. Why does the Install fail at the "installing GRUB" point?  There are no error messages or numbers which indicated anything for diagnosis... just the error-box as quoted in full above.

2. Is GRUB installable for dual-boot with W2K?  A brief read through the GRUB entry of the O'Reilly "Linux in a Nutshell" book warns me that there are issues with dual-booting NT and W2K, but I'm too new to this to make out what to do about it, if true.  It seems to indicate that I must leave the Windows boot code alone in hda1 MBR, but add something about "chaining" to GRUB code on hdb1(???) -- but if so, how does dual-booting then work to get Kubuntu up? :confused:

3. Can I manually finish the GRUB install, assuming y'all can give me complete guidance and advice here?

4. If "Yes" to #3 above, what's left undone by the fatal termination of the Install... that is, what's left to do after the GRUB install that hasn't yet been done?

5. Alternative to 1-4 above, should I just try to install Ubuntu v7.04, or would I encounter exactly the same problem? :confused:

TIA for any and all help and advice.  As a novice, I ask humbly that y'all be gentle and complete with any responses.  I'd hoped not to have to become a "GRUB guru" this soon in my learning curve, but apparently I must...  I am determined to join the ranks of Linux and Ubuntu, and eventually hope to give back to the community, once I actually learn something! :)

So, so far, I've done no damage to my PC -- it remains W2K bootable, and I've only accomplished a partial (unsuccessful) Kubuntu install.  I patiently, and gratefully, await any and all helpful guidance!

:lolflag:

---

### Post by Lorin Ricker on 2007-12-14
dstew -- Thanks for the advice and encouragement. In particular:

> 2. ... Yes. I have a notebook at work which dual boots W2K fine.

Great -- I've taken fresh courage. :)

> One goal of all this is to learn. Why don't we try to get grub set up on your installation? Then we might both learn something.

To install grub manually, see ... If grub doesn't install, at least you get to see the error messages!

Roger that -- I'm intrepid, but not rash.  I'll need a while to read & comprehend all this, as I'm certain only at this point that idle experimentation can actually trash things.  I'll come up for air tomorrow, hopefully a bit wiser, and will give this all a go... I do get the gist of it, just not the details (yet).

Naivity checkpoint:  Is the O'Reilly "Linux in a Nutshell" book's advice about GRUB in re: "don't overwrite the Windows MBR, but use 'chaining'" indeed on the right track?  Or a blind alley for my config?

Again, thanks, and I'll keep y'all posted.

---

### Post by Pumalite on 2007-12-14
No. Install Grub to the MBR and you'll have an option to boot either OS.

---

### Post by Lorin Ricker on 2007-12-15
OK, help... I'm stuck now.  Following the advice above, I have done this:

1.  Backed up everything of value on my Windows partitions... two separate places, so I'm OK there.
2.  Booted the Kubuntu Live CD (Gutsy, v7.10) ... when I get a Konsole up, here's what I do (excuse any typos... I'm re-entering this on a laptop keyboard):

```

$ sudo mkdir /mnt/root
$ sudo mount -t ext3 /dev/hdb1 /mnt/root      #Kubuntu's install partition is hdb1
$ sudo mount -t proc none /mnt/root/proc
$ sudo mount -o bind /dev /mnt/root/dev
$ sudo chroot /mnt/root /bin/bash
#

```

Up to this point, fine... doing a mount -l shows me a believable set of mounted devices.

I understand basically what's doing, including the chroot, as per the "How to install Grub from a live Ubuntu cd" thread.  But checking the /boot/grub directory doesn't look right...

```

# ls /boot/grub/
device.map
# 

```

Um... just one file?  Shouldn't there be some stage[123] files here?  Boldly, let's see what grub itself says:

```

# sudo grub
Probing devices to guess BIOS drives.  THis may take a long time.
### actually, it doesn't.  It just immediately clears-screen, and jumps right to...

   [ Minimal BASH-like ... ]

grub> find /boot/grub/stage1

Error 15: File not found

grub> quit   ### don't go any farther!...
# 

```

So, it seems like my original couple of Kubuntu Install tries (yesterday) have come up short?  Or do I boldly & blindly proceed with the grub root (hd1,0) ; setup (hd0) commands??? :confused:  That seems to me like asking for trouble (a trashed MBR), if the grub find fails, right?

So, I need more advice!  I do think I'm looking at directories and files on hdb1 (my install target), if I've understood and done the above mounts right.  So why is there only a device.map file in /boot/grub/???  :confused:

I'm flat stuck, clueless.  Studying other threads and reference books is not helpful at this point, as I'm not sure what the right initial conditions for this whole grub operation really are... it just looks like I'm short of files.  How do I proceed?  Are the right files stashed somewhere on the Live CD, and I just have to copy them to /boot/grub/?  Or what?...  I've no plans (and in no hurry) to continue with this until I better understand what's needed next.

TIA -- This forum and the whole Ubuntu/Linux community is fantastic!  I'm low on my learn-curve, but am determined to ramp up quickly.

---

### Post by dstew on 2007-12-16
> Um... just one file? Shouldn't there be some stage[123] files here?You were doing **ls** on the LiveCD filesystem, which does not have grub stage1, stage2 etc. Try```
# ls /mnt/root/boot/grub/
```Of course, if you turned off the computer, you need to mount the hard disk to the LiveCD file system again.

---

### Post by Pumalite on 2007-12-16
Before installing ANY OS you should backup everything. The best option is to install Grub to MBR.

---

### Post by Lorin Ricker on 2007-12-16
Thanks, dstew -- You said:

> 
 Um... just one file? Shouldn't there be some stage[123] files here?
You were doing ls on the LiveCD filesystem, which does not have grub stage1, stage2 etc. Try
Code:
# ls /mnt/root/boot/grub/

Of course, if you turned off the computer, you need to mount the hard disk to the LiveCD file system again.


Didn't the chroot command put me in the right context?  I'm the novice here (at Linux, but not at computation), and I had thought about "am I ls'ing the right place?..." -- From the evidence, I thought I was.

I did indeed try the ls command you gave (above)... the response was "Not a directory" -- so now your response has *really* confused me. :confused:

I can reboot the Live Disc and try again, but I'm pretty sure that I'm only going to reproduce my earlier results (sorry to seem obstinate -- I'm not meaning to be... :) ).  If the ls command you give above is supposed to work, then did I do all the mount steps right?  To an old VMS hack like me, this mount-point stuff is still pretty impenetrable.  Please be patient -- I'll catch up soon!

BTW, please also see thread [http://ubuntuforums.org/showthread.php?p=3964719](http://ubuntuforums.org/showthread.php?p=3964719), which is exactly the same problem I'm having (with Edgy), but with Feisty!  That thread has no resolution yet, either!

I remain persistent (to fix this), willing (to learn), and will be methodical at whatever next steps y'all might offer.  Thanks!

---

### Post by Pumalite on 2007-12-16
Boot your Live CD and post from Terminal:
sudo fdisk -lu
Mount your partition:
sudo mkdir /media/dev/xxx (you get this from your fdisk -lu)(sdax or hdax or sdbx or hdbx,etc)
sudo mount -t ext3 /dev/xxx /media/dev/xxx ( sda2,3,4 or 5)
From that partition, post:
cat /boot/grub/menu.lst
(if you are using Vista, you should have allocated space for Kubuntu with Vista partitioner in the first place. If that is so, and you didn't do it that way, you should start again)

---

### Post by vinay.v on 2007-12-17
Is the problem fixed? If not, here is something you can try. I had the exact same problem (with Ubuntu) yesterday night and I fixed it.
I notice that you are installing (k)Ubuntu to /dev/hdb1, which is the first partition in the second hard disk. I did the same too. And I got rid of the error by enabling the "boot" flag for that partition.
To do that, you can boot from the live CD. Open up the partition manager (gparted). Select the first partition on the second disk (/dev/hdb1), where you want to install Ubuntu. Right click on it and select "Manage Flags". In the dialog that comes up, put a check mark on the Boot flag and close the dialog and the partition manager. 

Now try installing grub (or re-installing Ubuntu from live cd) and it should work.

To answer your other question, you CAN manually finish installing grub after setting the boot flag for the partition. But I wouldn't recommend this as for me, not all files were completely copied by setup to the partition when the grub install failed for me. I installed grub manually, but a lot of device files in the /dev directory like /dev/hda*, /dev/hd*, were missing. This will make your system unusable even after you install grub. So, a better thing to do is to completely re-install to the same partition (after enabling the boot flag)

---

### Post by Lorin Ricker on 2007-12-17
Thanks, vinay.v!!!  This looks like, finally, the right track.  I'll be able to do this reinstall later this evening, and will post results.  With fingers-crossed (I'm anxious to be **using** Kubuntu, not messing around with install problems!).  :)  -- Lorin

---

### Post by Lorin Ricker on 2007-12-19
OK.  I've mixed news on this.  Here's the good news:  I'm _finally_ an Ubuntu (not Kubuntu) user, Gutsy v7.10 -- I finally got a clean install late last night.  But I had to use the Alternate Desktop CD, not the Live CD.  But, after several experiments which initially only reproduced my original problem, the Alt-CD finally came through.  **Now** my real learning curve begins...

Initially, here's what I did:

a) Attempting to follow vinay.v's advice (post #12 above) -- Booted original Kubuntu 7.10 Live CD, went looking for the gparted partition manager, but only found QTparted... so I tried that utility.  However, QTparted does not appear to have any means of managing the boot (etc.) flags, so after fooling around just a bit with this, I gave up on Kubuntu-CD and, instead...

b) Booted Ubuntu 7.10 Live CD... Here I found the gparted utility, just as vinay.v said, and as I started it, I noted that the first partition on the IDE0 drive (/dev/hda1, where Windows lives) was marked with a boot flag (as expected).  So I attempted to set the boot flag for first partition on IDE1 drive (the correct equivalent of /dev/hdb1 in gparted).  When I clicked OK on this dialog box, gparted crashed!  Restarting it, I then found that the /dev/hdb1 drive indeed now carried the boot flag (and /hda1 did not -- can only one drive be marked with this boot flag at a time?).  So apparently it worked, but why the application crash?

c) OK, now believing that, perhaps, these drive flags were configured properly, I rebooted the Kubuntu 7.10 Live CD, and started a full install.  Paid close attention to the partitioning choices (I'm getting good at that part!), and let 'er rip.  About 10 elapsed minutes later, at exactly 94% install completed, the very same

```
Unable to install GRUB in (hd0)
  Executing 'grub-install (hd0)' failed.
  This is a fatal error.
```

occured.  Incomplete installation.

d) OK, let's try this with Ubuntu 7.10 Live CD (anticipating yet another demonstration of Einstein's definition of "insanity") -- boot this disk, start an installation... 10 minutes later:  Boom!  Same fatal error at exactly 94%.  Dead duck (er, Gibbon).

e) Great -- let's try one more... Insert the Alternate Desktop CD 7.10, boot it and start an installation from this.  Hmmm... After answering install ?'s, this one takes _a lot longer_ to get things done (compared to the two Live CDs above), but at about 40 minutes elapsed, I observed the Executing 'grub-install (hd0)' step to **succeed**!  And the installation then finished just fine!

f) Upon reboot, I now see a grub dual-boot menu, with the Ubuntu and my original W2K bootstrap choices, installed and working just fine.  Tests show that each boot option indeed works/boots the correct OS.

So, to summarize:  i) I've done a successful install on this PC, with grub dual-boot capability, using the Ubuntu 7.10 Alternate Desktop install-CD.

ii) I don't know for sure whether or not vinay.v's advice (#12) was instrumental in making this third install attempt work... Would the Alt-CD install have worked without fiddling with /hdb1's boot flag?  I dunno.

iii) I certainly believe that there's a bad bug in (at least) the v7.10 Live CD installation processes, both for Ubuntu and Kubuntu, and I'll try to report a coherent & helpful bug report to that effect.

iv) I don't know if this problem is specific only to some hardware configurations (ref. Thread [Unable to install Ubuntu Feisty - Grub-install hd(0) fatal error]("http://ubuntuforums.org/showthread.php?t=449767"), where sainib reports exactly the same problem with nearly identical hd-configuration, installing into IDE1/partition-1), or if it's dependent on BIOS issues, or what.  :confused:

v) At any rate, after posting a bug report, I'm going to consider this issue only "partially resolved", as I prefer to get along with actually learning and using Ubuntu -- and I simply don't have the requisite knowledge or expertise to investigate and fully diagnose this any further on my own.

Many thanks to all who responded with helpful advice and wisdom!  Ubuntu lives (and Windows will ultimately die) in Franktown Colorado! :)

---

### Post by bobopopo on 2008-02-18
No clue why this thread is marked as "solved" because I read a lot of threads and none of them had a solution. Just a lot of geeky stuff and after trying out some I was tired of being misled all the time.

If there is a solution, it should be marked what the solution is...

I have a very standard Samsung X11 Laptop (Intel Dual Core, 2GB RAM, 200GB Sata HDD) and already successfully installed Ubuntu 7.04 on this machine (just with a 100GB Sata HDD) without any trouble (that was my first linux installation) in dual boot with Win XP pro.

After changing the HDD I wanted to have the dual boot setup again to further play around with (K)Ubuntu. So downloaded Kubuntu 7.10 and tried to install but permanently received the 'Fatal Grub error' stated above.

Then I tried to install Ubuntu 7.04 hoping that at least that will work out (because it worked out before, just disk size changed) and again had the Grub error. After thinking over what was the difference between the working setup and the faulty setup I realized that I formated the system partition (root) for (K)Ubuntu as ext2 filesystem (because I did not know better). So I tried that and it immediately worked out...

I learned that ext3 is a more modern version of ext2 with more security and more features and already exists since some years - so how is it possible that Grub produces an installation failure from this? My hardware is neither too new nor outdated, very standard and I assume a lot of people had the same trouble that I had and wasted days on something with a very easy solution (that is mentioned nowhere!).

For me that is really another proof of the very poor documentation and help features that (K)Ubuntu comes with. Yes, I am a newbie with (K)Ubuntu and if is pretty stupid to try to install it with ext3 (what obviously often does not work well) then the system should tell me and not just terminate in a fatal error.

Sorry for writing so much on this but I am really fed up with the (still) very geeky solutions and absolutely poor documentation...

Nevertheless, it's free and I honor the hard work of the community - but sometimes the developers should really lean back and have a look at their work from the perspective of a newbie (just think of the pop-up and error messages in a lot of well known programs like 'gparted' that make absolutely no sense (due to bad translation or poor design)). Then (K)Ubuntu might become the userfriendly OS that it always claims to be - at the moment that is just daydreaming...

Cheers,

bobopopo

---

