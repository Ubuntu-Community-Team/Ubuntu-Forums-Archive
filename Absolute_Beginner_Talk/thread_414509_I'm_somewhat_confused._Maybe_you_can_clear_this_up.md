---
title: "I'm somewhat confused. Maybe you can clear this up."
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-04-19
I installed Windows XP on one of my hard drives when it was set as master. Just recently I bought a new hard drive. I set the new hard drive as master and installed Ubuntu onto it. I set the Windows as slave. Grub located my Windows drive and I could boot to either the Windows drive or the Ubuntu drive.

Problem:
I had a power failure during a defrag of Windows. After that, I could not boot back into Windows. I could not boot into Windows when I "removed" the Linux drive and reset the Windows drive to master. After much effort I decided to fdisk my drive. My BIOS sees the drive as 80 GB. That is what it should see. However, I can only get 7.9 GB to show up after I partition the drive to one partition. Is that because Windows is still in another partition but unrecognized by fdisk? If that is the case, how can I repartition the hard drive, since fdisk will not work, and get all of the hard drive back. I do not have important files, so formatting is no problem. Formatting at this time shows only the 7.9 GBs...not the full 80GBs.
I do not have a CD-Rom/R-W drive that is presently working. Therefore I can not burn gparted to a disk. It too went bad about the same time I messed up the 80GB hard drive. I know that it was working the day before this problem occurred. When it rains, it pours.
Any help would be greatly appreciated. Where are you computer geeks? You are being herald. 
kh

---

### Post by freebird54 on 2007-04-19
How bad is the CD-RW.  If it still reads, then the fixes (whichever they may be) will probably de best done from the Live CD (if that's what you installed from).  GPartEd is a free Partition Magic essentially, and some Magic is what's needed here!

---

### Post by Pobega on 2007-04-19
If your power went out during a defrag I think you're in for a long night.

I'm not sure if you're able to get back any of that data, but if I were you I would just do a clean install; Maybe backup anything that you need using a LiveCD and USB drive (LiveCD for a GNU/Linux environment, and a flash drive for storing the data) and then do a fresh install.

But don't take anything I've said here as definite fact, I haven't worked much with NTFS/FAT file systems so I'm not 100% sure. But if I understand correctly what defragging actually does, I think you're kind of screwed.

---

### Post by kittyhawk63 on 2007-04-19
> **freebird54 said:**
> How bad is the CD-RW.  If it still reads, then the fixes (whichever they may be) will probably de best done from the Live CD (if that's what you installed from).  GPartEd is a free Partition Magic essentially, and some Magic is what's needed here!

Hi Freebird54. Glad you are here. No, my BIOS does not recognize my CD-RW drive. I get no light on boot up. I have wiggled every wire that I can think of and disconnected and reattached wires to no avail. I think the CD-RW went bonkers. But I don't really know for sure.

---

### Post by kittyhawk63 on 2007-04-19
> **Pobega said:**
> If your power went out during a defrag I think you're in for a long night.

I'm not sure if you're able to get back any of that data, but if I were you I would just do a clean install; Maybe backup anything that you need using a LiveCD and USB drive (LiveCD for a GNU/Linux environment, and a flash drive for storing the data) and then do a fresh install.

But don't take anything I've said here as definite fact, I haven't worked much with NTFS/FAT file systems so I'm not 100% sure. But if I understand correctly what defragging actually does, I think you're kind of screwed.

It will not take a reinstall. I tried a number of times.

---

### Post by kittyhawk63 on 2007-04-19
It won't take a new install because there is not enough GB to work with, That is why I need to get back my whole drive, not just the 7.9GB that it recognizes with fdisk. I can't seem to repartition the drive with only one partition.

---

### Post by Pobega on 2007-04-19
> **kittyhawk63 said:**
> It will not take a reinstall. I tried a number of times.

What do you mean *it won't take a reinstall*?

Do you mean that your computer isn't letting you reinstall it, or that there is a way to work around it?

If you know a workaround already why post here? :P

**Edit:** Now I see your above post, so I'll respond to that. Your entire drive is only being picked up as 8GB? Or just your partition?

---

### Post by kittyhawk63 on 2007-04-19
Here is a thought. If I try installing Ubuntu onto this drive will it repartition the _***whole***_ drive?

---

### Post by freebird54 on 2007-04-19
It sounds (unfortunately) as if you may have taken a power surge in conhunction with your power outage.  I don't think a recovery is possible without a functioning (in read mode) CD drive.  Any old ones lying around the house?  In a box at the back of a cupboard?  Still in the old computer that you didn't take to the computer recyclers yet?

If there was nothing particularly valuable on the drive, all you can do about this is to start again - hoping that the HD itself is OK.  :(

---

### Post by kittyhawk63 on 2007-04-19
> **Pobega said:**
> What do you mean *it won't take a reinstall*?

Do you mean that your computer isn't letting you reinstall it, or that there is a way to work around it?
If you know a workaround already why post here? :P
**Edit:** Now I see your above post, so I'll respond to that. Your entire drive is only being picked up as 8GB? Or just your partition?
BIOS sees it as 80 GBs. But fdisk only allows the 7.9GB for installing an OS. I am posting because I don't know of a workaround.
kh

---

### Post by kittyhawk63 on 2007-04-19
> **freebird54 said:**
> It sounds (unfortunately) as if you may have taken a power surge in conhunction with your power outage.  I don't think a recovery is possible without a functioning (in read mode) CD drive.  Any old ones lying around the house?  In a box at the back of a cupboard?  Still in the old computer that you didn't take to the computer recyclers yet?

If there was nothing particularly valuable on the drive, all you can do about this is to start again - hoping that the HD itself is OK.  :(

 I still have one CD-Rom on the computer that is working fine. Nothing happened to it. I can't get the hard drive to take a full OS install unless Ubuntu can be loaded there on 7.9 GBs.

---

### Post by Pobega on 2007-04-19
> **kittyhawk63 said:**
> BIOS sees it as 80 GBs. But fdisk only allows the 7.9GB for installing an OS. I am posting becasue I don;t know of a workaround.
kh

Mmm...What install CD are you using? I'm assuming the Ubuntu alternate install CD (fdisk), and if that's so I'd personally try another distro's install CD just to see if that changes anything. If it does you can install that distro, and then install Ubuntu over it.

I recommend [Debian's Etch Installer](http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/) and boot it with the "installgui" parameter to get a GUI installer. It's the most advice I can offer.

---

### Post by kittyhawk63 on 2007-04-19
> **Pobega said:**
> Mmm...What install CD are you using? I'm assuming the Ubuntu alternate install CD (fdisk), and if that's so I'd personally try another distro's install CD just to see if that changes anything. If it does you can install that distro, and then install Ubuntu over it.

I recommend [Debian's Etch Installer]("http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/") and boot it with the "installgui" parameter to get a GUI installer. It's the most advice I can offer.

No, I have the full version of Ubuntu on live CD. I am using my Linux hard drive right now. There is nothing wrong with it. I am trying to get my Windows XP hard drive working again with GRUB. Maybe I should be on another forum. I was just thinking that others with a dual boot using two hard drives may be able to help.

---

### Post by lamalex on 2007-04-19
have you tried the gparted cd yet?

---

### Post by kittyhawk63 on 2007-04-19
> **Iamalex said:**
> have you tried the gparted cd yet?

I can't burn the iso of gparted. I lost my CD-RW drive the same time I started having hard drive problems.

---

### Post by kittyhawk63 on 2007-04-20
Can I repartition my Windows XP hard drive by using a Linux program which is on my Linux hard drive? In other words, I am using two separate hard drives.

If I can partition the one hard drive by using Linux on the other hard drive, what program can I use? I cannot burn gparted. I installed it from the repositories but cannot locate it anywhere on the Menu. 

I do **not** have a CD-RW drive to burn the gparted iso to a CD disk.
Thanks for any suggestions.
kh

---

### Post by Comzee on 2007-04-20
I have a dual boot setup and have had tons of experience with PC hardware. From my experience of many corrupted hard drives, the BIOS is always wrong. I would trust fdisk. I once had a horribly corrupted hard drive from a lightning strike and the BIOS still said it had it's full 40gb left. Which was totally wrong. It might just be that a huge chunk of sectors on your HD got corrupted. I'm assuming you've never but Linux on your Windows HD.

---

### Post by kittyhawk63 on 2007-04-20
> **Comzee said:**
> I have a dual boot setup and have had tons of experience with PC hardware. From my experience of many corrupted hard drives, the BIOS is always wrong. I would trust fdisk. I once had a horribly corrupted hard drive from a lightning strike and the BIOS still said it had it's full 40gb left. Which was totally wrong. It might just be that a huge chunk of sectors on your HD got corrupted. 

I'm assuming you've never but Linux on your Windows HD.

I think that may be correct. I really can't remember. My memory is poor due to an illness I am recovering from. However, I "don't think" I have installed Linux on that particular drive. What if I had once installed to the windows drive. Would that make a difference? Is that what could have repartitioned the drive the way it is? If it is, will Linux repartition it again? This time correctly?

---

### Post by freebird54 on 2007-04-20
Without being able to view it from a known capable source - it is quite difficult to tell.  One of the simpler ways is to use your original live CD to boot up and take a look at things.  THis could mean replacing the drive, of course, if it won't read either.  Another is to install (you have net access for Synaptic?) the QPartEd partitioning program on your main Ubuntu.  This can then, after you UNmount your Windows drive, take a look at it and tell us what to do next.

Of course, even a

```
sudo fdisk -l
```

output posted here would help with that  - assuming it can see the Windows drive...

---

### Post by Comzee on 2007-04-20
> **kittyhawk63 said:**
> I think that may be correct. I really can't remember. My memory is poor due to an illness I am recovering from. However, I "don't think" I have installed Linux on that particular drive. What if I had once installed to the windows drive. Would that make a difference? Is that what could have repartitioned the drive the way it is? If it is, will Linux repartition it again? This time correctly?

I'm just learning about Linux partitions. I know alot more about windows partitioning and file systems. I do know one thing. If you have an XP disk, it will detect any unknown partitions and let you delete them and re-partition the space to NTFS. If you don't have one try to borrow one from a friend or anybody. If all else fails run a huge magnet over it and try partitioning it after that.

---

### Post by kittyhawk63 on 2007-04-20
> **Comzee said:**
> I'm just learning about Linux partitions. I know alot more about windows partitioning and file systems. I do know one thing. If you have an XP disk, it will detect any unknown partitions and let you delete them and re-partition the space to NTFS. If you don't have one try to borrow one from a friend or anybody. If all else fails run a huge magnet over it and try partitioning it after that.

A huge magnet will not damage the hard drive? 

I do have an XP install disk. I will try that. I have been trying installing first with my WinME install disk because I like using the Easy Access Keys on my Compaq keyboard. XP does not support them. After installing WnME I use the upgrade feature of XP. This keeps my Easy Access Keys functioning. 
However, since push has gone to shove, I will forgo the Easy Access keys and see if XP will work. Thanks for the advice. 
Please reply about the magnet. Could it possible damage it in any way?
kh

---

### Post by freebird54 on 2007-04-20
There is no real difference between partitioning in Windows and partitioning in Linux.  The biggest change is that Linux recognizes more file systems (and can work with them) than Windows will admit to.  The physical set up of partitions is unchanged either way.  (4 primary only, extended+logical to get around it etc etc)

Hope that helps understand things!

(if it's to the magnet stage, it's probably to the 'bin it' stage too)

---

### Post by medad on 2007-04-20
I was thinking about your issue and had two different trains of thought (This is assuming that you have kissed off any chances of recovering your WinXP files):

1> Do you have your Windows XP CD?  If you do, install it and select R for recovery.  It will take you to the C drive.  Enter Diskpart.  It should let you see the entire C drive.  You can unpartition any  partitions still showing.  Then you can try to partition your complete drive and then exit the program.  After that you can format your disk by entering FORMAT C:.  Then you should be able to reload your WinXP program.

2>  Look for Gnome Partition Editor in your System/Administration folder.  From there you should be able to see what your old Windows drive looks like (This is assuming that you have the linux harddrive as primary and your windows harddrive as slave).  You should be able to select the Windows harddrive and work from there.  I don't have much experience in using Gparted, but it seemed pretty easy to comprehend when I was partitioning my 300GB harddrive.  I am still pretty much a newbie to linux.

Good Luck.....

---

### Post by kittyhawk63 on 2007-04-20
> **freebird54 said:**
> There is no real difference between partitioning in Windows and partitioning in Linux.  The biggest change is that Linux recognizes more file systems (and can work with them) than Windows will admit to.  The physical set up of partitions is unchanged either way.  (4 primary only, extended+logical to get around it etc etc)
Hope that helps understand things!
(if it's to the magnet stage, it's probably to the 'bin it' stage too)

Thanks for the advice.
kh

---

### Post by kittyhawk63 on 2007-04-20
> **medad said:**
> I was thinking about your issue and had two different trains of thought (This is assuming that you have kissed off any chances of recovering your WinXP files):
1> Do you have your Windows XP CD?  If you do, install it and select R for recovery.  It will take you to the C drive.  Enter Diskpart.  It should let you see the entire C drive.  You can unpartition any  partitions still showing.  Then you can try to partition your complete drive and then exit the program.  After that you can format your disk by entering FORMAT C:.  Then you should be able to reload your WinXP program.
2>  Look for Gnome Partition Editor in your System/Administration folder.  From there you should be able to see what your old Windows drive looks like (This is assuming that you have the linux harddrive as primary and your windows harddrive as slave).  You should be able to select the Windows harddrive and work from there.  I don't have much experience in using Gparted, but it seemed pretty easy to comprehend when I was partitioning my 300GB harddrive.  I am still pretty much a newbie to linux.
Good Luck.....

I will try your suggestion tomorrow as soon as my brain clears. It is getting late and I have been up since early this morning. It seems this will take more time than I have for tonight.
Thank for the suggestion.
kh

---

### Post by Comzee on 2007-04-20
> **freebird54 said:**
> 

(if it's to the magnet stage, it's probably to the 'bin it' stage too)

It is a last resort. If neither your XP disk or Linux disk can see free space or partitions that would be your last option. The magnet only effects the HD disks, every modern HD has a small flash space where it keeps it's info, like manufacturer and how much space it is suppose to have. The magnet just realigns the magnetic poles of the disk, like smashing a magnet with a hammer. In most cases it doesn't work though, so it is a very last step in trying to fix it.

---

### Post by kittyhawk63 on 2007-04-20
> **Comzee said:**
> It is a last resort. If neither your XP disk or Linux disk can see free space or partitions that would be your last option. The magnet only effects the HD disks, every modern HD has a small flash space where it keeps it's info, like manufacturer and how much space it is suppose to have. The magnet just realigns the magnetic poles of the disk, like smashing a magnet with a hammer. In most cases it doesn't work though, so it is a very last step in trying to fix it.
Thanks Comzee for the info.
kh

---

### Post by jimbean on 2007-04-20
what kind of harddrive is it most harddrive makers maxtor ,ibm, seagate have diagnostic programs on there web sites

---

### Post by Jhongy on 2007-04-20
You'd need a bloody stong magnet to erase the hdd... don't bother

I second the option of using "Gnome Partition Editor" in your Administration menu. It will almost certainly pick the wasted space up.

If not, check your jumper settings on the drive - ensure they're both set to cable select, or master/slave. Also look in the BIOS and set the drive type on that channel to be "auto detect", or something similar.

---

### Post by rillip on 2007-04-20
Just idle speculation here, but may be worth a guess.

I had a similar issue.  I had Win 2k installed. It was working fine.  Something hapened, think I ended up needing to replace the mobo or something.  Anyway, the drive got taken out, put back in.  Figured I should just be able to boot.

And I could. But, the instant I tried to run anything, I got metric tonnes of errors and crashed.

Looked into it and found my 40 gig drive was only 8ish gigs according to Windows!! I saw it the same as always in Bios.

After a few days of chuggling along with it, I remembered that there was a jumper that could be set to limit the drive for workstation use. I never really got the feature and had just left it in the default configuration - which was, of course, the 8 gigs.

When I set the jumpers correctly, it worked. I never did figure out why it suddenly had a change of heart on detecting that feature.  Can you check your drive for a similar issue? It may be completely unrelated, but I could never explain the change, so who knows unless you try?

If you don't have important data, you might try getting a utility like KilDisk and zeroing the drive.  That should definitely remove any concerns about partitions and such.

---

### Post by kittyhawk63 on 2007-04-20
Good morning. Thanks for the last three posts. Sorry I was away in dream land and didn't come back to you sooner. I will try each suggestion in the order they come (less the magnet) and will let you guys know if any of them work and will post what was successful. I will also post if nothing corrected the problem.
I still have not had this answer. Can I work with the Windows drive (partition and format) by using Linux. which is on another drive?
Not sure how long I can stay with this, I have just started "upgrading" to Feisty using dist-upgrade command in terminal.
Thanks again for all the great suggestions.
kh

---

### Post by medad on 2007-04-20
Gparted should be able to partition and format your Windows drive by using Linux, which is on another drive.  When I partitioned my 300GB, I left 50GB open for Windows XP and formated that partition to NTFS, but I never ended up installing XP.  But everytime I check the partition it is showing up as NTFS.

---

### Post by kittyhawk63 on 2007-04-20
> **medad said:**
> Gparted should be able to partition and format your Windows drive by using Linux, which is on another drive.  When I partitioned my 300GB, I left 50GB open for Windows XP and formated that partition to NTFS, but I never ended up installing XP.  But everytime I check the partition it is showing up as NTFS.

Medad,
I installed gparted from the repos but I can't find it in the Menu. Where do I find it to use it? I can't burn it. I have no CD-RW rom drive. Thanks for your info, so far, though.

---

### Post by rillip on 2007-04-20
If you look through, I believe someone already answered a few places to look in Gnome.  If you're using Kde, it's K-menu, Settings -> Gnome partition editor

---

### Post by kittyhawk63 on 2007-04-20
> **rillip said:**
> If you look through, I believe someone already answered a few places to look in Gnome.  If you're using Kde, it's K-menu, Settings -> Gnome partition editor

Thanks. I am using Gnome and will see if I can locate it by doing a search. I wasn't able to find it yesterday in the short time that I had. I will try again. Muchos gracias!
kh

Edit: I did find my answer about locating gparted. I found that it had not installed for some reason. I will reinstall it after I finish upgrading to feisty. 71% downloaded so far in 1-1/2 hrs. Not too bad considering the burden on the servers.

---

### Post by freebird54 on 2007-04-20
System->Administration->Gnome Partition Editor.

You will jnow if it will work for you more easily by opening a terminal and doing

```
sudo fdisk -l
```

which will give you what the 'rest of the world' thinks the drive is.  GPartEd will allow you to make changes.  Unless the drive is actually hosed of course!

---

### Post by kittyhawk63 on 2007-04-20
> **freebird54 said:**
> System->Administration->Gnome Partition Editor.

You will jnow if it will work for you more easily by opening a terminal and doing

```
sudo fdisk -l
```which will give you what the 'rest of the world' thinks the drive is.  GPartEd will allow you to make changes.  Unless the drive is actually hosed of course!

Thanks Freebird54
I have about one minute to go for the Feisty install to complete. I will check out your instructions soon after I reboot into Feisty.
kh

---

