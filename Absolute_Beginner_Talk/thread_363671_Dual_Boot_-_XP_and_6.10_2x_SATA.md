---
title: "Dual Boot - XP and 6.10? 2x SATA"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by jakc on 2007-02-17
I have spent last hour or so looking through similar threads, google videos and alike on how to install Ubuntu alongside Windows XP.

I am hoping to install Ubuntu mainly for the purpose of using [GRASS](http://grass.itc.it/) but also cos id like to learn more about linux as well.

However, I need my Windows.

I have ordered a huge 750GB seagate SATA drive which should be turning up in couple of days.  I am ok with computers but still I would prefer the simplest course of action to get a Ubuntu installed and still have an all around stable working envronment.

So maybe ive fallen over at the first hurdle by downloading **ubuntu-6.10-desktop-i386.iso** from one of the "local" official Ubuntu mirrors.

I do like to have the latest version, and I understand its may not be as simple as dapper or 6.06 but i like to have latest stable version and from what ive read it looks to be a good version.  Please point out if you think I should download a different installer cd?

Ok lets get my machine specs out the way b4 i forget:

MESH Matrix AMD 3500+
250GB SATA drive
*New 750GB SATA drive from seagate* - not yet installed
1gb RAM
g800GT Nvidia
Audigy 2 Plat Sound Blaster

Currently my partition on my 250GB looks like zis:
[IMG]http://i7.photobucket.com/albums/y254/jak-c/DrivePartition.jpg[/IMG]

Id quite like to keep that recovery partition even though ive got the XP installer cds somewhere.  

Partitions then...  I guess im gonna have a lot of storage to play around with when that 750 turns up, however id liek to reserve most of this for my video editing in windows.  However, I think I can spare 80GB or so for Ubuntu.  How should I set up my partitions then?  I assume I should do it with the Ubuntu partitioner (which I assume is part of the installer iso?) I dont want to wipe my existing Windows and start over if poss.  

Does Ubuntu have issues with partitions on SATA drives? 

Im backing up My Documents now, but I will admit - Im scared to burn that iso to a cd and put it in my machine - im trying to prepare myself as much as possible so please hurl ur advice at me, links to relevant threads or a "How to install" guide that will is suited to my version/specs/desires..........

Thanks in advance for any help.

:guitar: (thats me playing guitar)

---

### Post by Dylnuge on 2007-02-17
To start, I will just say that I am posting this from Ubuntu on a dual-booted Ubuntu XP laptop with SATA drives. I have not seen any issues with installation.

However, if you ever see anything on the forum refrencing hda or hdb or hda1 or hdb2 or something like that, be aware that it is actually sda or sdb or sda1 or sdb2. (hd or sd is hard drive or SCSI/SATA hard drive, the letter is the actual drive, the # is the partition ).

Also, ubuntu will recognise XP and not have any problems. When you reload, however, it will give you 10 seconds to choose an OS, and if you do not, it will boot Ubuntu.

---

### Post by mikewhatever on 2007-02-17
I've just reread your post three times, and still not quite sure what exactly are you going to do. Lets assume, that you'll install Ubuntu on the new HD. That in no way can harm any of the Windows partitions, since they are on the other HD. In fact, some have found it useful to disconnect that other HD during Ubuntu installation to make sure GRUB is written to the right place. 
I have a SATA drive of smaller size, and Ubuntu partitioner had done a good job resizing and partitioning it, but can someone guarantee the lack of problems?
The partition you need to create for Ubuntu are:
root - mounted as /
swap - mounted as swap
if you want, you can also create a FAT32 partition to exchange data between Windows and Ubuntu. That can also be done by means of a USB memory or by enabling Ubuntu writing to NTFS.

80 GB for root is more then enough, and swap size should be about 1GB or so.

Good luck, and welcome

---

### Post by jakc on 2007-02-17
> it will give you 10 seconds to choose an OS, and if you do not, it will boot Ubuntu

Surely this can be reversed as 9 times out of 10 i will be booting windows (i say that now).

However, niggles like this im not 2 bothered about at this stage.  I am really researching the installation procedure itself.  Good to hear you got it going easy enough on a laptop though.

---

### Post by jakc on 2007-02-17
> still not quite sure what exactly are you going to do

Me neither yet - hence asking for advice.

I think the partition bit is the bit Id like to set in stone before installing anything.  

Explain swap space please - is this similar to virtual memory in Windows, i understand that it has to be created for linux but what is it?  If I am doing processor/RAM intensive tasks in Ubuntu (GRASS) should I increase the SWAP space?

I imagine I will also need to transfer data between the two machines - So I assume that perhaps I will need to create an additional FAT32 partition to dump files too - id like to limit the number of  partitions if possible so would prefer to enable Ubuntu to write to NTFS - As long as this def can be done quite easily, perhaps I dont need to install the FAT32 partition?

So far:

DISK 0 (250GB) ill call sda  (250GB)
DISK 1 (750GB) ill call sdb  (750GB)

sda1 - Recovery (like to leave that there)  (5GB)
sda2 - Windows (C drive)  (230GB)

sdb1 - Ubuntu Root   (around 80GB)
sdb2 - Ununtu Swap  (1GB)
(sdb3 - Possibly a FAT32 medium to transfer data between OS's) (10GB)
sdb4 - Storage for Windows - All my media/video editing data to be stored (660GB)

I know order is important.  Please point out any errors or if I am confusing myself?

---

### Post by confused57 on 2007-02-17
This site explains much of what you'll need to get started:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

As mikewhatever suggested, you might want to disconnect your Windows drive when you install Ubuntu...you might want to connect your 750 Gb to the #1 controller, install Ubuntu, then reconnect your Windows drive to the #2 controller...see this guide, it's for IDE, but should work equally well for SATA:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

It would probably be best to "play" around with the live cd for a few days, just to make sure there are no compatibility issues with your system & to familiarize yourself with Ubuntu.  When you boot up the live cd, it won't hurt your system in any way to run it, open a terminal(Applications---Accessories---Terminal), enter(copy & paste):
```
sudo fdisk -l
```
The -l is a small "L"
This will show your current partition tables, if your SATA drive with Windows is detected properly, that's a good sign.

There are several different ways to setup your partitions: root(/) would probably be between 10-20 Gb, swap 1-2 Gb, separate home(individual preference), and you might want to set up a large ext 3 data partition, that you can share between Windows & Ubuntu...there's an fs-driver you can install on Windows, that enables Windows to recognize & rw to ext3.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

You'll probably get several different suggestions, 'cause there's many ways of setting things up...this is just one.

---

### Post by mikewhatever on 2007-02-17
> Explain swap space please - is this similar to virtual memory in Windows, i understand that it has to be created for linux but what is it? If I am doing processor/RAM intensive tasks in Ubuntu (GRASS) should I increase the SWAP space?

Swap in Linux is similar to the Page File in Windows, the difference it being a separate partition. Its size can vary, so if you think 1GB it not enough because you know you'll be running lots of programs etc, make it bigger. It's not like you are going to have space problems, right?

---

### Post by jakc on 2007-02-17
> be best to "play" around with the live cd for a few days

Ive downloaded the installer image:
*ubuntu-6.10-desktop-i386.iso*

But having trouble locatin a link for the live cd - I assume u just boot from this live cd and play about?

---

### Post by mikewhatever on 2007-02-17
> **jakc said:**
> Ive downloaded the installer image:
*ubuntu-6.10-desktop-i386.iso*

But having trouble locatin a link for the live cd - I assume u just boot from this live cd and play about?
Yes that's correct. A live session allows you to run Ubuntu from the memory and the CD, without installing anything at all.

---

### Post by jakc on 2007-02-17
Yeah, but i assume its a different iso from the one i downloaded? where can i get the new iso? or am i talking rubish

---

### Post by mikewhatever on 2007-02-17
> **jakc said:**
> Yeah, but i assume its a different iso from the one i downloaded? where can i get the new iso? or am i talking rubish

The desktop iso is the Live CD, so you have the right one.

---

### Post by freebird54 on 2007-02-17
Try the one you have - it probably is the live CD - it is also the installer when you want it to be...

freebird54

---

### Post by Dylnuge on 2007-02-17
> **jakc said:**
> Surely this can be reversed as 9 times out of 10 i will be booting windows (i say that now).

However, niggles like this im not 2 bothered about at this stage.  I am really researching the installation procedure itself.  Good to hear you got it going easy enough on a laptop though.

You can change it, sort of.

You can change how long you have. You can also change which os is set to auto load, however, it is a numerical value. (i.e, if windows is fourth on the list, you set the number to 3 (it starts counting at 0)). Since new kernals get added to the list (think updates), the number needs to constantly be raised. On the other hand, you can download an application called Start-up Manager. (Google it). It will keep changing the number for you, so you don't need to worry.

---

### Post by linux_kid on 2007-02-17
Be sure to have at least 7GB for your basic linux partition, and 1Gb for swap.  You may also want to clean up your C:\ drive in windows, its really full.

---

### Post by Velotix on 2007-02-17
You seem to know what you're doing to a degree so I'll drop the patronising crap and get to the point, as I'm sure you'll appreciate it much more that way:

Unlike Windows, where the root of the file system is always a menu showing all the separate hard-drives and media drives, in Linux the root of the file system is *wherever the hell you want it to be*. Equally, you can mount specific hard-drives and partitions as certain directories.

Alternatively, you can create a symlink (like a shortcut, only instead of just pointing to another location, it actually creates an alternative route to that location) to the location of your files.

I bring this up because you seem to use your My Documents folder in Windows a lot (enough to bother backing it up). Generally, a user's documents and settings are stored in a folder, like XP. This folder is always found at "/home/[username]". A lot of people create a separate partition for their user files and mount the partition as "/home" , so they don't have to reinstall everything when they want to upgrade the OS. You may prefer to symlink your My Documents folder from Windows to your /home folder. The choice is yours, but this may be problematic for reasons I'll discuss shortly.

As for the swap partition, it's a fixed-size partition of what is essentially virtual memory. It uses its own unique filesystem, designed for maximum read/write access times. It's usually recommended to have a swap partition be about 1.5 to 2.5 times the amount of RAM in size, so *your* swap partition should be at least 1.5GB big. When I installed Ubuntu, though, it gave me a 6GB swap partition automatically, which is three times my 2GB of RAM, so if this is too much for you, make sure to set the swap partition manually during the install. I've not seen my swap partition get used once, but as you "only" have 1GB of RAM you'll probably need yours, so make sure it's big enough to work smoothly from the outset, because unlike Windows it doesn't change size on demand.

Linux by default can't write to NTFS-formatted filesystems - it can only read them because Microsoft have never released the specifications for the filesystem unlike FAT32, which is supported in Linux. (Naturally then, you can't format a partition as NTFS in Linux either by default.) A third-party open-source program called ntfs-3g will give you write access to NTFS filesystems, but it'll ignore access rights. Similarly, a third-party program for Windows, "Ext2 IFS For Windows", will allow it to read ext2 and ext3 partitions, also without acknowledging access rights - this is due to the different way Windows and UNIX-based systems handle file permissions. Be aware that you'll be opening up a possible security hole by using these programs, but aside from that they're reported to work very reliably, and may be for you. If you intend to use Windows as your primary OS, I recommend Ext2 IFS because it'll open up the security hole in the OS you can afford to drop anyway.

In summary then, I recommend this:

[i]sda1 - FAT32 (Windows Recovery); 5GB
sda2 - NTFS (Windows XP); 220GB, with [ext2/3 compatibility drivers installed](http://www.fs-driver.org/)

sdb1 - ext3 (Ubuntu 6.10); 80GB
sdb2 - FAT32 (Ubuntu/Windows shared access); 667GB
sdb3 - N/A (placeholder primary partition); 1KB
sdb5 - swap (Linux swap partition); 3GB[/i]

(The seemingly useless sdb3 must be included as Linux insists the swap partition is a logical rather than primary partition... *shrug*)

If you choose to install ntfs-3g as well, make *sdb2* an NTFS partition for stability reasons (as I recall FAT32 doesn't honour file permissions anyway, so there's no impact on security), or alternatively make it an ext3 partition if you have the ext2/3 compatibility installed. For that partition, choose whichever you feel most comfortable using. Ubuntu itself works best on ext3, hence my suggestion.

Apologies if I rambled on. :P

---

### Post by jakc on 2007-02-18
Thanks for the detailed reply. Its late so ive maybe not taken it fully in.

So your saying keep My Documents on sdb2 as a FAT32. Theres nothing I need to keep secure on there anyhow so I dont see this being a problem.  However I was under the impression that FAT32 had poorer performance against NTFS: [http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm) (think i saw some benchmark results in a mag once as well) Performance degrades even more so with larger volumes - 750 is large.  Do you agree with this? I also read:
*In Windows XP, the maximum partition size that can be created using FAT32 is 32GB*
True?

I won't actually need to access My Documents from the Linux (although would be nice) but will only need around 80gb of storage to create files with, within Linux.  But then im going to have to create another partition as storage for My Documents alone, but will probably keep this as NTFS.

Where is sdb4?  Still a bit unsure about the sdb3 one as well - logical vs primary partition?

Thanks, I think this was initial advice I needed - the partition structure.

Does anyone disagree/agree with this advice?

---

### Post by confused57 on 2007-02-18
You can have only 4 primary partitions on a hard drive, partition numbering 1-4 are reserved for primary partitions...the proposed sdb3 is an extended primary partition that can contain many logical partitions, e.g. swap sdb5...if you made another primary partition it would be sdb4.   Therefore, you could subdivide your hard drive up into many logical partitions, if you want.   You could set up one extended partition and make the rest logical...maybe not what you would want to do, but you could.
   Many people prefer to use ext3, rather than FAT32, to share data between Windows(with driver) & Linux.  Ext3 doesn't have many of the restrictions of FAT32.
   Velotix  described things nicely that you'll need to know...as I mentioned, it will be a matter of personal preference, especially since you can "subdivide" your hd into logical partitions, if you like...you might want to read over some of threads in the forum concerning partition preferences & suggestions.

---

### Post by jakc on 2007-02-18
My new drive should be with me in tommorows post.  Id like to get it in my machine and plug it into the second (of 2) SATA ports of the motherboard.  This is what I then propose to do - Turn machine on and hopefully BIOS will spot it ok.  Create a NTFS partition in Windows of around 650GB.  Ill then dump my docs there eventually.

Then id like to install Ubuntu on this 2nd SATA drive, but choose to manually sort the partitions within the install.

So hows about this:

sda1 - FAT32 (Windows Recovery); 5GB
sda2 - NTFS (Windows XP); 220GB, with ext2/3 compatibility drivers installed

sdb1 – NTFS Windows access 667GB
sdb2 - ext3 (Ubuntu 6.10); 80GB
sdb3 - N/A (placeholder primary partition); 1KB
sdb5 - swap (Linux swap partition); 3GB

Im pretty sure I've researched enough info (thanks to you lot) - I will use some of the links that Confused gave me. 

However, I would appreciate it if someone could point out any flaws in the above method and there are still some point id like cleared up which I mentioned in my previous post

---

### Post by linux_kid on 2007-02-18
Your partitiong seems fine, but you shouldn't need to put the swap partition (sdb5) on an extended partition, so sdb3 is an unneeded partition.  sdb3 is only needed if linux insists the swap be on an extended partition.  Also, what happened to sdb4 ??

Overall, good job

---

### Post by jakc on 2007-02-19
> sdb3 is only needed if linux insists the swap be on an extended partition. Also, what happened to sdb4

not sure if im getting contradicting advice - linux kid if you read previous 2 posts they go against ur advice.  Whos right here? Will be installing tommorow night i rekon.

---

### Post by Velotix on 2007-02-19
Hoboy. Now we're getting into awkward territory - filesystem discussion. Ack. I'll try and keep this legible. :P

Microsoft systems generally only support Microsoft file systems, unless you add extra software to improve file system support (which is risky as all existing solutions modify the Windows kernel directly). That means that Windows XP can natively read and write only to NTFS and FAT32.

FAT32 partitions cannot indeed be formatted larger than 32GB under Windows, but this is an arbitrary restriction - Microsoft are keen to get people to switch to NTFS, and for once they're right to do so - an old Win98SE I once used had FAT32-formatted drives and it managed to corrupt my Windows installation of its own accord one day. Needless to say, using FAT32 at all is risky, but it can be done, and is the only filesystem that Linux and Windows both fully support without messing with either of them.

Linux, being open-source, can read any filesystem under the sun - the list of supported filesystems under Linux is *enormous*, and I can't possibly remember them all. NTFS is the only filesystem that's problematic in Linux simply because no-one but Microsoft knows how to program a stable driver for it - the *ntfs-3g* driver was built from pure trial-and-error, and has only recently progressed to Release Candidate status. Ironically, you could really use NTFS support. However, it's not your only option at all:

By default, Ubuntu uses the open-source *ext3* filesystem, which is itself merely an upgraded version of a much older filesystem called *ext2*. The key differences between the two are the fact that ext3 partitions can be much larger and ext3 has a very, very useful function called journalling.

*looks this one up first :P*

Journalled filesystems (NTFS and ext3, but **NOT** FAT32 and ext2) keep a record of changes being made to a file before actually making the changes. Another consequence of this is that on NTFS, you can actually see how many times a file has been modified, and exactly what those changes were. I myself am still learning, so I'm not quite sure why, but both NTFS and ext3 are very, VERY stable filesystems.

(Minor note: USB flash drives use FAT32. FAT32 is OK on those drives because they're not that big, but it's still risky.)

Now, why am I bringing this all up? Choosing which filesystem a partition uses is a reasonably involved decision because it will directly influence how reliable, and how fast, you can read and write to your files. There's another issue, too: *LINUX HARD DRIVES DON'T EVER FRAGMENT UNTIL THEY'RE NEARLY FULL*. That's because of the way ext3 and other non-Microsoft filesystems modify their files - they place the new file wherever free space is available and then delete the old one, rather than adding the new parts on a separate part of the drive and leaving your files all over the place on the drive. Think of it as ext3 running a very quick mini-defrag every time you save a file. Much less annoying.

So, to the point: don't use FAT32 unless you have to. Ever. NTFS is better, but prone to fragmenting. Windows programs since XP have been built assuming they were running on NTFS, so they tend to run better in it, but avoid storing your precious files in it, unless you have to. NTFS isn't prone to corruption - I've found it very stable when I've used it - but you are doing video editting, so you'll have a lot of large, valuable files that are bound to get ridiculously fragmented after only a few days.

Your big fat 600GB partition may then be better off as an ext3 partition, which I didn't want to suggest before because your Windows partition would have to rely on third-party software to read the My Documents folder. :/

Dual-booting is usually less messy if you make it so that the OS can't access each other's drives, as it's a security nightmare waiting to happen (i.e. in Windows, your ext3 drives wouldn't fragment but they're also completely insecure - no file access rights are honoured by the Windows driver - and can be messed with by anyone as much as they want. If you're the only person who uses your computer, this isn't an issue).

If you want more detailed information of filesystems, check Wikipedia - certain filesystems are more effective at running OSes and some are better for storing media. Of course, on Windows you have little choice - (forgive my bluntness) crappy, or crapp*ier* - but when life hands you lemons, make lemonade, as the saying goes. :)

Finally:

> Your partitiong seems fine, but you shouldn't need to put the swap partition (sdb5) on an extended partition, so sdb3 is an unneeded partition. sdb3 is only needed if linux insists the swap be on an extended partition. Also, what happened to sdb4 ??

Check the included attachment. Notice the 1KB sda2 partition - all it's there for is as an index to tell the system where to find the sda5 partition on the drive. That was done automatically by Ubuntu when it installed itself, so yes, it does insist the swap partition is on a logical drive partition. Why, I don't yet know.

Partition numbers in Linux work as follows:
*#1, #2, #3, #4* - reserved for primary partitions - these partitions are PHYSICAL separations on the hard-drive defined by the master boot record (MBR) of the hard-drive; a limitation of existing hard-drives is that they can only have four primary partitions
*#5 and onwards* - logical partitions; a parimary partition can be set up so that it doesn't actually contain any data at all and is instead an index, telling the OS where to look for the arbitrary partitions held within it; these partitions are called logical because they're defined by data in the hard drive, not the MBR. You can have as many logical partitions as you please - hence as you may have guessed logical partitions were invented to dodge the limitation of primary partitions. :)

The numbering is the way it is so that there's no danger of two partitions trying to mount to the same place, which would cause a very major system crash.

In summary, then; I'm going to include this time WHERE to mount the partitions in Linux for maximum convenience (after installing :P) as well, and I'll put them in bold - as you're aware in Windows they just show up in My Computer as separate drives. You will notice I've made some changes as well following questions and points raised in previous posts:

[i]sda1 - **/media/win-recovery** - FAT32 (Windows Recovery); 5GB
sda2 - **/media/drive-c** - NTFS (Windows XP); 220GB, with [ext2/3 compatibility drivers installed](http://www.fs-driver.org/)

sdb1 - **/** - ext3 (Ubuntu 6.10); 80GB
sdb2 - **/home** - FAT32/ext3/NTFS (Ubuntu/Windows shared access); **As large as you feel happy with**
sdb3 - **/home/[username]/windows-storage** - NTFS (Windows-only Storage); (667 - sdb2)GB *(i.e. the rest of the drive)*
sdb4 - **[N/A]** (you'll never need to see this drive anyway) - N/A (placeholder primary partition); 1KB
sdb5 - **[N/A]** (Ubuntu will look for this in a specific place, so don't mess with the default) - swap (Linux swap partition); 3GB[/i]

In case you're worried, you can set the mount points after the rest of the install is completed - you have to edit a setup file to do this, but it's not that complicated. It should be noted that you can always make sdb2 and sdb3 one partition instead of two (in which case everything goes back to the old suggestion and you still mount sdb2 as /home).

There is one exception to that, though - /home is where Ubuntu stores all your user settings as well as your files, so if you want to mount a special partition as /home, you have to say so during the install. It can't wait. Bad things will happen if you do, like not being able to login, etc.

I told you this was going to get awkward. :P

---

### Post by jakc on 2007-02-19
ive learnt a lot from this one thread alone, and believe me ive been googlin around for ideas everywhere.

Ok. I have read your reply and taken most of it in but want to catch u whilst ur still online.

I agree with your structure from the comments you have made. I just wish it was going to a lot simpler partition structure than this.  

I still need to get my head around what you have just written, especially:

> I'm going to include this time WHERE to mount the partitions in Linux for maximum convenience


I understand mounting is the equivalent of drives in windows i think.  This isnt part of the installation process?  I am not sure if I will need sdb2 though - need to think about that.

I need to research a bit more abotu what you have just written.  Getting myself confused and scared.

Thanks loads though, youve been a great help and please check back over next couple of days if u have time.

---

### Post by jakc on 2007-02-19
quickie - is it still recommended to swap the drives around
i.e. After installation plug the new 750 into sata1 port and wak Ubuntu cd in to create partitions.  I cant see there being any problem if i left it as is, with it plugged into sata 2 port and im sure Ubuntu will pick up on both drives and allow me to choose which drive to partition?

---

### Post by Velotix on 2007-02-19
This is somewhat embarassing to admit but I'm not very familiar with the Ubuntu installer. XD
I let it set my system up automatically because this computer was brand-new at the time.

Now however I've had to amass a large amount of partitioning and drive information very quickly because I'm planning to make this machine dual-boot as well, only I'll be needing another hard-drive to do it. You have the opposite problem to me, so be glad that you're actually doing it the easier way. XP

As to swapping the drives around during install, that's only if you don't want GRUB installed on your Windows drive. GRUB is a bootloader (GRUB = Grand Universal Bootloader). Windows, like all OSes, uses a bootloader to tell the computer where to load the system files from. Yes, you guessed it, Microsoft's bootloader only loads Microsoft OSes! :D

GRUB, however, will load pretty much anything under the sun, hence it was chosen as Ubuntu's bootloader. I imagine you were told to avoid installing GRUB to your Windows drive because you're new to Linux and would have to learn (and risk) how to edit GRUB to get it working properly.

However you do it, **the drive that you install GRUB to should always be the master drive, otherwise your system will use the bootloader on the master drive**.

The Ubuntu installer is very good at detecting Windows OSes and adding an entry in GRUB for them, so don't disconnect your Windows drive completely - just make it your slave drive during the install process. You can of course leave it that way if you want, or you can switch it back.

Tell us which drive you'd prefer as the Master and we'll go from there, but I'm guessing it's the Windows drive.

**EDIT:** Forgot your other question.

> I understand mounting is the equivalent of drives in windows i think.

No. Windows also mounts drives. Mounting a drive is the process in which a drive is recognised and configured so that you can read and write files from it. All removeable drives also have to mount, too; every time you've inserted a CD into a drive, it has been mounted and set as read-only. Similarly, every time you remove a CD, it has to be unmounted first, otherwise Windows or any other OS would still think it could access the files on the CD, which is problematic to say the least. Same goes for USB memory sticks, and why you have to "Safely Remove" the drives - you have to unmount them first before taking them out.

Think of it this way: in Windows, My Computer is the root folder of your entire filesystem. Windows mounts all your drives directly to this folder, and it also sometimes leaves a few other programs lying around in the root of the filesystem too. (I recall being able to access printing options in My Computer.)

In Linux, the convention is to not force someone to mount their drives straight to the root folder because it causes inflexibility issues (a la Windows) that are solved simply by letting you mount the drives where you want. In Linux, the root of your filesystem is usually the root folder of your primary hard-drive. In your case, it'll be the root folder of whatever drive you chose to put Ubuntu on.
Of course, you certainly can mount all your drives in a folder where you can see them all clearly if you want to: in Ubuntu this folder is called /media; in other Linux distributions it's called /mnt (for "mount"). As you can see, it really doesn't matter where they go so long as you can know where they are and can find them.

Drives don't have to be mounted, either, if say for example you didn't want to use a drive at all - the recovery partition on your Windows drive is one such example of a permanently unmounted partition - doing so also means it's never assigned a drive letter, which would be a bit pointless. In case you hadn't worked it out yet, the drive letters in Windows are simply generic mount points.

> This isnt part of the installation process?

Mounting drives has nothing to do with installation. You can do it during installation if you want, or anytime afterwards.

Also, you're asking for a custom installation, because making /home a mount point for a hard-drive is not a standard install option, even though it is quite popular for the purposes of safely upgrading your Linux OS. Chances are if you don't tell Ubuntu to mount the drives in specific places, it'll mount them in the /media folder (so your Windows drive will show up in */media/sda2*).
You can do this if you think it's less hassle.

(Note I have no firsthand experience of this - I have one hard-drive with two partitions - a swap and the main partition, and that partition is mounted as "/", so my files are all in one place anyway. It does take some getting used to though, I admit, but you'll probably find it's a more effective system when you rid yourself of the Microsoft brainwashing. :P)

---

### Post by jakc on 2007-02-19
Yes GRUB I have done little research on and only know what you just told me.

I also get a bit confused as I refer to slave and master when talking about IDE drives, where as I was under the impression that SATA drives were equal in a way.

I assume I dont want GRUB installed on sda and like I said in the first post - I want to make this install as simple as possible.  Therefore I would like to minimise manual editing of important system-like files such as this GRUB boot loader.  

As Windows will be my OS I will be using the majority of the time, it would make sense to make sda the master drive (250gb one), so this suggests that GRUB should be installed here?  

As I said, not too sure about the slave vs master with SATA thing.  

This is what I propose to do tomorrow:  
[LIST]
[*]Install the new SATA and plug it into SATA2 port. Boot windows, hope the BIOS detects drive, and check it under drive mgmt in XP.
[*]Shutdown. 
[*]Swap the ports so 250gb is in SATA2 and 750 is in SATA1. Boot from Ubuntu CD.
[*]Begin Installation process.
[*]Create partitions as per your advice earlier.
[*]Hopefully work the GRUB bit out and install on the 250GB drive?
[*]Reboot and hopefully have option to choose which OS to boot into
[/LIST]

Im sure it wont quite like that, but heres hoping. Please point out any mistakes in the above list.

---

### Post by Velotix on 2007-02-19
Please note the edit to my previous post, I forgot something very important. :)

---

### Post by confused57 on 2007-02-19
Velotix has explained everything, rather eloquently & thorough, I may add.
You might want to glance over the grub section in this link:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I don't claim to be an expert, but whichever drive you have set as the first boot device in bios "should" be the drive where grub is installed to the mbr, i.e. if you have bios set to boot first to your SATA#1 controller(sda), then that's where grub "should" install to the mbr.

A good way of setting up a dualboot with 2 hard drives(Windows & Ubuntu on separate drives) is in a link I gave you earlier:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

You could connect your 750 Gb drive to SATA #1 controller(sda) when you install Ubuntu, you shouldn't need to disconnect your Windows 250 Gb drive, unless you want to be absolutely sure...at the grub install step, you could always designate to install to **/dev/sda**, by typing it in .
Ubuntu may automatically add an entry to boot Windows, but it's easy to manually add one(see the link)...the benefit of setting your system up this way is that grub isn't installed to the Windows drive mbr...grub can boot either Windows or Ubuntu...if Ubuntu fails to boot, then switch your boot order to boot into Windows.

In grub, your first hard drive will be designated as hd0, and your second drive will be hd1.

---

